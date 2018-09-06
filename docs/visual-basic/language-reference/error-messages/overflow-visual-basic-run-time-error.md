---
title: Taşma (Visual Basic Çalışma Süresi Hatası)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 7546676b85465577b357b7ad0757b4db8d40dbe3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863357"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="65a16-102">Taşma (Visual Basic Çalışma Süresi Hatası)</span><span class="sxs-lookup"><span data-stu-id="65a16-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="65a16-103">Atamanın hedef sınırlarını aşan bir atama denediğinizde bir taşma neden olur.</span><span class="sxs-lookup"><span data-stu-id="65a16-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65a16-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="65a16-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="65a16-105">Atamalar, hesaplamaları ve veri türü dönüşümleri değişkenlerinin değer türü için izin verilen aralıkta gösterilemeyecek kadar büyük değildir ve bir türden bir değişkene bir değer atamak sonuçları daha büyük bir değer aralığının tutabilir emin olun , gerekirse.</span><span class="sxs-lookup"><span data-stu-id="65a16-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="65a16-106">Özelliklere atamalar için yapılan özellik aralığı sığdığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="65a16-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="65a16-107">Tamsayıları zorlanır hesaplamalarda kullanılan numaraları sonuçları tamsayı büyük olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="65a16-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a16-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65a16-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="65a16-109">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="65a16-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="65a16-110">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="65a16-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
