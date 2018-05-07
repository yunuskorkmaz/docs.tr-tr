---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Türetilmiş sınıflar temel sınıf olayları oluşturamaz
Bir olay, içinde bildirildiği yalnızca bildirim alanından yükseltilebilir. Bu nedenle, bir sınıfın başka bir sınıf, hatta bir onu türetildiği olaylarından yükseltemez.  
  
 **Hata Kimliği:** BC30029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta; bu nedenle deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
