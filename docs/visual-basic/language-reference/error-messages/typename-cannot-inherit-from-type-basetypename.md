---
title: '&#39;&lt;TypeName&gt; &#39; devralamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; temelinin erişimini genişlettiğinden &lt;türü&gt; derleme dışından'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556489"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;TypeName&gt; &#39; devralamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; temelinin erişimini genişlettiğinden &lt;türü&gt; derleme dışından
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
