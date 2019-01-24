---
title: EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 809cb2ab6e84f8c7f14f5a3b03dfc6142a31b5bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558975"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir
Tırnak işareti sınırlayıcı olarak sağlanan `TextFieldParser`, ancak `EscapeQuotes` ayarlanır `True`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Ayarlama `EscapeQuotes` için `False`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
