---
description: 'Hakkında daha fazla bilgi edinin: taşma (Visual Basic Run-Time hata)'
title: Taşma (Visual Basic Çalışma Süresi Hatası)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: a01a8916e09f9278dbdf6d594c5ef84d63b04c51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795462"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="676b6-103">Taşma (Visual Basic Çalışma Süresi Hatası)</span><span class="sxs-lookup"><span data-stu-id="676b6-103">Overflow (Visual Basic Run-Time Error)</span></span>

<span data-ttu-id="676b6-104">Atama hedefinin sınırlarını aşan bir atamaya çalıştığınızda bir taşma oluşur.</span><span class="sxs-lookup"><span data-stu-id="676b6-104">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="676b6-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="676b6-105">To correct this error</span></span>  
  
1. <span data-ttu-id="676b6-106">Atamalar, hesaplamalar ve veri türü dönüştürmelerinden oluşan sonuçların, bu tür değer için izin verilen değişkenlerin aralığında gösterilemeyecek kadar büyük olmadığından emin olun ve değeri, gerekirse daha büyük bir değer aralığını tutabilecek bir tür değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="676b6-106">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="676b6-107">Özelliklerin atamalarının, yaptıkları özelliğin aralığına uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="676b6-107">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="676b6-108">Tamsayılar üzerinde zorlanmakta olan hesaplamalarda kullanılan sayıların, tamsayılarla daha büyük sonuçlara sahip olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="676b6-108">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676b6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="676b6-109">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="676b6-110">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="676b6-110">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="676b6-111">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="676b6-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
