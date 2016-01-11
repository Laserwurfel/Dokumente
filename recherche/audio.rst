OpenAL
======

OpenAL_ ist wie OpenGL aufgebaut, wodurch wir und Lernaufwand sparen würden.
PyAL_ benötigt OpenAL welches separat installiert werden muss.

.. _OpenAL: http://www.openal.org/
.. _PyAL: https://pythonhosted.org/PyAL/index.html

Externe Decoder
===============

PyMedia_, audioread_ und decoder.py_ benötigt externe Programme.

.. _PyMedia: http://pymedia.org//index.html
.. _audioread: https://github.com/beetbox/audioread
.. _decoder.py: https://bitbucket.org/tom_slick/decoder.py

PortAudio
=========

PortAudio_ und dessen Python Bindings PyAudio_ können nur Ton abspielen, aber
keine Audiodateien (bis auf riesige .wav Dateien) lesen.

.. _PortAudio: http://www.portaudio.com/
.. _PyAudio: https://people.csail.mit.edu/hubert/pyaudio/

FFmpeg/Libav
============

PyAV_ könnte alle möglichen Audiodateien lesen, man muss aber FFmpeg oder Libav
richtig installieren (man kann es nicht einfach mitliefern) was sehr aufwändig
sein kann.

.. _PyAV: https://mikeboers.github.io/PyAV/

Lösung
======

Audiodateien mit decoder.py einlesen und dann mit PyAudio abspielen.
Decoder.py ist derzeit nicht über Pypi verfügbar und muss deshalb manuell
installiert werden. Wir werden ein Skript schreiben, dass diesen Vorgang
automatisiert.

