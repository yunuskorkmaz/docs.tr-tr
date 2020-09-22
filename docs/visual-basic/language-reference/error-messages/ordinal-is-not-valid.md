---
title: Sıra sayısı geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 64f56b2ecace0ceafb310a175ea605e6959b7256
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871396"
---
# <a name="ordinal-is-not-valid"></a>Sıra sayısı geçerli değil

Bir dinamik bağlantı kitaplığı (DLL) çağrısı, söz dizimini kullanarak bir yordam adı yerine bir sayı kullanmak için belirtilmiştir `#num` . Bu hatanın olası nedenleri şunlardır:  
  
- `#num`İfadeyi bir sıraya dönüştürme girişimi başarısız oldu.  
  
- `#num`BELIRTILEN dll 'de herhangi bir işlev belirtmiyor.  
  
- Bir tür kitaplığında geçersiz bir sıra numarası iç kullanımına neden olan geçersiz bir bildirim vardır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. İfadenin geçerli bir sayıyı temsil ettiğinden emin olun veya yordamı ada göre çağırın.  
  
2. `#num`DLL 'de geçerli bir işlev tanımladığından emin olun.  
  
3. Kodu açıklama ekleyerek soruna neden olan yordam çağrısını yalıtın. `Declare`Yordam için bir ifade yazın ve sorunu tür kitaplığı satıcısına bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Declare Deyimi](../statements/declare-statement.md)
