---
description: 'Hakkında daha fazla bilgi edinin: geçersiz desenli dize'
title: Geçersiz desenli dize
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4fbf16dd43ac4ae44e1a99d85caae4a7baf99109
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462067"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="74620-103">Geçersiz desenli dize</span><span class="sxs-lookup"><span data-stu-id="74620-103">Invalid pattern string</span></span>

<span data-ttu-id="74620-104">Bir aramanın işleminde belirtilen model dizesi `Like` geçersiz.</span><span class="sxs-lookup"><span data-stu-id="74620-104">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74620-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="74620-105">To correct this error</span></span>  
  
1. <span data-ttu-id="74620-106">Liste ifadeleri için geçerli karakterleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="74620-106">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="74620-107">Model aralığında, başlangıç aralığı karakterinin ' de olduğu gibi bitiş aralığı karakterinden küçük olduğundan emin olun `[a-z]` .</span><span class="sxs-lookup"><span data-stu-id="74620-107">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="74620-108">Model aralığında, içinde olduğu gibi birbirini izleyen birden çok tire olmadığından emin olun `[a--z]` .</span><span class="sxs-lookup"><span data-stu-id="74620-108">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="74620-109">Kapanış ayracı ile bitiş deseninin aralığı.</span><span class="sxs-lookup"><span data-stu-id="74620-109">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74620-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74620-110">See also</span></span>

- [<span data-ttu-id="74620-111">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="74620-111">Like Operator</span></span>](../language-reference/operators/like-operator.md)
