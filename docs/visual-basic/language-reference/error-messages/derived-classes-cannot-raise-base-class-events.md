---
description: 'Hakkında daha fazla bilgi edinin: BC30029: türetilmiş sınıflar temel sınıf olayları oluşturamaz'
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 68546f2654f7c34fcb309d5af68e237d5f1eac79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796606"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029: türetilmiş sınıflar temel sınıf olayları oluşturamaz

Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir. Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.

 **Hata kimliği:** BC30029

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.

## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../statements/event-statement.md)
- [RaiseEvent Deyimi](../statements/raiseevent-statement.md)
