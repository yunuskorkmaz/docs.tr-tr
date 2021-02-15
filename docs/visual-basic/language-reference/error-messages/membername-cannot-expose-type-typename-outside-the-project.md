---
description: "Hakkında daha fazla bilgi: BC30909: ' <membername> ', ' ' türünü <typename> proje dışında <containertype> ' ' üzerinden <containertypename> gösteremez"
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 8acff03c80316e0f2aa4157ea9cce399c2e6975d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470999"
---
# <a name="bc30909-membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="d0f84-103">BC30909: ' ', ' ' \<membername> türünü \<typename> proje dışında ' ' üzerinden \<containertype> gösteremez \<containertypename></span><span class="sxs-lookup"><span data-stu-id="d0f84-103">BC30909: '\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>

<span data-ttu-id="d0f84-104">Bir değişken, yordam parametresi veya işlev dönüşü kapsayıcının dışında sunulur, ancak kapsayıcı dışında gösterilmemesi gereken bir tür olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0f84-104">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>

 <span data-ttu-id="d0f84-105">Aşağıdaki iskelet kodu, bu hatayı üreten bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0f84-105">The following skeleton code shows a situation that generates this error.</span></span>

```vb
Private Class privateClass
End Class
Public Class mainClass
    Public exposedVar As New privateClass
End Class
```

 <span data-ttu-id="d0f84-106">,, Veya olarak belirtilen bir türün `Protected` , `Friend` `Protected Friend` `Private` Bildirim bağlamı dışında sınırlı erişimi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0f84-106">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="d0f84-107">Bunu daha az kısıtlanmış erişimi olan bir değişkenin veri türü olarak kullanmak, bu amacı erteçine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d0f84-107">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="d0f84-108">Önceki iskelet kodunda, `exposedVar` `Public` ve `privateClass` erişimine sahip olmaması gereken kodla kullanıma sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="d0f84-108">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>

 <span data-ttu-id="d0f84-109">**Hata kimliği:** BC30909</span><span class="sxs-lookup"><span data-stu-id="d0f84-109">**Error ID:** BC30909</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d0f84-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d0f84-110">To correct this error</span></span>

- <span data-ttu-id="d0f84-111">Değişkenin, yordam parametresinin veya işlevin erişim düzeyini, veri türünün erişim düzeyi olarak en az kısıtlayıcı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0f84-111">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f84-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0f84-112">See also</span></span>

- [<span data-ttu-id="d0f84-113">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="d0f84-113">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
