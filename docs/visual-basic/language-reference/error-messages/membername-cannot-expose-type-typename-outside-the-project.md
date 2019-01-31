---
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 03767501488a395073f925e27adea439751c0de6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265070"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="1423d-102">'\<membername >' türü gösteremez '\<typename >' aracılığıyla projenin dışına \<containertype > '\<containertypename >'</span><span class="sxs-lookup"><span data-stu-id="1423d-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="1423d-103">Bir değişken, yordam parametre veya dönüş işlevi kapsayıcısı dışında sunulur, ancak kapsayıcı dışında açılmamalıdır bir türü olarak bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="1423d-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="1423d-104">Aşağıdaki çatı kod bu hatayı oluşturan durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1423d-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="1423d-105">Bildirilen tür `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1423d-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="1423d-106">Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amacını boşa.</span><span class="sxs-lookup"><span data-stu-id="1423d-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="1423d-107">Önceki iskelet kodda `exposedVar` olduğu `Public` ve kullanılabilmesini `privateClass` , erişimi olmaması gereken kod için.</span><span class="sxs-lookup"><span data-stu-id="1423d-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="1423d-108">**Hata Kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="1423d-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1423d-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1423d-109">To correct this error</span></span>  
  
-   <span data-ttu-id="1423d-110">Değişken, yordam parametresi veya işlev erişim düzeyini değiştir en az olabildiğince kısıtlayıcı kendi veri türüne erişim düzeyini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1423d-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1423d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1423d-111">See also</span></span>
- [<span data-ttu-id="1423d-112">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="1423d-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
