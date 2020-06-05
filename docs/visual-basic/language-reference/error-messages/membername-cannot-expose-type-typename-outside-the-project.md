---
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397291"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="89c3d-102">'\<membername>', '\<typename>' türünü proje dışında \<containertype> '\<containertypename>' üzerinden gösteremez</span><span class="sxs-lookup"><span data-stu-id="89c3d-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="89c3d-103">Bir değişken, yordam parametresi veya işlev dönüşü kapsayıcının dışında sunulur, ancak kapsayıcı dışında gösterilmemesi gereken bir tür olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="89c3d-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="89c3d-104">Aşağıdaki iskelet kodu, bu hatayı üreten bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="89c3d-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="89c3d-105">,, Veya olarak belirtilen bir türün `Protected` , `Friend` `Protected Friend` `Private` Bildirim bağlamı dışında sınırlı erişimi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89c3d-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="89c3d-106">Bunu daha az kısıtlanmış erişimi olan bir değişkenin veri türü olarak kullanmak, bu amacı erteçine neden olur.</span><span class="sxs-lookup"><span data-stu-id="89c3d-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="89c3d-107">Önceki iskelet kodunda, `exposedVar` `Public` ve `privateClass` erişimine sahip olmaması gereken kodla kullanıma sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="89c3d-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="89c3d-108">**Hata kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="89c3d-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89c3d-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="89c3d-109">To correct this error</span></span>  
  
- <span data-ttu-id="89c3d-110">Değişkenin, yordam parametresinin veya işlevin erişim düzeyini, veri türünün erişim düzeyi olarak en az kısıtlayıcı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="89c3d-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c3d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89c3d-111">See also</span></span>

- [<span data-ttu-id="89c3d-112">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="89c3d-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
