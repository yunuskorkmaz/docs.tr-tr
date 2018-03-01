---
title: "Taşma (Visual Basic Çalışma Süresi Hatası)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="3ee99-102">Taşma (Visual Basic Çalışma Süresi Hatası)</span><span class="sxs-lookup"><span data-stu-id="3ee99-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="3ee99-103">Atamanın hedef sınırlarını aşıyor atama çalıştığınızda taşma sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3ee99-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3ee99-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3ee99-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="3ee99-105">Dönüşümler değişkenleri bu türde bir değer için izin verilen aralıktaki gösterilemeyecek kadar büyük olmayan ve bir türün bir değişkene değer atamak atamaları, hesaplama ve veri türü sonuçlarını daha büyük bir değer aralığı tutabilir emin olun , gerekirse.</span><span class="sxs-lookup"><span data-stu-id="3ee99-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="3ee99-106">Özelliklere atamalar yapılan özellik aralığını uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3ee99-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="3ee99-107">Tamsayıları yüklenen hesaplamalarda kullanılan numaraları sonuçları tamsayılar büyük olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="3ee99-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee99-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ee99-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="3ee99-109">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="3ee99-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="3ee99-110">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="3ee99-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
