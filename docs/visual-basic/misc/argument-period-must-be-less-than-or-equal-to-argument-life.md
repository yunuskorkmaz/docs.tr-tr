---
description: "Hakkında daha fazla bilgi: ' period ' bağımsız değişkeni, ' Life ' bağımsız değişkenine eşit veya ondan küçük olmalıdır"
title: "' Period ' bağımsız değişkeni, ' Life ' bağımsız değişkenine eşit veya ondan küçük olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 451defc2e9015b12bd6b340c3c32782ea4d4774f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100458635"
---
# <a name="argument-period-must-be-less-than-or-equal-to-argument-life"></a><span data-ttu-id="216ab-103">' Period ' bağımsız değişkeni, ' Life ' bağımsız değişkenine eşit veya ondan küçük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="216ab-103">Argument 'Period' must be less than or equal to argument 'Life'</span></span>

<span data-ttu-id="216ab-104">`Period`Varlık amortismanının hesaplandığı dönemi belirten bağımsız değişkenin değeri, `Life` bağımsız değişkenin değerinden büyüktür.</span><span class="sxs-lookup"><span data-stu-id="216ab-104">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="216ab-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="216ab-105">To correct this error</span></span>  
  
- <span data-ttu-id="216ab-106">`Life`Ve `Period` bağımsız değişkenlerinin aynı birimlerde belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="216ab-106">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="216ab-107">Örneğin, `Life` ay cinsinden ölçüldüğünde `Period` de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="216ab-107">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216ab-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="216ab-108">See also</span></span>

- [<span data-ttu-id="216ab-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="216ab-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
