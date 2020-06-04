---
title: Geçersiz desenli dize
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402219"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="9707a-102">Geçersiz desenli dize</span><span class="sxs-lookup"><span data-stu-id="9707a-102">Invalid pattern string</span></span>
<span data-ttu-id="9707a-103">Bir aramanın işleminde belirtilen model dizesi `Like` geçersiz.</span><span class="sxs-lookup"><span data-stu-id="9707a-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9707a-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9707a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="9707a-105">Liste ifadeleri için geçerli karakterleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="9707a-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="9707a-106">Model aralığında, başlangıç aralığı karakterinin ' de olduğu gibi bitiş aralığı karakterinden küçük olduğundan emin olun `[a-z]` .</span><span class="sxs-lookup"><span data-stu-id="9707a-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="9707a-107">Model aralığında, içinde olduğu gibi birbirini izleyen birden çok tire olmadığından emin olun `[a--z]` .</span><span class="sxs-lookup"><span data-stu-id="9707a-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="9707a-108">Kapanış ayracı ile bitiş deseninin aralığı.</span><span class="sxs-lookup"><span data-stu-id="9707a-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9707a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9707a-109">See also</span></span>

- [<span data-ttu-id="9707a-110">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="9707a-110">Like Operator</span></span>](../language-reference/operators/like-operator.md)
