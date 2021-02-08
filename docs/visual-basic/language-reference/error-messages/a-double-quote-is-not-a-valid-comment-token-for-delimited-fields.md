---
description: 'Hakkında daha fazla bilgi edinin: bir çift tırnak işareti, kaçış eşlerinin true olarak ayarlandığı sınırlı alanlar için geçerli bir açıklama belirteci değildir'
title: EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: d0668c6ffb479e649d4d3900070dc125db6dec05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797217"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>EscapeQuote True olarak ayarlandığında çift tırnak işareti ayrılmış alanlar için geçerli bir açıklama belirteci değildir

İçin sınırlayıcı olarak bir tırnak işareti sağlandı `TextFieldParser` , ancak `EscapeQuotes` olarak ayarlanır `True` .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `EscapeQuotes`Olarak ayarlayın `False` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](../../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
