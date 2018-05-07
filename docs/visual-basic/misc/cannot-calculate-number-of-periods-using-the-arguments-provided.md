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
---
# <a name="cannot-calculate-number-of-periods-using-the-arguments-provided"></a>Sağlanan bağımsız değişkenler kullanılarak dönem sayısı hesaplayamıyor
Çağrı `NPer` işlevi tüm gerekli bağımsız değişkenleri içermiyor.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Emin `Rate`, `Prnt` ve `PV` değer işlev çağrısında dahil edilir.