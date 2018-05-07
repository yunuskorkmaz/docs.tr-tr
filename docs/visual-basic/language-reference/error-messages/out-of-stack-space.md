---
title: Yığın için ayrılan alan doldu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="out-of-stack-space-visual-basic"></a>Yığın için ayrılan alan doldu (Visual Basic)
Yığın yürütülen programınızı taleplerini ile dinamik olarak büyür ve küçülür bellek bir çalışma alanıdır. Kendi sınırlarını aştı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Yordamlar çok fazla iç içe değil olduğunu denetleyin.  
  
2.  Özyinelemeli yordamlar düzgün sonlandırma emin olun.  
  
3.  Yerel değişkenler kullanılabilir alandan daha fazla yerel değişken gerektiriyorsa, bazı değişkenler modülü düzeyinde bildirme deneyin. Ayrıca tüm değişkenleri yordamda statik koyarak bildirebilirsiniz `Property`, `Sub`, veya `Function` anahtar sözcüğüyle `Static`. Veya kullanabilirsiniz `Static` yordamları statik bağımsız değişkenler bildirmek için deyimi.  
  
4.  Sabit uzunluklu dizeler değişken uzunluklu dizeler daha fazla yığın alanı kullanırken, sabit uzunluklu dizeler değişken uzunluklu dizeler olarak bazıları yeniden tanımlayın. Burada, hiçbir yığın alanı gerektiriyor modülü düzeyinde dize tanımlayabilir.  
  
5.  Sayısını denetleyin iç içe geçmiş `DoEvents` işlev çağrılarını kullanarak `Calls` hangi yordamların yığında etkin görüntülemek için iletişim kutusu.  
  
6.  "Olay cascade" olay yordamı zaten yığında çağıran bir olay tetikleme tarafından neden değil emin olun. Bir olay cascade bir Sonlandırılmamış özyinelemeli yordam çağrısına benzer, ancak çağrı kodda açık bir çağrı yerine, Visual Basic yapıldığından kadar belirgin. Kullanım `Calls` hangi yordamların yığında etkin görüntülemek için iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bellek pencereleri](/visualstudio/debugger/memory-windows)
