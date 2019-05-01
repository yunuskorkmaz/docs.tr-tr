---
title: Sağlanan bağımsız değişkenler kullanarak dönem sayısı hesaplayamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_CannotCalculateNPer
ms.assetid: a96fed1c-73e6-4a2b-9906-0190bc3d4c3c
ms.openlocfilehash: a88837d198091f9f8d11dd90656534588c2f0550
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051071"
---
# <a name="cannot-calculate-number-of-periods-using-the-arguments-provided"></a><span data-ttu-id="47555-102">Sağlanan bağımsız değişkenler kullanarak dönem sayısı hesaplayamıyor</span><span class="sxs-lookup"><span data-stu-id="47555-102">Cannot calculate number of periods using the arguments provided</span></span>
<span data-ttu-id="47555-103">Bir çağrı `NPer` işlevi tüm bağımsız değişkenlerini içermez.</span><span class="sxs-lookup"><span data-stu-id="47555-103">A call to the `NPer` function does not contain all of the required arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47555-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="47555-104">To correct this error</span></span>  
  
- <span data-ttu-id="47555-105">Emin `Rate`, `Prnt` ve `PV` değer işlev çağrısında dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="47555-105">Ensure that the `Rate`, `Prnt` and `PV` values are included in the function call.</span></span>