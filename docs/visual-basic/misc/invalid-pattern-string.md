---
title: "Geçersiz örnek dize"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="e4bfe-102">Geçersiz örnek dize</span><span class="sxs-lookup"><span data-stu-id="e4bfe-102">Invalid pattern string</span></span>
<span data-ttu-id="e4bfe-103">Belirtilen desen dizesi `Like` arama işlemi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="e4bfe-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e4bfe-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e4bfe-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="e4bfe-105">Liste ifadeler için geçerli karakterler gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e4bfe-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="e4bfe-106">Desen aralıktaki başlangıç aralığı karakteri son aralık karakteri değerinden olarak olduğundan emin olun `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="e4bfe-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="e4bfe-107">Desen aralığında değil olarak birbirine, birden çok kısa çizgi emin `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="e4bfe-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="e4bfe-108">Desen aralığı bir kapanış ayracı ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="e4bfe-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bfe-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4bfe-109">See Also</span></span>  
 [<span data-ttu-id="e4bfe-110">Like işleci</span><span class="sxs-lookup"><span data-stu-id="e4bfe-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
