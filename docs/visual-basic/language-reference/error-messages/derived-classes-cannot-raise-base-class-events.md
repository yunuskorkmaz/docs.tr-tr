---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 7b86420466d77a6aa45b1201a9375b4433e4b5ec
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163447"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029: türetilmiş sınıflar temel sınıf olayları oluşturamaz

Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir. Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.

 **Hata kimliği:** BC30029

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.

## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../statements/event-statement.md)
- [RaiseEvent Deyimi](../statements/raiseevent-statement.md)
