---
title: '&#39;&lt;membername&gt; &#39; türünü gösteremez &#39; &lt;typename&gt; &#39; üzerinden proje dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588099"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="f5975-102">&#39;&lt;membername&gt; &#39; türünü gösteremez &#39; &lt;typename&gt; &#39; üzerinden proje dışına &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="f5975-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="f5975-103">Değişken, yordam parametresini veya işlev dönüş kapsayıcısı dışında gösterilir, ancak kapsayıcı dışında gösterilmeyen gerekir bir türü olarak bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f5975-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="f5975-104">Aşağıdaki iskelet kod bu hatayı oluşturan bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5975-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="f5975-105">Bildirilmiş bir türü `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f5975-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="f5975-106">Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amaçla boşa.</span><span class="sxs-lookup"><span data-stu-id="f5975-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="f5975-107">Önceki iskelet kodda, `exposedVar` olan `Public` ve kullanılabilmesini `privateClass` erişimi olmaması gereken kodu.</span><span class="sxs-lookup"><span data-stu-id="f5975-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="f5975-108">**Hata Kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="f5975-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5975-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f5975-109">To correct this error</span></span>  
  
-   <span data-ttu-id="f5975-110">Değiştirme değişkeni, yordam parametresini ya da işlevin erişim düzeyi en az olabildiğince kısıtlayıcı, veri türü erişim düzeyi dönün.</span><span class="sxs-lookup"><span data-stu-id="f5975-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5975-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5975-111">See Also</span></span>  
 [<span data-ttu-id="f5975-112">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f5975-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
