# rdzwx-go TODO List

## High Priority

- [ ] **Stale Sonde Handling**: When a sonde is stale (no data after X time) it should drop off the map
  - Define staleness timeout threshold (e.g., 5 minutes, 10 minutes)
  - Implement timer/timeout logic to track last update per sonde
  - Show a timer displaying how old the data point on screen is (e.g., "2m ago", "15s ago")
  - Remove stale sondes from map display
  - Consider visual indicator for "aging" sondes before removal

- [ ] **UI/UX Improvements**: Add tooltips or help text for icons/buttons
  - Implement tooltip system for mobile (long-press or info icons)
  - Add descriptive labels or hints for UI controls
  - Ensure users understand what each icon/button does
  - Consider onboarding flow or help overlay for first-time users

## iOS Port - Bug Fixes

- [ ] **Fix prediction not working on iOS**
  - Investigate why prediction feature fails on iOS
  - Test prediction algorithms and data flow
  - Ensure iOS-specific coordinate calculations are correct

- [ ] **Fix mDNS not working on iOS**
  - Debug NSNetServiceBrowser implementation in MDNSHandler
  - Verify Bonjour service discovery for `_jsonrdz._tcp`
  - Test on actual iOS device (may work differently than simulator)
  - Check iOS network permissions and Info.plist configuration

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

## Development Tools

- [ ] **Mock TTGO Server**: Create mock server for ad-hoc development and testing
  - Implement JSON-RDZ protocol TCP server
  - Support mDNS/Bonjour service broadcasting (`_jsonrdz._tcp`)
  - Generate realistic sonde data (coordinates, altitude, speed, etc.)
  - Allow running on laptop without physical TTGO ESP32 hardware
  - Support configurable update intervals and multiple simulated sondes
  - Enable testing of stale sonde handling, prediction, and other features

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

## Project Architecture (Long-term Considerations)

- [ ] **Monorepo Consolidation**: Merge separate git repos into single repository
  - Currently: `rdzwx-go/` (main app) and `rdzwx-plugin/` (custom plugin) are separate
  - Investigate if Cordova can handle monorepo structure
  - Consider impacts on plugin development workflow
  - Evaluate benefits: simpler version management, atomic commits across app+plugin

- [ ] **Framework Evaluation**: Reassess whether Cordova is the right choice
  - Consider modern alternatives: React Native, Flutter, Capacitor, native Swift/Kotlin
  - Evaluate trade-offs: development velocity, performance, platform capabilities
  - Analyze offline mapping requirements for each framework
  - Consider migration path if refactor is warranted
  - Document pros/cons of current Cordova approach vs alternatives

## Future Enhancements

- [ ] App Store submission pipeline for iOS
- [ ] Google Play Store updates for Android
- [ ] Feature parity validation between platforms
- [ ] Performance profiling and optimization
- [ ] User documentation and help system

---

**Last Updated**: 2025-12-03
