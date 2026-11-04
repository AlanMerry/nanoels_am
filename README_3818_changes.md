## Version 3818

Version 3818 introduces a substantial set of improvements to the automated machining functions, with major new features including Spring Pass support, TURN and FACE chamfering, improved pass control, stronger coordinate preservation, expanded setup preferences, enhanced diagnostic logging, and safer startup behaviour.

### Spring Pass

Spring Pass is a major new feature added in version 3818.

After the final normal TURN or FACE pass, the operator can optionally repeat the final cut at the same programmed depth without increasing the cut.

The prompt is:

`Spring Pass? Go=Repeat Stop=Finish`

Pressing **GO** repeats the final pass.

After the Spring Pass completes, the same prompt is displayed again, allowing additional Spring Passes if required.

Pressing **STOP** ends the Spring Pass sequence.

Spring Pass can be enabled or disabled through a setup preference.

This provides a useful finishing operation for removing residual material caused by tool deflection, machine flex, backlash effects, or finishing variation.

### Spring Pass and Chamfer sequence

Where chamfering is enabled, the automatic sequence becomes:

`TURN / FACE → Spring Pass → Chamfer → Finish`

After the operator finishes the Spring Pass sequence, the controller proceeds to the Chamfer prompt rather than ending the job immediately.

### TURN and FACE Chamfer

A new optional chamfer operation has been added to the end of automated TURN and FACE jobs.

The operator is prompted:

`Chamfer? Go=Cut Stop=Finish`

Pressing **GO** starts the chamfer.

Pressing **STOP** finishes the job without cutting the chamfer.

The chamfer dimension is entered as the required Z-axis chamfer length.

At the normal 45° setting, the corresponding X movement is calculated automatically.

Setting the chamfer dimension to zero disables the chamfer operation.

### Independent Chamfer pass count

Chamfer passes are independent from the normal TURN or FACE pass count.

A separate chamfer pass value is set using the existing **+ / -** controls.

This value is stored as a preference and shared by TURN and FACE.

For example, a TURN operation may use three normal cutting passes while the chamfer uses six lighter passes.

### Progressive TURN Chamfer cutting

TURN chamfer cutting was developed further so that the selected chamfer passes progressively remove only the material that still remains after the TURN operation.

Earlier development versions could produce either:

- an excessively heavy first chamfer pass, or
- several initial air passes.

The final implementation takes into account the amount of material already removed by the preceding TURN operation and divides only the remaining useful chamfer material between the selected chamfer passes.

The final pass still reaches the requested chamfer dimension and angle.

### FACE Chamfer datum handling

FACE chamfering uses the actual finished FACE position as its reference.

The finished Z position is captured before the tool retracts and is then reused as the chamfer datum.

This ensures the FACE chamfer is positioned relative to the finished face rather than a temporary retract position.

### Synchronized Chamfer motion

Chamfer cutting uses the same proven synchronized-motion principles as the existing Cone functionality.

The spindle and main axis provide the synchronized reference while the secondary axis follows proportionally to maintain the required chamfer angle.

This gives coordinated X/Z movement rather than treating the axes as separate unsynchronized moves.

### Reduced Chamfer feed

Chamfer cuts use a reduced synchronized pitch compared with the normal TURN or FACE feed.

This provides a finer feed during the chamfer operation and improves the resulting surface finish.

The normal TURN and FACE pitch settings are otherwise unchanged.

### Separate FACE pass count

FACE now has its own persistent normal machining pass count rather than always sharing the TURN pass count.

This allows TURN and FACE to retain different preferred pass settings.

### Axis zero and reference handling improvements

The existing axis-zero and saved-preference framework was already present before version 3818, but several important reference-handling improvements were made.

These include:

- preserving the operator-set X zero throughout TURN operations
- preventing automatic pass setup from unintentionally redefining the depth reference
- preserving the original machining coordinate system through TURN or FACE, Spring Pass, and Chamfer
- retaining the correct reference positions when the tool retracts between passes
- preserving the correct machining origin when starting a Spring Pass
- using the actual finished FACE Z position as the FACE chamfer reference
- improving consistency between displayed cut values and the original zeroed axis position.

These changes are especially important now that several automatic operations can run sequentially without redefining the machining zero.

### TURN Z preload and zero-boundary handling

TURN Z-axis preload and zero-boundary behaviour were further refined and instrumented.

Additional diagnostics were added around:

- preload movement
- return to zero
- pulse counts
- first-pass preload
- synchronized pass start
- motor position versus tool position.

This helped confirm that backlash preload and synchronized Z movement were occurring from the intended reference point.

### Pass and cut-depth display improvements

Pass-related displays were improved so that the displayed information more accurately reflects the programmed and completed cuts.

The cut-depth display was corrected to reference the original zeroed axis rather than temporary pass or retract positions.

Pass reporting was also made more consistent across the automated modes.

### Chamfer dimension shown in the final setup summary

The final TURN and FACE pre-start display now includes the configured chamfer dimension along with the other programmed movement values.

For example:

`Go X0.50 Y0.00 Z3.00 Ch1.00?`

This gives the operator another opportunity to confirm the chamfer size before starting the automatic operation.

### New setup preferences

Additional setup preferences were added to support the expanded automatic machining functions.

These include preferences associated with:

- Spring Pass enable/disable
- chamfer operation
- chamfer pass count
- TURN and FACE pass handling
- automatic-operation behaviour
- diagnostic and motion logging.

Where appropriate, these values are retained after power-off.

### Enhanced diagnostic logging

Diagnostic logging was expanded substantially during the development of version 3818.

The logging now provides much more detailed information for TURN, FACE, Spring Pass, Chamfer and general axis movement.

This includes:

- automatic operation start and completion
- individual pass start and end positions
- commanded and actual tool movement
- motor movement
- backlash compensation
- motor/tool position offsets
- preload movement
- retract movement
- return movement
- pulse counts
- expected versus actual travel
- motion-validation results
- Spring Pass activity
- chamfer setup data
- chamfer pass geometry
- synchronized chamfer movement
- final chamfer completion.

Logging can be controlled through setup preferences so detailed diagnostics can be enabled when required.

### Startup key lock

Startup input handling has been changed for improved safety and predictability.

After power-up, while the software version and IP address are displayed, only the **GO** key is accepted.

All other keys are ignored until GO is pressed.

This includes:

- numeric entry
- pitch changes
- mode keys
- zero keys
- movement controls
- setup keys.

This prevents accidental key presses or number entry from changing the pitch or another setting before startup has been acknowledged.

### Software version

Software version updated from:

`3817`

to:

`3818`

### Summary of major changes

Version 3818 includes:

- Spring Pass support
- repeatable finishing passes
- Spring Pass enable/disable preference
- TURN and FACE Chamfer support
- independent Chamfer pass count
- progressive TURN Chamfer cutting
- corrected FACE Chamfer datum handling
- synchronized Chamfer motion
- reduced Chamfer feed
- TURN/FACE → Spring Pass → Chamfer workflow
- separate FACE pass count
- improved axis-zero and origin preservation
- improved TURN Z preload and zero-boundary handling
- corrected cut-depth and pass displays
- additional setup preferences
- persistent automatic-operation settings
- Chamfer dimension in the final start summary
- startup GO-only key lock
- significantly enhanced motion and diagnostic logging.

Overall, version 3818 represents a major expansion of the automatic machining capability while also improving operator control, coordinate consistency, finishing quality, startup safety, and troubleshooting information.
