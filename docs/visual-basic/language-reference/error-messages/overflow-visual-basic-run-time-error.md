---
title: Taşma (Visual Basic Çalışma Süresi Hatası)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594181"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="dca66-102">Taşma (Visual Basic Çalışma Süresi Hatası)</span><span class="sxs-lookup"><span data-stu-id="dca66-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="dca66-103">Atamanın hedef sınırlarını aşıyor atama çalıştığınızda taşma sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="dca66-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dca66-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dca66-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="dca66-105">Dönüşümler değişkenleri bu türde bir değer için izin verilen aralıktaki gösterilemeyecek kadar büyük olmayan ve bir türün bir değişkene değer atamak atamaları, hesaplama ve veri türü sonuçlarını daha büyük bir değer aralığı tutabilir emin olun , gerekirse.</span><span class="sxs-lookup"><span data-stu-id="dca66-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="dca66-106">Özelliklere atamalar yapılan özellik aralığını uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="dca66-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="dca66-107">Tamsayıları yüklenen hesaplamalarda kullanılan numaraları sonuçları tamsayılar büyük olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="dca66-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca66-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dca66-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="dca66-109">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="dca66-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="dca66-110">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="dca66-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
