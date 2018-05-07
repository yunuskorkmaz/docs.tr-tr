---
title: '&#39;&lt;TypeName&gt; &#39; devralınmalıdır olamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; taban erişimini genişlettiğinden &lt;türü&gt; derleme dışına'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;TypeName&gt; &#39; devralınmalıdır olamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; taban erişimini genişlettiğinden &lt;türü&gt; derleme dışına
Sınıfta veya arabirimde bir taban sınıftan veya arabirim ancak daha az kısıtlayıcı bir erişim düzeyi vardır.  
  
 Örneğin, bir `Public` arabirimi devralan bir `Friend` arabirimi, veya bir `Protected` sınıfı bir `Private` sınıfı. Bu, taban sınıf veya hedeflenen düzeyini aştığını erişmek için arabirim sunar.  
  
 **Hata Kimliği:** BC30910  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Türetilmiş sınıf veya en az olabildiğince kısıtlayıcı, temel sınıf veya arabirim arabirime erişim düzeyini değiştirin.  
  
     -veya-  
  
-   Daha az kısıtlayıcı erişim düzeyi gerekiyorsa kaldırma `Inherits` deyimi. Bir daha kısıtlı bir temel sınıf veya arabirim devralır olamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
