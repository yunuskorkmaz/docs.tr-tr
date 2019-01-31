---
title: "'<typename>', <type> temelinin erişimini derleme dışına genişlettiğinden <basetypename> '<type>' öğesinden devralamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 226c85f887ecc706a5cb554c2163742f10896141
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269828"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename >' öğesinden devralamaz \<türü > '\<basetypename >' temelinin erişimini genişlettiğinden \<türü > derleme dışından
Bir sınıf veya arabirim bir temel sınıftan devraldığı veya arabirimi ancak daha az kısıtlayıcı bir erişim düzeyi yok.  
  
 Örneğin, bir `Public` arabirim sınıfından devralan bir `Friend` arabirimi veya `Protected` sınıfının devraldığı bir `Private` sınıfı. Bu, temel sınıf veya hedeflenen düzeyinin ötesinde erişmek için bir arabirimi kullanıma sunar.  
  
 **Hata Kimliği:** BC30910  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Türetilmiş bir sınıf veya arabirim en az olabildiğince kısıtlayıcı, temel sınıf veya arabirim erişim düzeyini değiştirin.  
  
     -veya-  
  
-   Daha az kısıtlayıcı erişim düzeyi gerekiyorsa, kaldırma `Inherits` deyimi. Bir daha kısıtlı bir temel sınıfı veya arabirimi devralınamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
