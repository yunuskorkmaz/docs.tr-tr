---
title: Deyim yöntem/çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: d5d756f1772b9519613e163119b88a3057d36cf3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870625"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="e7872-102">Deyim yöntem/çok satırlı lambda içinde geçerli değil</span><span class="sxs-lookup"><span data-stu-id="e7872-102">Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="e7872-103">İfade `Sub` ,, `Function` özellik `Get` veya özellik yordamı içinde geçerli değil `Set` .</span><span class="sxs-lookup"><span data-stu-id="e7872-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="e7872-104">Bazı deyimler modüle veya sınıf düzeyine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e7872-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="e7872-105">Diğer bir deyişle, gibi `Option Strict` diğer tüm bildirimlerin önünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7872-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="e7872-106">**Hata kimliği:** BC30024</span><span class="sxs-lookup"><span data-stu-id="e7872-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7872-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e7872-107">To correct this error</span></span>  
  
- <span data-ttu-id="e7872-108">İfadeyi yordamdan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e7872-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7872-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7872-109">See also</span></span>

- [<span data-ttu-id="e7872-110">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="e7872-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="e7872-111">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="e7872-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="e7872-112">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="e7872-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="e7872-113">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="e7872-113">Set Statement</span></span>](../statements/set-statement.md)
