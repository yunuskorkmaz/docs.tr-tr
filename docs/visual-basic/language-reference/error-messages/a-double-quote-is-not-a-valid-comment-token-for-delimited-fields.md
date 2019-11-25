---
title: EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: df7868c510eaacbad1d4421259234f4187f60cd7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976214"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir

`TextFieldParser`sınırlayıcı olarak bir tırnak işareti sağlandı, ancak `EscapeQuotes` `True`olarak ayarlanmıştır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `EscapeQuotes` `False`olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
