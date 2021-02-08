---
description: 'Hakkında daha fazla bilgi edinin: sıra sayısı geçerli değil'
title: Sıra sayısı geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7c58675a08d3821cd05ba0109e5ce0107c68e497
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795527"
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
