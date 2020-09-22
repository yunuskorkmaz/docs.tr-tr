---
title: Yığın için ayrılan alan doldu
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: afb6a42372bdbd2e49ac15fbbf2b9e254f8db431
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871310"
---
# <a name="out-of-stack-space-visual-basic"></a>Yığın için ayrılan alan doldu (Visual Basic)

Yığın, yürütülen programınızın taleplerini dinamik olarak büyüyen ve küçüldüğü belleğin çalışma alanıdır. Sınırları aşıldı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yordamların çok derin iç içe olmadığını kontrol edin.  
  
2. Özyinelemeli yordamların düzgün sonlandırılmadığından emin olun.  
  
3. Yerel değişkenler kullanılabilir olandan daha fazla yerel değişken alanı gerektiriyorsa, modül düzeyinde bazı değişkenler bildirmeyi deneyin. Ayrıca `Property` ,, `Sub` veya `Function` anahtar sözcüğünden önce kullanarak statik yordamdaki tüm değişkenleri de bildirebilirsiniz `Static` . Ya da `Static` yordamlar içindeki bağımsız statik değişkenleri bildirmek için ifadesini kullanabilirsiniz.  
  
4. Sabit uzunluklu dizeler değişken uzunluklu dizeler olarak daha fazla yığın alanı kullanırken, sabit uzunluklu Dizelerinizin bazılarını değişken uzunluklu dizeler olarak yeniden tanımlayın. Dizeyi, yığın alanı gerektirmeyen modül düzeyinde de tanımlayabilirsiniz.  
  
5. `DoEvents` `Calls` Yığın üzerinde etkin olan yordamları görüntülemek için iletişim kutusunu kullanarak iç içe geçmiş işlev çağrılarının sayısını denetleyin.  
  
6. Yığında zaten olan bir olay yordamını çağıran bir olay tetikleyerek bir "olay basamaklandırmaya" neden olmadığından emin olun. Olay basamaklama, Sonlandırılmamış özyinelemeli yordam çağrısına benzerdir, ancak çağrı, koddaki açık bir çağrı yerine Visual Basic tarafından yapıldığından daha az açıktır. `Calls`Yığında etkin olan yordamları görüntülemek için iletişim kutusunu kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bellek Pencereleri](/visualstudio/debugger/memory-windows)
