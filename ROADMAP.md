
## Overview

Develop a compact, camera-based system that measures hand movement precision and consistency while a user traces a predefined path.

The system will track a pen marker through a live camera feed, reconstruct the traced trajectory, compare it with a reference curve, and calculate interpretable performance metrics. The project will prioritise repeatable measurements, lightweight computer vision, and eventual portability to a small computer.

Potential use cases include darts, archery, and activities or conditions where hand motor control is relevant. The system is an assessment aid, not a medical diagnostic tool.

## Current Status

- [x] Project concept selected and refined.
- [x] Initial user survey created and responses gathered.
- [x] Core requirements and high-level system workflow defined.
- [x] Initial system and pen-marker detection flowcharts drafted.
- [x] Path-tracing component started.
- [ ] End-to-end measurement pipeline completed and validated.
- [ ] Physical enclosure and portable hardware finalised.

## Roadmap

### Phase 1: Define and validate the assessment

- [x] Explore possible applications and select hand precision assessment as the core concept.
- [x] Create a survey to investigate likely users, useful metrics, preferred result formats, portability, and acceptable test duration.
- [x] Gather initial survey responses.
- [x] Identify precision as a key metric and consider separate use profiles for different applications.
- [ ] Summarise survey findings and translate them into final, prioritised requirements.
- [ ] Define the intended user workflow and target assessment duration.
- [ ] Document intended use, limitations, and the distinction between a general hand-control assessment and medical diagnosis.

Exit criteria
- The intended use cases and core requirements are documented.
- The required outputs and approximate test duration are defined.
- The system's limitations are clear to users.

### Phase 2: Generate and represent the reference curve

- [ ] Generate a curve for the user to trace.
- [ ] Establish how the reference curve will be printed or displayed on paper.
- [ ] Detect or otherwise obtain the reference curve's points and represent them as coordinates.
- [ ] Define a consistent coordinate system for the reference curve and camera image.
- [ ] Overlay the detected or reconstructed reference curve on an image to validate its coordinates.
- [ ] Test the coordinate representation with curves of different shapes.

Exit criteria
- The reference curve can be represented as a set of coordinates.
- An overlay or equivalent visual check confirms that the coordinates correspond to the printed curve.
- The reference path can be used by the analysis pipeline.

### Phase 3: Track the pen and reconstruct the trace

- [ ] Capture frames from a live camera feed.
- [ ] Pre-process frames to improve marker detection.
- [ ] Identify candidate red regions and select a suitable marker candidate.
- [ ] Estimate the pen-tip position in each frame.
- [ ] Record each detected position with a timestamp and, where practical, a confidence value.
- [ ] Record missing detections rather than silently treating them as valid positions.
- [ ] Display the tracked trajectory during or after the tracing test.
- [ ] Test tracking under different lighting conditions and against relevant background colours.

Exit criteria
- The system can track the marker through a test and reconstruct the observed trajectory.
- Missing detections can be identified.
- Tracking behaviour and known limitations are documented.

### Phase 4: Align paths and calculate precision

- [ ] Map the reference-curve coordinates and tracked pen coordinates into the same coordinate system.
- [ ] Implement a method for comparing the traced path with the reference path.
- [ ] Calculate the distance between the traced trajectory and the target curve.
- [ ] Investigate how to distinguish overall path accuracy from small, rapid variations in movement.
- [ ] Test the calculations using deliberately different tracing paths with known or expected deviations.
- [ ] Check how missing detections, uneven sampling, and path alignment affect the results.

Exit criteria
- The traced and reference paths can be compared quantitatively.
- The calculation method is documented and tested against controlled examples.
- Known sources of error and ambiguity are recorded.

### Phase 5: Validate and present performance metrics

- [ ] Implement mean deviation to describe average distance from the reference path.
- [ ] Implement maximum deviation to describe the largest measured distance from the reference path.
- [ ] Investigate consistency as a measure of variation in deviation across the trace.
- [ ] Investigate smoothness, including changes in direction or speed, once the underlying measurements have been validated.
- [ ] Validate each metric against traces with deliberately different characteristics.
- [ ] Display the traced path overlaid on the reference curve.
- [ ] Highlight sections with larger deviations using visual indicators.
- [ ] Present numerical results clearly and include units where meaningful.
- [ ] Decide whether results should be shown as separate measurements, an overall score, or both, based on the intended use and validation.

Exit criteria
- Each reported metric has a documented definition.
- Tests show whether the metrics respond as expected to controlled differences in tracing.
- The result screen communicates the measurements without overstating what they mean.

### Phase 6: Integrate the software workflow

- [ ] Connect curve generation, reference-path representation, pen tracking, analysis, and results display into one workflow.
- [ ] Define how a test starts and finishes.
- [ ] Handle missing marker detections and incomplete traces.
- [ ] Save results in a consistent format for later comparison.
- [ ] Test the complete workflow from starting an assessment to displaying and saving results.
- [ ] Refine the interface and feedback based on testing.

Exit criteria
- A user can complete an assessment using one integrated workflow.
- The system produces and saves results consistently.
- Errors and incomplete tests are handled in a clear way.

### Phase 7: Evaluate repeatability and sources of error

- [ ] Repeat the same tracing under consistent conditions to assess measurement repeatability.
- [ ] Investigate the effects of missed pen detections, camera noise, lighting variation, and differences in setup.
- [ ] Check whether changes in measured results reflect changes in the trace rather than changes in camera position or paper placement.
- [ ] Compare results from controlled traces with their expected differences.
- [ ] Document the testing method, findings, limitations, and any changes made as a result.
- [ ] Refine the software based on the evaluation.

Exit criteria
- Repeatability has been assessed using repeated tests.
- Important error sources have been investigated.
- Conclusions are supported by recorded tests rather than assumptions.

### Phase 8; Final evaluation and documentation

- [ ] Run a final set of controlled tests against the project requirements.
- [ ] Record performance, repeatability, limitations, and unresolved issues.
- [ ] Document the hardware, software dependencies, setup procedure, and assessment workflow.
- [ ] Explain the meaning and limitations of each metric.
- [ ] Identify realistic improvements for a future version.

Exit criteria
- Each requirement has a recorded status and supporting evidence.
- The project can be set up and run using the documentation.
- Limitations and future improvements are clearly stated.

## Flowcharts

* Already made - to be added very soon

## Key Requirements

| Requirement | Rationale | Validation approach |
|---|---|---|
| Track the pen tip reliably | Core function of the system | Compare tracked positions with controlled observations and inspect missed detections |
| Compare movement against a known path | Needed for quantitative measurement | Validate coordinate alignment and distance calculations using known traces |
| Keep camera position fixed | Improves measurement consistency | Repeat tests with a standardised setup |
| Position A4 paper consistently | Makes tests comparable | Use a repeatable placement method and check alignment |
| Avoid a large machine-learning model | Supports lightweight hardware | Test performance using the intended computer-vision approach |
| Design for portability | Supports practical use | Evaluate the physical prototype and setup process |
| Produce interpretable results | Makes measurements useful | Test metrics against deliberately different tracing patterns |
| Document limitations | Prevents overinterpretation | Record known error sources and explain what the results can and cannot establish |

## Technical Information

- Language: Python
- Computer vision: OpenCV (`cv2`)
- Initial development platform: A conventional Windows computer with a connected camera
- Target platform: A compact computer with camera support, subject to performance testing, most likely a Linux-based OS

## Risks and Open Questions

* `(TODO)` To consider

## Possible Future Improvements

- Explore different reference-curve shapes and assessment profiles.
- Compare alternative methods for measuring smoothness and consistency.
- Investigate longer-term tracking of results across sessions, if appropriate for the use case.
- Improve calibration and compensate for perspective where testing shows it is necessary.
- Explore additional feedback and reporting options based on user needs.

## Development Log

* This is summarised - my full devlogs contain more detail on my thought process and everything I considered :)

| Date | Milestone |
|---|---|
| 13 September 2026 | Explored initial project ideas and selected camera-based hand-movement analysis as the main concept. |
| 24 September 2026 | Refined the project into a broader hand precision assessment rather than a tool aimed only at a specific medical condition. |
| 26 September 2026 | Designed and began distributing a survey to investigate user needs and requirements. |
| 4 October 2026 | Initial survey responses supported darts/archery and motor-control-related use cases; precision was identified as an important metric. |
| 20 October 2026 | Defined the project brief, requirements, system workflow, pen-marker detection approach, and initial development tasks. |
| 21 October 2026 | Began developing the path-tracing component. |

