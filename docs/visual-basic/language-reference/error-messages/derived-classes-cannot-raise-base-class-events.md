---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 030c9c2ffa97572298b23f05c23e3af0df7387b0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913168"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Türetilmiş sınıflar temel sınıf olayları oluşturamaz
Bir olay, yalnızca içinde bildirildiği bildirim alanından yükseltilebilir. Bu nedenle, bir sınıf, olayları herhangi başka bir sınıftan, hatta bir türetilir oluşturamaz.  
  
 **Hata Kimliği:** BC30029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta şekilde deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
