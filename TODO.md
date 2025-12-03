# rdzwx-go TODO List

## High Priority

- [ ] **Stale Sonde Handling**: When a sonde is stale (no data after X time) it should drop off the map
  - Define staleness timeout threshold (e.g., 5 minutes, 10 minutes)
  - Implement timer/timeout logic to track last update per sonde
  - Show a timer displaying how old the data point on screen is (e.g., "2m ago", "15s ago")
  - Remove stale sondes from map display
  - Consider visual indicator for "aging" sondes before removal

## iOS Port - Remaining Work

### Phase 4: Offline Mapping (Most Complex)
- [ ] Choose offline mapping strategy:
  - [ ] Option 1: Port Mapsforge rendering to Objective-C/Swift
  - [ ] Option 2: Pre-generate tile cache from .map files (recommended)
  - [ ] Option 3: Alternative map format with conversion tools
- [ ] Implement chosen mapping solution
- [ ] Replace placeholder OfflineTileCache implementation
- [ ] Test map rendering with actual .map files

### Phase 5: Document Handling
- [ ] Implement UIDocumentPickerViewController for .map file selection
- [ ] Handle iOS sandboxing and file access permissions
- [ ] Integrate file picker with offline tile cache system

### Phase 6: Performance & Polish
- [ ] Handle iOS background operation restrictions
- [ ] Optimize memory management for iOS constraints
- [ ] Review and ensure iOS App Store compliance
- [ ] Test battery impact and optimize

## Testing & Validation

- [ ] Complete iOS device testing checklist:
  - [ ] App launches without crashing
  - [ ] Location permission prompt appears and works
  - [ ] Network permission prompt appears and works
  - [ ] Manual IP connection to TTGO succeeds
  - [ ] Auto mDNS discovery finds TTGO device
  - [ ] JSON data from TTGO displays in app
  - [ ] GPS coordinates update and display

## Cross-Platform Maintenance

- [ ] Maintain dual-platform compatibility (Android + iOS)
- [ ] Keep plugin changes synchronized across platforms
- [ ] Document platform-specific quirks and workarounds

## Future Enhancements

- [ ] App Store submission pipeline for iOS
- [ ] Google Play Store updates for Android
- [ ] Feature parity validation between platforms
- [ ] Performance profiling and optimization
- [ ] User documentation and help system

---

**Last Updated**: 2025-12-03
