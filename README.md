

::::::::::VECTOR SYNTHESIS LIBRARY ::::::::::

The Vector Synthesis library allows the creation and manipulation of 2D and 3D vector shapes, Lissajous figures, and scan processed image and video inputs using audio signals sent directly to oscilloscopes, Vectrex game consoles, ILDA laser displays, or oscilloscope emulation softwares using the Pure Data programming environment. 

Audio waveforms control the vertical and horizontal movements as well as the brightness of a single beam of light, tracing shapes, points and curves with a direct relationship between sound and image.

The technique is based on the well-known principle of Lissajous figures, which are a mathematical representation of complex harmonic motion. Originally displayed by reflecting light between mirrors attached to a pair of vibrating tuning forks, we are most used to seeing them on the screen of an oscilloscope, where they can be produced using pairs of electronic oscillators tuned to specific ratios. 

There is a wealth of such experiments from the 1950s onward by major figure such as Mary Ellen Bute, John Whitney, Larry Cuba, Manfred Mohr, Nam June Paik, Ben Laposky, Bill Etra, and Steina & Woody Vasulka, which were all highly inspiration to the development of this library.

Tutorials, announcements, and testing here: 

https://www.facebook.com/groups/vectorsynthesis/

Demo videos here: 

https://vimeo.com/macumbista

 If this library has been useful, please consider making a donation towards the development:
 
 [![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=SPHWJSJWH92GG&source=url)
 
 Or you can support my research by ordering a copy of the Vector Synthesis book: 
 
 http://www.lulu.com/shop/derek-holzer/vector-synthesis-a-media-archaeological-investigation-into-sound-modulated-light/paperback/product-24379956.html
 
 You can also take a workshop from me. My workshops are annouced on the Facebook group above or on my website: 
 
 http://macumbista.net 
 

*REQUIREMENTS*

——SOFTWARE
	
	Pure Data "Vanilla", version 0.49 or newer: 

https://puredata.info/downloads/pure-data

	Gem 0.93.3 (OPTIONAL, used in scan processor only). 
	Gem is installed via deken, Pd’s externals manager (Menu bar: Help-->Find Externals)
	
	NOTE: Pd-Extended is too old for some features of this library. Do not rely on it.
	Purr-Data is also not explicitely supported.
	
——AUDIO INTERFACE
	
	DC-coupled audio interface 
	Minimum 3 output channels (horizontal, vertical, brightness)
	5 output channels recommended if seperate stereo audio channels are desired
	High sampling rate also recommended (192 kHz if possible)
	Balanced outputs recommended for ILDA laser display control
	Tested with MOTU UltraLite mk3 USB2 audio interface (Ten DC coupled, balanced outputs)
	
——DISPLAYS
	
	Oscilloscope or vector monitor (not vectorscope!) with X/Y/Z inputs (all DC-coupled)
	
	—or—
	
	Vectrex game console modified for X/Y/Z input (all DC-coupled) according to these instructions:

http://users.sussex.ac.uk/~ad207/adweb/assets/vectrexminijackinputmod2014.pdf
	
	—or—
	
	ILDA laser display with the following adapter from your minimum 5 channel, DC coupled 
	audio interface with balanced outputs (recommended: MOTU UltraLite) and the following 
	DIY adapter box: 

https://github.com/ffd8/dac_ilda 
	
	—or—
	
	Oscilloscope software with X/Y/Z inputs such as Hansi Raber's "Oscilloscope!" app

https://github.com/kritzikratzi/Oscilloscope/releases/tag/1.0.9
	
	(Hold SHIFT key when selecting input for third channel brightness control)
	plus audio loopback application such as SoundFlower or Virtual Audio Cable. 
	Please see SOFTWARE-OSCILLOSCOPE-TUTORIAL-WIN.pdf or SOFTWARE-OSCILLOSCOPE-TUTORIAL.pdf
	for further details on setup.
	
	NOTE: the Z axis should control the brightness of the beam, not 3D depth
	

*GENERAL NOTES*

	Start with the first files in the library, they are the tutorials:
	
		000.A.VECTOR_GENERATORS.pd
		000.B.2D_VECTORS.pd
		000.C.3D_VECTORS.pd
		000.D.VECTOR_MODIFIERS.pd
		000.G.VECTOR_MULTIPLEXING.pd
		000.H.ILDA_OUTPUT.pd
		000.I.PRESET_SYSTEM.pd
		
	The files with "gui" in their name are designed to be patched together much like a modular synth.
	The files with "ilda" in their name are designed to be used with the 000.H.ILDA_OUTPUT.pd patch.
	The files with "help" in their name are good examples to start with to learn more code. 
	The files without "gui" or "help" in their name are the abstractions themselves, without any controls.
	The files with a ".txt" extension are backup data for the various 3D shapes.
	
	
	For control of an oscilloscope, the following channels are used (where Audio Left and Right can be reassigned):

	Audio Interface Output 1 : Horizontal
	Audio Interface Output 2 : Vertical
	Audio Interface Output 3 : Brightness
	Audio Interface Output 4 : Audio Left (Horizontal * Brightness)
	Audio Interface Output 5 : Audio Right (Vertical * Brightness)
	
	For ILDA laser control, the channel assignement looks like this (where Audio Left and Right can be reassigned):
	
	Audio Interface Output 1 : Horizontal
	Audio Interface Output 2 : Vertical
	Audio Interface Output 3 : Brightness (normally not used, kept for compatibility)
	Audio Interface Output 4 : Red
	Audio Interface Output 5 : Green
	Audio Interface Output 6 : Blue
	Audio Interface Output 7 : Audio Left (Horizontal * Brightness)
	Audio Interface Output 8 : Audio Right (Vertical * Brightness)

	Higher sampling rate = higher resolution/fewer errors in the vector shapes
	Tested at 44.1kHz, 48kHz, 96kHz, 192kHz


*USING NON-RECOMMENDED HARDWARE*

	A stereo audio output is also usable, as well as a more common X/Y oscilloscope display,
	however there will be no brightness control.
	
	Normal laptop headphone audio outputs generate a lot of noise which is visible in the image.
	
	An AC-coupled soundcard or display will show noticeable distortions in the shape, 
	and the vector shapes will always appear in the center of the screen.

	DC-coupling is also necessary for brightness control.

	Brightness control is essential for multiplexing, scan processing of videos and photos, 
	and a number of other interesting visual effects, however you can still use this 
	library for many things without it.
	
	You can find an excellent overview of how DC COUPLING and SAMPLING RATE affect the oscilloscope 
	image in this video on Jerobeam Fenderson's YouTube channel:
	
[![](http://img.youtube.com/vi/piZPIMYfq0c/0.jpg)](http://www.youtube.com/watch?v=piZPIMYfq0c "Oscilloscope Music Tutorial 2: Setup (Compression, DC-coupling, Sampling Rate, Aliasing by Jerobeam Fenderson)")


*ACKNOWLEDGEMENTS*


I would like to thank the following people and institutions for their support and encouragement of the project: 

	Antti Ikonen/Aalto University Media Lab (Helsinki FI)
	Marianne Decoster-Taivalkoski/Centre for Music & Technology of the Sibelius Academy (Helsinki FI)
	Jason and Debora Bernagozzi/Signal Culture (Owego NY USA)
	Borut Savski/Cirkulacija2 (Ljubljana SI)
	Lars Larsen/LZX Industries (Portland OR USA)
	Gisle Frøysland/Piksel (Bergen NO)
	Alfredo Ciannameo and Lieke Ploeger/Spektrum (Berlin DE)
	Svetlana Maras/Radio Belgrade Electronic Studio (Belgrade SRB)
	Tapio “Tassu” Takala/Aalto University Department of Computer Science (Helsinki FI)
	Joseph Hyde/Seeing Sound/Bath Spa University (Bath UK)
	Jeff Chippewa & Nicolas Bernier/Canadian Electroacoustic Community (Montreal CA)
	Kari Yli-Annala/AAVE Festival (Helsinki FI)
	Andy Farnell
	Ivan Marušić Klif
	Dave Jones
	Nathan Thompson
	Roland Lioni/Akira’s Rebirth
	Hansi Raber
	Jerobeam Fenderson
	Lee Montgomery
	Andrew Duff
	Marco Donnarumma
	Robert Henke
	Chris King
	and finally the Video Circuits online community, without whom I never would have started down 
	this crazy road


Derek Holzer
Helsinki June 2019
http://macumbista.net
macumbista AT THE DOMAIN gmail DOT com
















# vectorsynthesis
