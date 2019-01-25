---
title: '&#39;&lt;membername&gt; &#39; türü gösteremez &#39; &lt;typename&gt; &#39; aracılığıyla projenin dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672350"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="4e1e7-102">&#39;&lt;membername&gt; &#39; türü gösteremez &#39; &lt;typename&gt; &#39; aracılığıyla projenin dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="4e1e7-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="4e1e7-103">Bir değişken, yordam parametre veya dönüş işlevi kapsayıcısı dışında sunulur, ancak kapsayıcı dışında açılmamalıdır bir türü olarak bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="4e1e7-104">Aşağıdaki çatı kod bu hatayı oluşturan durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="4e1e7-105">Bildirilen tür `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="4e1e7-106">Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amacını boşa.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="4e1e7-107">Önceki iskelet kodda `exposedVar` olduğu `Public` ve kullanılabilmesini `privateClass` , erişimi olmaması gereken kod için.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="4e1e7-108">**Hata Kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="4e1e7-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4e1e7-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4e1e7-109">To correct this error</span></span>  
  
-   <span data-ttu-id="4e1e7-110">Değişken, yordam parametresi veya işlev erişim düzeyini değiştir en az olabildiğince kısıtlayıcı kendi veri türüne erişim düzeyini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e1e7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-111">See also</span></span>
- [<span data-ttu-id="4e1e7-112">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="4e1e7-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
