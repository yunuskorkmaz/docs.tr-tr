---
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 31d44c93d62163df4d81cb8503b633f0eb317372
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873815"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="88625-102">'\<membername>', '\<typename>' türünü proje dışında \<containertype> '\<containertypename>' üzerinden gösteremez</span><span class="sxs-lookup"><span data-stu-id="88625-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>

<span data-ttu-id="88625-103">Bir değişken, yordam parametresi veya işlev dönüşü kapsayıcının dışında sunulur, ancak kapsayıcı dışında gösterilmemesi gereken bir tür olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="88625-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="88625-104">Aşağıdaki iskelet kodu, bu hatayı üreten bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="88625-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="88625-105">,, Veya olarak belirtilen bir türün `Protected` , `Friend` `Protected Friend` `Private` Bildirim bağlamı dışında sınırlı erişimi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="88625-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="88625-106">Bunu daha az kısıtlanmış erişimi olan bir değişkenin veri türü olarak kullanmak, bu amacı erteçine neden olur.</span><span class="sxs-lookup"><span data-stu-id="88625-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="88625-107">Önceki iskelet kodunda, `exposedVar` `Public` ve `privateClass` erişimine sahip olmaması gereken kodla kullanıma sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="88625-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="88625-108">**Hata kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="88625-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88625-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="88625-109">To correct this error</span></span>  
  
- <span data-ttu-id="88625-110">Değişkenin, yordam parametresinin veya işlevin erişim düzeyini, veri türünün erişim düzeyi olarak en az kısıtlayıcı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="88625-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88625-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88625-111">See also</span></span>

- [<span data-ttu-id="88625-112">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="88625-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
