---
title: Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: bc19fc7496b31eabca6dabedf212c89d6f5450d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819281"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
`TextFieldParser` Tırnak işareti (") ayırıcı olarak sağlanmadığından dosyasından okunamıyor ve `EscapeQuotes` ayarlanır `True`.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Ayarlama `EscapeQuotes` için `False`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextFieldParser.SetDelimiters yöntemi](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser.Delimiters özelliği](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser Nesnesi](../../visual-basic/language-reference/objects/textfieldparser-object.md)
