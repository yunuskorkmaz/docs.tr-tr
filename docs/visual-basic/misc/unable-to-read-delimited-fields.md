---
title: Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: cd2dd4226296ecd210a1e72a7b7fb593874b0008
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398480"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor
`TextFieldParser`Sınırlayıcı olarak bir tırnak işareti (") sağlandığı ve olarak `EscapeQuotes` ayarlandığı için dosyadan okunamıyor `True` .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `EscapeQuotes`Olarak ayarlayın `False` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextFieldParser. Setsınırlayıcılar yöntemi](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser. sınırlayıcılar özelliği](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser Nesnesi](../language-reference/objects/textfieldparser-object.md)
