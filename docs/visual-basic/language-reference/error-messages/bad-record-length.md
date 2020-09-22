---
title: Hatalı kayıt uzunluğu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869260"
---
# <a name="bad-record-length"></a>Hatalı kayıt uzunluğu

Bu hatanın olası nedenleri arasında:  
  
- ,, Veya ifadesinde belirtilen bir kayıt değişkeninin uzunluğu `FileGet` , `FileGetObject` `FilePut` `FilePutObject` karşılık gelen bildirimde belirtilen uzunluktan farklı `FileOpen` .  
  
- Or deyimindeki değişken veya `FilePut` `FilePutObject` değişken uzunluklu bir dize içeriyor.  
  
- Veya içindeki değişkeni `FilePut` `FilePutObject` bir tür ya da içerir `Variant` .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Kayıt değişkeninin türünü tanımlayan Kullanıcı tanımlı türdeki sabit uzunluklu değişkenlerin değerlerinin toplamının `FileOpen` deyimin yan tümcesinde belirtilen değerle aynı olduğundan emin olun `Len` .  
  
2. `FilePut`Or deyimindeki değişken veya `FilePutObject` bir değişken uzunluklu dize içeriyorsa, değişken uzunluklu dizenin, `Len` deyimin yan tümcesinde belirtilen kayıt uzunluğundan en az 2 karakter daha kısa olduğundan emin olun `FileOpen` .  
  
3. Ya da ' deki değişken `FilePut` veya `FilePutObject` içeriyorsa, `Variant` değişken uzunluklu dizenin en az 4 bayt olduğundan `Len` deyimin yan tümcesinde belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `FileOpen` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
