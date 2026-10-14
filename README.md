# Pi-hole Control Card

A responsive Home Assistant Lovelace card for Pi-hole v6, styled to match the Aurora/Ocean/Sunset/Lavender card collection.

## Features

- Four configurable headline metrics and optional DNS/client statistics
- Pi-hole service status and ad-blocking switch
- Temporary ad-blocking pause actions (1, 5, and 15 minutes)
- Optional group switches
- Optional maintenance buttons with an in-card confirmation step
- Optional installed-version and update-available badges
- Responsive, theme-aware design
- All entity IDs are selected in the card editor; no personal entity IDs are built in

## Install with HACS

1. In HACS, open the three-dot menu and choose **Custom repositories**.
2. Add `Liionboy/lovelace-pihole-control-card` with type **Dashboard**.
3. Install **Pi-hole Control Card**.
4. Add the card and choose the Pi-hole switch, status sensor, and statistic sensors.

```yaml
type: custom:pihole-control-card
entity: switch.example_pihole
status_entity: binary_sensor.example_pihole_status
queries_entity: sensor.example_pihole_queries
blocked_entity: sensor.example_pihole_blocked
blocked_percentage_entity: sensor.example_pihole_blocked_percentage
domains_entity: sensor.example_pihole_domains
palette: aurora
pause_service_domain: auto
```

Optional sensors: `unique_clients_entity`, `seen_clients_entity`, `cached_entity`, `forwarded_entity`, `query_rate_entity`, and `remaining_entity` (seconds until blocking resumes). `group_switches`, `maintenance_buttons`, and `update_entities` each accept a list of matching entity IDs. Maintenance actions ask for an in-card confirmation before calling `button.press`.

`pause_service_domain: auto` detects `pi_hole_v6.disable` or `pi_hole.disable` in Home Assistant's available services. The pause controls use the selected Pi-hole switch and Home Assistant's native temporary-disable action.

## Configuration

| Option | Required | Description |
| --- | --- | --- |
| `entity` | Yes | Pi-hole ad-blocking switch |
| `status_entity` | No | Binary sensor indicating whether Pi-hole is running |
| `queries_entity` | No | Total DNS queries |
| `blocked_entity` | No | Blocked DNS queries |
| `blocked_percentage_entity` | No | Blocked query percentage |
| `domains_entity` | No | Number of domains on the blocklist |
| `group_switches` | No | List of Pi-hole group switches |
| `maintenance_buttons` | No | List of Pi-hole action buttons; each action requires confirmation |
| `update_entities` | No | List of update entities for installed versions and update status |
| `remaining_entity` | No | Remaining pause duration in seconds |
| `palette` | No | `aurora`, `ocean`, `sunset`, or `lavender` |
