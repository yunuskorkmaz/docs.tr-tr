---
description: 'Hakkında daha fazla bilgi edinin: BC30024: deyimde yöntem/çok satırlı lambda içinde geçerli değil'
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: c70e5563ab8c161966cd9790ae1f192fa5d50b17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731181"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="8116b-103">BC30024: Ifade bir yöntem/çok satırlı lambda içinde geçerli değil</span><span class="sxs-lookup"><span data-stu-id="8116b-103">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="8116b-104">İfade `Sub` ,, `Function` özellik `Get` veya özellik yordamı içinde geçerli değil `Set` .</span><span class="sxs-lookup"><span data-stu-id="8116b-104">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="8116b-105">Bazı deyimler modüle veya sınıf düzeyine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8116b-105">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="8116b-106">Diğer bir deyişle, gibi `Option Strict` diğer tüm bildirimlerin önünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8116b-106">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="8116b-107">**Hata kimliği:** BC30024</span><span class="sxs-lookup"><span data-stu-id="8116b-107">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8116b-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8116b-108">To correct this error</span></span>

- <span data-ttu-id="8116b-109">İfadeyi yordamdan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8116b-109">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="8116b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8116b-110">See also</span></span>

- [<span data-ttu-id="8116b-111">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="8116b-111">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="8116b-112">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="8116b-112">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="8116b-113">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="8116b-113">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="8116b-114">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="8116b-114">Set Statement</span></span>](../statements/set-statement.md)
