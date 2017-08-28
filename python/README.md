# SentencePiece Python Wrapper

Python wrapper for SentencePiece with SWIG. This module wrappes sentencepiece::SentencePieceProcessor class with the following modifications:
* Encode and Decode methods are re-defined as EncodeAsIds, EncodeAsPieces, DecodeIds and DecodePieces respectevely.
* SentencePieceText proto is not supported.

## Build and Install SentencePiece
You need to install SentencePiece before before installing this python wrapper.

```
% pip install sentencepiece
```

You can install this module manually as follows:
```
% python setup.py build
% sudo python setup.py install
```

If you don’t have write permission to the global site-packages directory or don’t want to install into it, please try:
```
% python setup.py install --user
```

## Usage

```
% python
>>> import sentencepiece as spm
>>> sp = spm.SentencePieceProcessor()
>>> sp.Load("test/test_model.model")
True
>>> sp.EncodeAsPieces("This is a test")
['\xe2\x96\x81This', '\xe2\x96\x81is', '\xe2\x96\x81a', '\xe2\x96\x81', 't', 'est']
>>> sp.EncodeAsIds("This is a test")
[284, 47, 11, 4, 15, 400]
>>> sp.DecodePieces(['\xe2\x96\x81This', '\xe2\x96\x81is', '\xe2\x96\x81a', '\xe2\x96\x81', 't', 'est'])
'This is a test'
>>> sp.DecodeIds([284, 47, 11, 4, 15, 400])
'This is a test'
>>> sp.GetPieceSize()
1000
>>> sp.IdToPiece(2)
'</s>'
>>> sp.PieceToId('</s>')
2
```