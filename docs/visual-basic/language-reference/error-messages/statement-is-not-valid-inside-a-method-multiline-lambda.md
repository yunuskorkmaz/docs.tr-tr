---
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159683"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="bedd2-102">BC30024: Ifade bir yöntem/çok satırlı lambda içinde geçerli değil</span><span class="sxs-lookup"><span data-stu-id="bedd2-102">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="bedd2-103">İfade `Sub` ,, `Function` özellik `Get` veya özellik yordamı içinde geçerli değil `Set` .</span><span class="sxs-lookup"><span data-stu-id="bedd2-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="bedd2-104">Bazı deyimler modüle veya sınıf düzeyine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bedd2-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="bedd2-105">Diğer bir deyişle, gibi `Option Strict` diğer tüm bildirimlerin önünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bedd2-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="bedd2-106">**Hata kimliği:** BC30024</span><span class="sxs-lookup"><span data-stu-id="bedd2-106">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bedd2-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bedd2-107">To correct this error</span></span>

- <span data-ttu-id="bedd2-108">İfadeyi yordamdan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="bedd2-108">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="bedd2-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bedd2-109">See also</span></span>

- [<span data-ttu-id="bedd2-110">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="bedd2-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="bedd2-111">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="bedd2-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="bedd2-112">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="bedd2-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="bedd2-113">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="bedd2-113">Set Statement</span></span>](../statements/set-statement.md)
