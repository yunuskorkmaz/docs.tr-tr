---
title: Taşma (Visual Basic Çalışma Süresi Hatası)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387276"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="310c2-102">Taşma (Visual Basic Çalışma Süresi Hatası)</span><span class="sxs-lookup"><span data-stu-id="310c2-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="310c2-103">Atama hedefinin sınırlarını aşan bir atamaya çalıştığınızda bir taşma oluşur.</span><span class="sxs-lookup"><span data-stu-id="310c2-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="310c2-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="310c2-104">To correct this error</span></span>  
  
1. <span data-ttu-id="310c2-105">Atamalar, hesaplamalar ve veri türü dönüştürmelerinden oluşan sonuçların, bu tür değer için izin verilen değişkenlerin aralığında gösterilemeyecek kadar büyük olmadığından emin olun ve değeri, gerekirse daha büyük bir değer aralığını tutabilecek bir tür değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="310c2-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="310c2-106">Özelliklerin atamalarının, yaptıkları özelliğin aralığına uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="310c2-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="310c2-107">Tamsayılar üzerinde zorlanmakta olan hesaplamalarda kullanılan sayıların, tamsayılarla daha büyük sonuçlara sahip olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="310c2-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310c2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="310c2-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="310c2-109">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="310c2-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="310c2-110">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="310c2-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
