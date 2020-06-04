---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409705"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Türetilmiş sınıflar temel sınıf olayları oluşturamaz
Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir. Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.  
  
 **Hata kimliği:** BC30029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../statements/event-statement.md)
- [RaiseEvent Deyimi](../statements/raiseevent-statement.md)
