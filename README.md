```
sudo pacman -Syu zram-generator

sudo tee /etc/systemd/zram-generator.conf >/dev/null <<'EOF'
[zram0]
zram-size = ram * 2.5
compression-algorithm = zstd
EOF

sudo tee /etc/sysctl.d/99-swappiness.conf >/dev/null <<'EOF'
[zram0]
vm.swappiness = 180
vm.watermark_boost_factor = 0
vm.watermark_scale_factor = 125
vm.page-cluster = 0
EOF
```
