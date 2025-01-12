# Description
Simple 8 step sequencer. Has controls per step for envelope decay, pitch, and step activation.

# Controls
Edit and play mode, press encoder to switch modes. Edit is multicolored, play is green.

## Edit mode
| Control | Description | Comment |
| --- | --- | --- |
| Encoder | Rotate: run through steps | |
| Knob 1 | Set decay time | |
| Knob 2 | Set pitch | A pentatonic major |
| Button 1 | Toggle cycling | so you can listen to the step |
| Button 2 | Activate / deactivate a step | If on, the step will play when the sequence runs |
| Led 1 | Color: Current step | Colors see below |
| Led 2 | On/Off: Step active/inactive | |

When a step is activated, its envelope will cycle. Listen for pitch and envelope shape.

### Step Colors
| Step | Color |
| --- | --- |
| 1 | Red |
| 2 | Green |
| 3 | Blue |
| 4 | White |
| 5 | Purple |
| 6 | Cyan |
| 7 | Gold / Orange |
| 8 | Yellow |


## Play mode
| Control | Description | Comment |
| --- | --- | --- |
| Encoder | Rotate: Waveform | Ramp, Square |
| Knob 1 | Tempo | |
| Knob 2 | Filter cutoff |  |


# Code Snippet
    void NextSamples(float& sig)
    {
        env_out = env.Process();
        osc.SetAmp(env_out);
        sig = osc.Process();
        sig = flt.Process(sig);

        if (tick.Process() && !edit)
        {
	    step++;
    	    step %= 8;
    	    if (active[step])
    	    {
    	        env.Trigger();
    	    }
        }

        if (active[step])
        {
    	    env.SetTime(ADENV_SEG_DECAY, dec[step]);
    	    osc.SetFreq(pitch[step]);
    	    if (edit && ! env.IsRunning())
    	    {
    	        env.Trigger();
    	    }
        }
    }
