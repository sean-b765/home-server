| Service      | Description                                     | Port(s)                                 |
| ------------ | ----------------------------------------------- | --------------------------------------- |
| caddy        | Web server, use for reverse-proxy               | 80, 443                                 |
| adguard      | DNS server, blocks ads, can rewrite DNS entries | 8080 (admin dashboard), 3001 (setup ui) |
| homepage     | Nice dashboard                                  | 3000                                    |
| transmission | Torrent client                                  | 9091                                    |
| prowlarr     | Torrent indexer                                 | 9696                                    |
| radarr       | Movies                                          | 7878                                    |
| sonarr       | TV                                              | 8989                                    |
| lidarr       | Music                                           | 8686                                    |
| plex         | Media streaming                                 | 32400                                   |
| autoscan     |                                                 |                                         |
| tautulli     |                                                 | 18081                                   |
| overseerr    |                                                 | 5051                                    |
| glances      |                                                 | 61208                                   |
| n8n          |                                                 |                                         |

# AdGuard Home setup

Note: you will have to free port 53 on your server before hosting AdGuard...
Ubuntu uses `systemd-resolved` by default:

```
sudo systemctl stop systemd-resolved
sudo systemctl disable systemd-resolved
```

1. Visit http://hostname:3001 to setup
2. Bind to _All Interfaces_
3. Navigate to http://hostname:8080 to view the dashboard UI
4. Set your DNS server as the local IP of your home server
5. You can add custom DNS rewrites to choose a custom domain for your home server:

- `*.myhostname.local` -> `SERVER IP`
- `myhostname.local` -> `SERVER IP`

# Prowlarr setup

1. Prowlarr ➡️ Settings ➡️ Apps ➡️ Applications (+ Add)
2. Add **Sonarr/Radarr**:

- You want to change the **Prowlarr Server**, **Sonarr/Radarr Server**, **API Key** fields
- Prowlarr Server: `http://prowlarr:9696`
- Radarr Server: `http://radarr:7878`
- API Key: **Sonarr/Radarr** ➡️ Settings ➡️ General ➡️ Security ➡️ API key
