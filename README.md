GNU radio Direct Sequence Spread Spectrum blocks with examples
------

This repository contains two blocks: dsss_encoder_bb and dsss_decoder_cc which
can be used to set up a DSSS PSK transceiver (currently only BPSK has been tested to work).

Spreading codes can be specified as bit vectors (C++) or lists (Python).
Included are GRC examples for using Barker codes and pseudonoise codes with lengths
up to 1024 bits.

The DSSS encoder block takes 8 packed bits into a byte and outputs unpacked bits
- the original bits spread with the spreading bit sequence. These spread bits
can be modulated later and the chip rate will be 
Bit_rate_In * Spreading_sequence_length.

The DSSS decoder block takes as an input a RRC filtered complex waveform and outputs
a correlation value with a mean amplitude of 1 for maximum correlation. The output of the
decoder block sample rate is equal with:

input_sample_rate / (spreading_sequence_len * samples_per_symbol)

The DSSS decoder block uses a FIR filter whose length (based on spreading sequence length and
the samples per symbol value) will determine what is the maximum sample rate which can be
supported.

[![Screenshot](http://github.com/kantooon/gr-dsss/master/examples/DSSS_encode_decode.grc.png)]

Credits
-------

The original author of this GNU radio module is:
Copyright 2014 Eric de Groot

With bug fixes, additions and GRC examples by:
Copyright 2019 Adrian Musceac YO8RZZ

The code is available under the GNU GPLv3 license.
