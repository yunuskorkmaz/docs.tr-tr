---
title: "&#39; &lt;membername&gt;&#39; türündeki &#39; gösteremez&lt; TypeName&gt;&#39; üzerinden proje dışına &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="5f9ec-102">&#39; &lt;membername&gt;&#39; türündeki &#39; gösteremez&lt; TypeName&gt;&#39; üzerinden proje dışına &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="5f9ec-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="5f9ec-103">Değişken, yordam parametresini veya işlev dönüş kapsayıcısı dışında gösterilir, ancak kapsayıcı dışında gösterilmeyen gerekir bir türü olarak bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="5f9ec-104">Aşağıdaki iskelet kod bu hatayı oluşturan bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="5f9ec-105">Bildirilmiş bir türü `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="5f9ec-106">Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amaçla boşa.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="5f9ec-107">Önceki iskelet kodda, `exposedVar` olan `Public` ve kullanılabilmesini `privateClass` erişimi olmaması gereken kodu.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="5f9ec-108">**Hata Kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="5f9ec-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f9ec-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5f9ec-109">To correct this error</span></span>  
  
-   <span data-ttu-id="5f9ec-110">Değiştirme değişkeni, yordam parametresini ya da işlevin erişim düzeyi en az olabildiğince kısıtlayıcı, veri türü erişim düzeyi dönün.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9ec-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f9ec-111">See Also</span></span>  
 [<span data-ttu-id="5f9ec-112">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="5f9ec-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
