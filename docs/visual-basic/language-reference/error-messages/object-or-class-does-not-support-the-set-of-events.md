---
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 4a6f1f59f43cdb351d49fbcbfd18362db888586e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593210"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Nesne veya sınıf olay kümesini desteklemiyor
Kullanmaya çalıştığınız bir `WithEvents` olayları belirtilen kümesi için bir olay kaynağı olarak çalışamaz bir bileşeni ile değişken. Örneğin, bir nesne olaylar indirilir, sonra başka bir nesne oluşturmak istediğiniz `Implements` ilk nesne. Uygulanan nesneden olayları havuzu düşünebilirsiniz karşın, bu her zaman durumda değil. `Implements` yalnızca yöntemleri ve özellikleri için bir arabirimi uygular. `WithEvents` Özel için desteklenmeyen `UserControls`, type Info yükseltmek gereken `ObjectEvent` çalışma zamanında kullanılabilir değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Olay kaynağı olmayan bir bileşen için olayları kapatamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
