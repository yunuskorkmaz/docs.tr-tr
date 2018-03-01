---
title: "Yığın için ayrılan alan doldu (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a>Yığın için ayrılan alan doldu (Visual Basic)
Yığın yürütülen programınızı taleplerini ile dinamik olarak büyür ve küçülür bellek bir çalışma alanıdır. Kendi sınırlarını aştı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Yordamlar çok fazla iç içe değil olduğunu denetleyin.  
  
2.  Özyinelemeli yordamlar düzgün sonlandırma emin olun.  
  
3.  Yerel değişkenler kullanılabilir alandan daha fazla yerel değişken gerektiriyorsa, bazı değişkenler modülü düzeyinde bildirme deneyin. Ayrıca tüm değişkenleri yordamda statik koyarak bildirebilirsiniz `Property`, `Sub`, veya `Function` anahtar sözcüğüyle `Static`. Veya kullanabilirsiniz `Static` yordamları statik bağımsız değişkenler bildirmek için deyimi.  
  
4.  Sabit uzunluklu dizeler değişken uzunluklu dizeler daha fazla yığın alanı kullanırken, sabit uzunluklu dizeler değişken uzunluklu dizeler olarak bazıları yeniden tanımlayın. Burada, hiçbir yığın alanı gerektiriyor modülü düzeyinde dize tanımlayabilir.  
  
5.  Sayısını denetleyin iç içe geçmiş `DoEvents` işlev çağrılarını kullanarak `Calls` hangi yordamların yığında etkin görüntülemek için iletişim kutusu.  
  
6.  "Olay cascade" olay yordamı zaten yığında çağıran bir olay tetikleme tarafından neden değil emin olun. Bir olay cascade bir Sonlandırılmamış özyinelemeli yordam çağrısına benzer, ancak çağrı tarafından yapıldığından kadar belirgin [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodda açık bir çağrı yerine. Kullanım `Calls` hangi yordamların yığında etkin görüntülemek için iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bellek pencereleri](/visualstudio/debugger/memory-windows)
