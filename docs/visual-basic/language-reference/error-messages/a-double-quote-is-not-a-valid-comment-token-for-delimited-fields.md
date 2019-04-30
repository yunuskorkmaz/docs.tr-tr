---
title: EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 6e55fde395cec2fcd4053e66d855750945ea1448
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751663"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir
Tırnak işareti sınırlayıcı olarak sağlanan `TextFieldParser`, ancak `EscapeQuotes` ayarlanır `True`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Ayarlama `EscapeQuotes` için `False`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
