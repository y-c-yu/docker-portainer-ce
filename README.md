# Portainer CE

在 Portainer Server 主機上啟動服務：

```sh
docker compose up -d
```

## Portainer Agent

在要管理的 Linux Docker 主機上啟動 Agent：

```sh
docker compose -f compose.agent.yml up -d
```

在 Portainer 的 Environments 中新增 Docker Standalone 環境，選擇 Agent，並輸入 Agent 主機的 IP 或 DNS 名稱及連接埠，例如 `192.168.1.10:9001`。Agent 主機的 TCP 9001 必須能從 Portainer Server 存取；建議使用防火牆限制來源。

如果 Docker 的 volume 目錄不是 `/var/lib/docker/volumes`，請修改 `compose.agent.yml` 中掛載路徑的左側，右側保持不變。如果 Server 設定了 `AGENT_SECRET`，也必須在 Agent 設定相同的環境變數。Server 和 Agent 應使用相同版本。

詳細設定請參閱 [Portainer Agent 官方文件](https://docs.portainer.io/admin/environments/add/docker/agent)。
