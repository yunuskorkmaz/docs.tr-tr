---
title: Sağlanan bağımsız değişkenler kullanılarak dönem sayısı hesaplayamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_CannotCalculateNPer
ms.assetid: a96fed1c-73e6-4a2b-9906-0190bc3d4c3c
ms.openlocfilehash: a88837d198091f9f8d11dd90656534588c2f0550
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33633126"
---
# <a name="cannot-calculate-number-of-periods-using-the-arguments-provided"></a><span data-ttu-id="e12f9-102">Sağlanan bağımsız değişkenler kullanılarak dönem sayısı hesaplayamıyor</span><span class="sxs-lookup"><span data-stu-id="e12f9-102">Cannot calculate number of periods using the arguments provided</span></span>
<span data-ttu-id="e12f9-103">Çağrı `NPer` işlevi tüm gerekli bağımsız değişkenleri içermiyor.</span><span class="sxs-lookup"><span data-stu-id="e12f9-103">A call to the `NPer` function does not contain all of the required arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e12f9-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e12f9-104">To correct this error</span></span>  
  
-   <span data-ttu-id="e12f9-105">Emin `Rate`, `Prnt` ve `PV` değer işlev çağrısında dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e12f9-105">Ensure that the `Rate`, `Prnt` and `PV` values are included in the function call.</span></span>