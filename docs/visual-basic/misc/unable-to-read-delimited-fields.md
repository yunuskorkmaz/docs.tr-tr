---
description: 'Daha fazla bilgi edinin: bir çift tırnak, kaçış eşlerini true olarak ayarlandığında geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamadı'
title: Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 066b5110eaddad74b64f1d86683d7ca2a0a619f7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474401"
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
