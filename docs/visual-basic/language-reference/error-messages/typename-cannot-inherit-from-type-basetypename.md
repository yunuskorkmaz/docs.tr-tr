---
title: "'<typename>', <type> temelinin erişimini derleme dışına genişlettiğinden <basetypename> '<type>' öğesinden devralamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402778"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename>', \<type> temelinin erişimini derleme dışına genişlettiğinden \<basetypename> '\<type>' öğesinden devralamaz
Bir sınıf veya arabirim, temel bir sınıftan veya arabirimden devralınır, ancak daha az kısıtlayıcı erişim düzeyine sahiptir.  
  
 Örneğin, bir `Public` arabirim bir arabirimden devralınır veya bir sınıf bir `Friend` `Protected` sınıftan devralınır `Private` . Bu, hedeflenen düzeyin ötesine erişmek için temel sınıfı veya arabirimi kullanıma sunar.  
  
 **Hata kimliği:** BC30910  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Türetilmiş sınıfın veya arabirimin erişim düzeyini, en az temel sınıf veya arabirim ile kısıtlayıcı olacak şekilde değiştirin.  
  
     -veya-  
  
- Daha az kısıtlayıcı erişim düzeyine ihtiyacınız varsa, `Inherits` ifadesini kaldırın. Daha kısıtlı bir temel sınıftan veya arabirimden devralma yapılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Class Deyimi](../statements/class-statement.md)
- [Interface Deyimi](../statements/interface-statement.md)
- [Inherits Deyimi](../statements/inherits-statement.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
