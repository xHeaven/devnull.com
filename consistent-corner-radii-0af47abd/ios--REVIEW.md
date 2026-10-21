# iOS Simulator review

Device: iPhone 17, iOS 27.0; Safari; 402 x 874 screenshots at 1x. iPhone 18 Pro was unavailable (DEVICE_IN_USE), so its existing agent session was preserved. The owned iPhone 17 was closed and shut down successfully with T3 device_close at completion. Servers were left running.

Scope: actual local sign-in as fictional Alex Rivera (local-dev), touch interactions and native software keyboard. No repository edits, external-service writes, message sends, commit submissions, org creation, or host-global settings changes. Light theme only on device; Chrome media covers the broader theme/viewport matrix. Native recordings were not captured; these are reviewed screenshots.

## Results

No introduced corner-radius or geometry regression was observed in the exercised states. Profile bio mention/logo insets, rank and achievements, mobile FAB/navigation/menu, search results, Remotes bubbles/reaction chips/tray/emoji sheet, live sheet, org selected-person checkbox/chip and image-viewer controls rendered with the requested shapes. Avatars, graph marks and signal dots remain circular. Search-result navigation, achievement opening, actual FAB opening, live-sheet opening, long-press reactions and image ALT toggle worked.

Native keyboard checks: the composer Commit and Remotes Push controls remain visible; developer search selection and filtered emoji options remain visible and usable. New org has a pre-existing exception, detailed below.

## Pre-existing New org keyboard limitation

On both the final patch server (8187) and baseline server (8188), selecting Drew and then focusing Find people shows counter 2/100 and the selected member chip but clips Create org below the dialog. A scroll attempt on the patch did not expose it. Dismissing the native keyboard with Done reveals the enabled Create org button, preserving an operable path. Creation was deliberately not submitted. The paired baseline screenshot demonstrates that this is unchanged by the radius-only patch.

The current layout uses an overflow-hidden dialog and a min-h-40 candidates region. No unrelated layout repair was made.

## Final artifact map

All filenames below have prefix iphone17-ios27- and are in this directory.

| Surface/state | Final filename suffix |
|---|---|
| Log, pending status, active navigation | log-light.png |
| Profile bio/logo/rank, FAB and selected mobile navigation | profile-light.png |
| Achievement dialog | achievements-light.png |
| FAB opens composer; Commit visible above native keyboard | compose-keyboard-light.png |
| Final-build mobile dropdown/menu geometry | mobile-menu-final-light.png |
| Developer search with keyboard and selected result | search-keyboard-light.png |
| Sam live sheet | live-sheet-light.png |
| Remotes composer with keyboard and Push visible | remotes-keyboard-light.png |
| Touch long-press reaction tray | reaction-tray-light.png |
| Expanded emoji sheet | emoji-sheet-light.png |
| Filtered emoji options with keyboard | emoji-keyboard-light.png |
| Image viewer controls/commit sheet | image-viewer-light.png |
| Image ALT description toggle | image-description-light.png |
| Final-build New org unchecked rectangular selector, keyboard | org-unselected-keyboard-light.png |
| Final-build New org checked selector/member chip, no keyboard | org-selected-light.png |
| Final-build New org checked selector/member chip, keyboard clipping | org-selected-keyboard-light.png |
| Same patch state after ineffective scroll | org-keyboard-after-scroll-light.png |
| Keyboard dismissal restores enabled Create org | org-after-keyboard-dismiss-light.png |
| Baseline unchecked circular selector with keyboard | baseline-org-unselected-keyboard.png |
| Baseline checked circle/member chip with identical keyboard clipping | baseline-org-selected-keyboard.png |

## Superseded captures / publication cautions

- mobile-menu-light.png predates the last shared menu-shell radius adjustment. Use mobile-menu-final-light.png.
- An earlier attempted capture at org-selected-keyboard-light.png showed counter 1/100, an unchecked selector and Safari text-edit menu because an accessibility fallback ref resolved to an offset coordinate. It was replaced at that same path with the reviewed final image showing counter 2/100, checked rectangle and member chip, without the text-edit menu. Do not use the earlier tool-output image as selection evidence.
- The temporary profile-fab-position.png image was removed after it was used to resolve fallback coordinates.
- org-keyboard-after-scroll-light.png and the baseline images are limitation/comparison evidence, not a successful keyboard-visible-primary-action claim.

Every listed final screenshot was opened and visually reviewed. Some Safari accessibility snapshots fell back to XCTest/private AX and had incorrect vertical coordinates; affected actions were corrected using fresh screenshots and their actual on-screen coordinates. Resulting states were verified from screenshots and fresh snapshots rather than trusting tap success alone.
