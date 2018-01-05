---
title: "Sağlanan bağımsız değişkenler kullanılarak dönem sayısı hesaplayamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrFinancial_CannotCalculateNPer
ms.assetid: a96fed1c-73e6-4a2b-9906-0190bc3d4c3c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b915fec69e757cb9aa69a83b5c92c1af2988ac4
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="cannot-calculate-number-of-periods-using-the-arguments-provided"></a><span data-ttu-id="fdd17-102">Sağlanan bağımsız değişkenler kullanılarak dönem sayısı hesaplayamıyor</span><span class="sxs-lookup"><span data-stu-id="fdd17-102">Cannot calculate number of periods using the arguments provided</span></span>
<span data-ttu-id="fdd17-103">Çağrı `NPer` işlevi tüm gerekli bağımsız değişkenleri içermiyor.</span><span class="sxs-lookup"><span data-stu-id="fdd17-103">A call to the `NPer` function does not contain all of the required arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fdd17-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fdd17-104">To correct this error</span></span>  
  
-   <span data-ttu-id="fdd17-105">Emin `Rate`, `Prnt` ve `PV` değer işlev çağrısında dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fdd17-105">Ensure that the `Rate`, `Prnt` and `PV` values are included in the function call.</span></span>