---
title: Geçersiz desen dizesi
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 3fa42632ad6d69642d7b8ec36bf2880bc10a5024
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732485"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="6e430-102">Geçersiz desen dizesi</span><span class="sxs-lookup"><span data-stu-id="6e430-102">Invalid pattern string</span></span>
<span data-ttu-id="6e430-103">Belirtilen desen dizesi `Like` arama işlemi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="6e430-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e430-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6e430-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="6e430-105">Geçerli karakterler listesi ifadeler için gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="6e430-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="6e430-106">Desen aralığında başlangıç aralığı karakteri küçük Bitiş aralığı karakter olarak olduğundan emin olun `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="6e430-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="6e430-107">Desen aralığında değil olarak birden çok kısa çizgi, birbiriyle yanındaki emin olun `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="6e430-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="6e430-108">Bir köşeli ayraç aralıklarıyla deseni sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="6e430-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e430-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e430-109">See also</span></span>
- [<span data-ttu-id="6e430-110">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="6e430-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
