        const map = L.map('map', { preferCanvas: true }).setView([-1.4478, -48.4881], 17);
        
        L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
            maxZoom: 20
        }).addTo(map);
        
        const load = document.getElementById('load');
        const txt = document.getElementById('txt');
        const locBtn = document.getElementById('locBtn');
        
        let loaded = 0;
        let userMarker, userCircle, watchId;
        
        function done() {
            if (++loaded === 2) {
                setTimeout(() => load.classList.add('hide'), 300);
            }
        }
        
        // Perímetros
        txt.textContent = 'Carregando perímetros...';
        const p = omnivore.kml('KML-REDUTO-LOTES.kml')
            .on('ready', function() {
                p.setStyle({ color: '#FFD700', weight: 1.5, opacity: 0.7, fillOpacity: 0.05 });
                map.fitBounds(p.getBounds());
                txt.textContent = 'Carregando pontos...';
                done();
            })
            .addTo(map);
        
        // Pontos
        const r = omnivore.kml('KML-REDUTO-ROTULOS.kml')
            .on('ready', function() {
                const icon = L.icon({
                    iconUrl: 'data:image/svg+xml,%3Csvg width="6" height="6" xmlns="http://www.w3.org/2000/svg"%3E%3Ccircle cx="3" cy="3" r="2.5" fill="%238A2BE2" stroke="white" stroke-width="0.5"/%3E%3C/svg%3E',
                    iconSize: [6, 6],
                    iconAnchor: [3, 3]
                });
                
                r.eachLayer(l => {
                    if (l.setIcon) l.setIcon(icon);
                    
                    const props = l.feature?.properties;
                    if (props?.name) {
                        const tt = L.tooltip({
                            permanent: true,
                            direction: 'right',
                            className: 'lote-label',
                            offset: [4, 0]
                        }).setContent(props.name);
                        
                        l.bindTooltip(tt);
                        if (map.getZoom() < 18) l.closeTooltip();
                        
                        l.bindPopup(`<b>Nº ${props.name}</b>`);
                    }
                });
                
                done();
            })
            .addTo(map);
        
        // Zoom control
        map.on('zoomend', () => {
            const z = map.getZoom();
            r.eachLayer(l => {
                if (l.getTooltip()) {
                    z >= 18 ? l.openTooltip() : l.closeTooltip();
                }
            });
        });
        
        // Location
        locBtn.onclick = () => {
            if (!navigator.geolocation) return;
            
            if (locBtn.classList.contains('active')) {
                if (watchId) navigator.geolocation.clearWatch(watchId);
                if (userMarker) {
                    map.removeLayer(userMarker);
                    map.removeLayer(userCircle);
                }
                locBtn.classList.remove('active');
                return;
            }
            
            watchId = navigator.geolocation.watchPosition(
                pos => {
                    const { latitude: lat, longitude: lng, accuracy } = pos.coords;
                    const icon = L.divIcon({ className: 'user-marker', iconSize: [16, 16] });
                    
                    if (userMarker) {
                        userMarker.setLatLng([lat, lng]);
                        userCircle.setLatLng([lat, lng]).setRadius(accuracy);
                    } else {
                        userMarker = L.marker([lat, lng], { icon, zIndexOffset: 1000 }).addTo(map);
                        userCircle = L.circle([lat, lng], { radius: accuracy, color: '#4285f4', fillOpacity: 0.1, weight: 1 }).addTo(map);
                        map.setView([lat, lng], 18);
                    }
                    
                    locBtn.classList.add('active');
                },
                () => {},
                { enableHighAccuracy: true, maximumAge: 0 }
            );
        };
    
