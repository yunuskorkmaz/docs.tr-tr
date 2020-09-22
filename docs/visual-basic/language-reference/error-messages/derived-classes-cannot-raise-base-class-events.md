---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0233a1584c5e871506b5c4762e98874c343f19b8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874483"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Türetilmiş sınıflar temel sınıf olayları oluşturamaz

Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir. Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.  
  
 **Hata kimliği:** BC30029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../statements/event-statement.md)
- [RaiseEvent Deyimi](../statements/raiseevent-statement.md)
