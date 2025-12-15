# Maintainer: Ctrler <your-email@example.com>
# Local PKGBUILD - builds from local pre-compiled binary

pkgname=antigravity-tools
pkgver=2.1.1
pkgrel=1
pkgdesc="Professional Account Management for AI Services (Gemini / Claude)"
arch=('x86_64')
url="https://github.com/lbjlaq/Antigravity-Manager"
license=('custom:CC-BY-NC-SA-4.0')
depends=(
    'cairo'
    'desktop-file-utils'
    'gdk-pixbuf2'
    'glib2'
    'gtk3'
    'hicolor-icon-theme'
    'pango'
    'webkit2gtk-4.1'
    'libappindicator-gtk3'
)

# No source - we use local files
source=()
sha256sums=()

package() {
    cd "$startdir"
    
    # Install binary
    install -Dm755 "src-tauri/target/release/antigravity_tools" \
        "$pkgdir/usr/bin/antigravity-tools"
    
    # Install desktop file
    install -Dm644 /dev/stdin "$pkgdir/usr/share/applications/antigravity-tools.desktop" <<EOF
[Desktop Entry]
Name=Antigravity Tools
Comment=Professional Account Management for AI Services
Exec=antigravity-tools
Icon=antigravity-tools
Terminal=false
Type=Application
Categories=Utility;Development;
StartupWMClass=antigravity-tools
EOF

    # Install icons
    install -Dm644 "public/icon.png" \
        "$pkgdir/usr/share/icons/hicolor/512x512/apps/antigravity-tools.png"
    
    for size in 32 128; do
        if [[ -f "src-tauri/icons/${size}x${size}.png" ]]; then
            install -Dm644 "src-tauri/icons/${size}x${size}.png" \
                "$pkgdir/usr/share/icons/hicolor/${size}x${size}/apps/antigravity-tools.png"
        fi
    done
    
    # Install license
    install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
