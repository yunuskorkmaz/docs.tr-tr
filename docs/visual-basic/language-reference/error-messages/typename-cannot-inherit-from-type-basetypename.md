---
title: "&#39; &lt;typename&gt;&#39; devralınmalıdır olamaz &lt;türü&gt; &#39;&lt; basetypename&gt;&#39; taban erişimini genişlettiğinden &lt;türü&gt; derleme dışına"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords: BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39; &lt;typename&gt;&#39; devralınmalıdır olamaz &lt;türü&gt; &#39;&lt; basetypename&gt;&#39; taban erişimini genişlettiğinden &lt;türü&gt; derleme dışına
Sınıfta veya arabirimde bir taban sınıftan veya arabirim ancak daha az kısıtlayıcı bir erişim düzeyi vardır.  
  
 Örneğin, bir `Public` arabirimi devralan bir `Friend` arabirimi, veya bir `Protected` sınıfı bir `Private` sınıfı. Bu, taban sınıf veya hedeflenen düzeyini aştığını erişmek için arabirim sunar.  
  
 **Hata Kimliği:** BC30910  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Türetilmiş sınıf veya en az olabildiğince kısıtlayıcı, temel sınıf veya arabirim arabirime erişim düzeyini değiştirin.  
  
     veya  
  
-   Daha az kısıtlayıcı erişim düzeyi gerekiyorsa kaldırma `Inherits` deyimi. Bir daha kısıtlı bir temel sınıf veya arabirim devralır olamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
