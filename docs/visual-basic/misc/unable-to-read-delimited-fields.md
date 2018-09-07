---
title: Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: a119bf2592982b87c4bd361f9d125e6e8b7173c1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087231"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
`TextFieldParser` Tırnak işareti (") ayırıcı olarak sağlanmadığından dosyasından okunamıyor ve `EscapeQuotes` ayarlanır `True`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Ayarlama `EscapeQuotes` için `False`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextFieldParser.SetDelimiters yöntemi](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)  
- [TextFieldParser.Delimiters özelliği](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)  
- [Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
- [TextFieldParser Nesnesi](../../visual-basic/language-reference/objects/textfieldparser-object.md)
