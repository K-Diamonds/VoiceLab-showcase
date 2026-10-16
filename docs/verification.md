# Verification and current limits

## Verification recorded during development

| Check | Scope |
| --- | --- |
| TypeScript and Vite build | Production frontend compilation and bundling. |
| Two Node integration tests | Loopback proxy behavior and explicit failure when no local engine is configured. |
| Eleven Python regression tests | Real media decoding/conversion, browser WebM duration recovery, subtitle boundaries, M4B chapter metadata, safe file containment, pronunciation handling, cancellation, stale retry prevention, and restart recovery. |
| Real inference smoke test | Generate an artificial voice, use it as a reference for a new sentence, then transcribe that sentence locally. |
| Real API production checks | Story/batch audio, chaptered audiobook, transcription, cleanup, timed dubbing, local text generation, clone-profile upload, WAV speech API, speaker labels, revoicing, automatic dubbing, origin rejection, and backup export. |
| Desktop interaction | Save a production, generate it, and exercise audio playback from the Electron window. |

Checks were exercised on an Apple M3 Pro development machine. Public screenshots show generic interface content; personal recordings, voice samples, private scripts, credentials, and verification output files are excluded from this showcase.

## Limits to consider in a review

- The local speech UI offers ten Qwen language choices; it does not claim universal language coverage.
- The inference path is Apple Silicon-specific. Windows/Linux inference parity and signed distributable installers are not implemented.
- Dictation is record/stop/transcribe, not live global keyboard insertion.
- Speaker labels use segment-level embedding clustering, not robust overlap-aware diarization.
- Revoicing resynthesizes a transcript; it does not preserve the source performance through a dedicated voice-conversion model.
- Dubbing replaces the original audio track; it does not restore background music or perform lip sync.
- Compact-model translations need human review.
- Cancellation cannot preempt every GPU kernel or in-progress model download.
- ElevenLabs routes exist, but live account access requires an API key and has not been claimed as verified.
- This is a local prototype, not a hosted multi-user product, audited security system, or production service with an SLA.

No private source or test fixtures are distributed here. A confidential walkthrough or source review can be requested through the repository's review-request issue template.
