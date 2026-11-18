```
sudo pacman -Syu zram-generator

sudo tee /etc/systemd/zram-generator.conf >/dev/null <<'EOF'
[zram0]
zram-size = 2 * ram
compression-algorithm = zstd
swap-priority=100
EOF

sudo tee /etc/sysctl.d/99-swappiness.conf >/dev/null <<'EOF'
vm.swappiness = 180
vm.watermark_boost_factor = 0
vm.page-cluster = 0
vm.watermark_scale_factor = 200
vm.min_free_kbytes = 262144
vm.vfs_cache_pressure = 400
EOF
```
