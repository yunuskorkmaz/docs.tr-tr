---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803577"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Türetilmiş sınıflar temel sınıf olayları oluşturamaz
Bir olay, yalnızca içinde bildirildiği bildirim alanından yükseltilebilir. Bu nedenle, bir sınıf, olayları herhangi başka bir sınıftan, hatta bir türetilir oluşturamaz.  
  
 **Hata Kimliği:** BC30029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta şekilde deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
