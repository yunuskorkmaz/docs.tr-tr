---
title: Geçersiz desen dizesi
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: bc2e91060ca1b0e21ea28b0f08febc3e0c54f4f1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027311"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="564f5-102">Geçersiz desen dizesi</span><span class="sxs-lookup"><span data-stu-id="564f5-102">Invalid pattern string</span></span>
<span data-ttu-id="564f5-103">Belirtilen desen dizesi `Like` arama işlemi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="564f5-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="564f5-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="564f5-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="564f5-105">Geçerli karakterler listesi ifadeler için gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="564f5-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="564f5-106">Desen aralığında başlangıç aralığı karakteri küçük Bitiş aralığı karakter olarak olduğundan emin olun `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="564f5-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="564f5-107">Desen aralığında değil olarak birden çok kısa çizgi, birbiriyle yanındaki emin olun `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="564f5-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="564f5-108">Bir köşeli ayraç aralıklarıyla deseni sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="564f5-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="564f5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="564f5-109">See also</span></span>

- [<span data-ttu-id="564f5-110">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="564f5-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
