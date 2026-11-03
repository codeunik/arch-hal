sudo pacman -Syu zram-generator

sudo tee /etc/systemd/zram-generator.conf >/dev/null <<'EOF'
[zram0]
zram-size = ram * 2
compression-algorithm = zstd
EOF
