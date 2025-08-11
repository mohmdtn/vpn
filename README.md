{
  "log": {
    "level": "warn",
    "output": "box.log",
    "timestamp": true
  },
  "dns": {
    "servers": [
      {
        "tag": "dns-remote",
        "address": "udp://1.1.1.1",
        "address_resolver": "dns-direct"
      },
      {
        "tag": "dns-trick-direct",
        "address": "https://sky.rethinkdns.com/",
        "detour": "direct-fragment"
      },
      {
        "tag": "dns-direct",
        "address": "1.1.1.1",
        "address_resolver": "dns-local",
        "detour": "direct"
      },
      {
        "tag": "dns-local",
        "address": "local",
        "detour": "direct"
      },
      {
        "tag": "dns-block",
        "address": "rcode://success"
      }
    ],
    "rules": [
      {
        "domain": [
          "pl2.playergg.ir",
          "nl.lostarc.ir",
          "fr.playergg.ir",
          "v.p.n.l",
          "pl.playergg.ir"
        ],
        "server": "dns-direct"
      },
      {
        "domain": "connectivitycheck.gstatic.com",
        "server": "dns-remote",
        "rewrite_ttl": 3000
      },
      {
        "rule_set": [
          "geoip-ir",
          "geosite-ir"
        ],
        "server": "dns-direct"
      },
      {
        "domain_suffix": ".ir",
        "server": "dns-direct"
      }
    ],
    "final": "dns-remote",
    "static_ips": {
      "sky.rethinkdns.com": [
        "104.17.148.22",
        "104.17.147.22",
        "104.18.1.48",
        "104.18.0.48"
      ]
    },
    "independent_cache": true
  },
  "inbounds": [
    {
      "type": "tun",
      "tag": "tun-in",
      "mtu": 9000,
      "inet4_address": "172.19.0.1/28",
      "auto_route": true,
      "strict_route": true,
      "endpoint_independent_nat": true,
      "stack": "mixed",
      "sniff": true,
      "sniff_override_destination": true
    },
    {
      "type": "mixed",
      "tag": "mixed-in",
      "listen": "127.0.0.1",
      "listen_port": 12334,
      "sniff": true,
      "sniff_override_destination": true
    },
    {
      "type": "direct",
      "tag": "dns-in",
      "listen": "127.0.0.1",
      "listen_port": 16450
    }
  ],
  "outbounds": [
    {
      "type": "selector",
      "tag": "select",
      "outbounds": [
        "auto",
        "✅  | mti_kzi | هرروز آپدیت کنید  § 0",
        "📊 0 B | حجم مصرف شده   § 1",
        "🗓 تاریخ | 1404-06-02   § 2",
        "🚀🇵🇱 Shadow  § 3",
        "🚀🇵🇱 Shadow 2  § 4",
        "🚀🇳🇱 Shadow 3  § 5",
        "🚀🇫🇷 Shadow 4  § 6",
        "🇵🇱 VPNLAND  § 7"
      ],
      "default": "auto"
    },
    {
      "type": "urltest",
      "tag": "auto",
      "outbounds": [
        "✅  | mti_kzi | هرروز آپدیت کنید  § 0",
        "📊 0 B | حجم مصرف شده   § 1",
        "🗓 تاریخ | 1404-06-02   § 2",
        "🚀🇵🇱 Shadow  § 3",
        "🚀🇵🇱 Shadow 2  § 4",
        "🚀🇳🇱 Shadow 3  § 5",
        "🚀🇫🇷 Shadow 4  § 6",
        "🇵🇱 VPNLAND  § 7"
      ],
      "url": "http://connectivitycheck.gstatic.com/generate_204",
      "interval": "10m0s",
      "tolerance": 1,
      "idle_timeout": "30m0s"
    },
    {
      "type": "vless",
      "tag": "✅  | mti_kzi | هرروز آپدیت کنید  § 0",
      "server": "v.p.n.l",
      "server_port": 2044,
      "uuid": "65c43acc-858f-41a8-912a-ec891bf7067f",
      "packet_encoding": "xudp"
    },
    {
      "type": "vless",
      "tag": "📊 0 B | حجم مصرف شده   § 1",
      "server": "v.p.n.l",
      "server_port": 2044,
      "uuid": "65c43acc-858f-41a8-912a-ec891bf7067f",
      "packet_encoding": "xudp"
    },
    {
      "type": "vless",
      "tag": "🗓 تاریخ | 1404-06-02   § 2",
      "server": "v.p.n.l",
      "server_port": 2044,
      "uuid": "65c43acc-858f-41a8-912a-ec891bf7067f",
      "packet_encoding": "xudp"
    },
    {
      "type": "shadowsocks",
      "tag": "🚀🇵🇱 Shadow  § 3",
      "server": "PL.playergg.ir",
      "server_port": 1080,
      "method": "chacha20-ietf-poly1305",
      "password": "n2uCiY5YRquaipjIO1SX_A"
    },
    {
      "type": "shadowsocks",
      "tag": "🚀🇵🇱 Shadow 2  § 4",
      "server": "PL2.playergg.ir",
      "server_port": 1080,
      "method": "chacha20-ietf-poly1305",
      "password": "n2uCiY5YRquaipjIO1SX_A"
    },
    {
      "type": "shadowsocks",
      "tag": "🚀🇳🇱 Shadow 3  § 5",
      "server": "nl.lostarc.ir",
      "server_port": 1080,
      "method": "chacha20-ietf-poly1305",
      "password": "n2uCiY5YRquaipjIO1SX_A"
    },
    {
      "type": "shadowsocks",
      "tag": "🚀🇫🇷 Shadow 4  § 6",
      "server": "fr.playergg.ir",
      "server_port": 1080,
      "method": "chacha20-ietf-poly1305",
      "password": "n2uCiY5YRquaipjIO1SX_A"
    },
    {
      "type": "vless",
      "tag": "🇵🇱 VPNLAND  § 7",
      "server": "PL.playergg.ir",
      "server_port": 33033,
      "uuid": "65c43acc-858f-41a8-912a-ec891bf7067f",
      "transport": {
        "type": "http",
        "host": "iran.ir",
        "path": "/",
        "method": "GET"
      },
      "packet_encoding": "xudp"
    },
    {
      "type": "dns",
      "tag": "dns-out"
    },
    {
      "type": "direct",
      "tag": "direct"
    },
    {
      "type": "direct",
      "tag": "direct-fragment",
      "tls_fragment": {
        "enabled": true,
        "size": "10-30",
        "sleep": "2-8"
      }
    },
    {
      "type": "direct",
      "tag": "bypass"
    },
    {
      "type": "block",
      "tag": "block"
    }
  ],
  "route": {
    "rules": [
      {
        "domain": ".ir",
        "outbound": "direct"
      },
      {
        "rule_set": [
          "geoip-ir",
          "geosite-ir"
        ],
        "outbound": "direct"
      },
      {
        "inbound": "dns-in",
        "outbound": "dns-out"
      },
      {
        "port": 53,
        "outbound": "dns-out"
      },
      {
        "clash_mode": "Direct",
        "outbound": "direct"
      },
      {
        "clash_mode": "Global",
        "outbound": "select"
      },
      {
        "process_name": [
          "Hiddify",
          "Hiddify.exe",
          "HiddifyCli",
          "HiddifyCli.exe"
        ],
        "outbound": "bypass"
      }
    ],
    "rule_set": [
      {
        "type": "remote",
        "tag": "geoip-ir",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/hiddify/hiddify-geo/rule-set/country/geoip-ir.srs",
        "update_interval": "120h0m0s"
      },
      {
        "type": "remote",
        "tag": "geosite-ir",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/hiddify/hiddify-geo/rule-set/country/geosite-ir.srs",
        "update_interval": "120h0m0s"
      }
    ],
    "final": "select",
    "auto_detect_interface": true,
    "override_android_vpn": true
  },
  "experimental": {
    "cache_file": {
      "enabled": true,
      "path": "clash.db"
    },
    "clash_api": {
      "external_controller": "127.0.0.1:16756",
      "secret": "jaD-34sUO50TewzV"
    }
  }
}
