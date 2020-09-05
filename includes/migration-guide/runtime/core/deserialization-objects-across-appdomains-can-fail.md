---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497718"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>AppDomain 'lerde nesnelerin serisini kaldırma başarısız olabilir

#### <a name="details"></a>Ayrıntılar

Bazı durumlarda, bir uygulama farklı uygulama temellerine sahip iki veya daha fazla uygulama etki alanı kullandığında, uygulama etki alanlarında mantıksal çağrı bağlamındaki nesnelerin serisini kaldırma girişimi bir özel durum oluşturur.

#### <a name="suggestion"></a>Öneri

Bkz [. azaltma: uygulama etki alanları arasında nesnelerin serisini kaldırma](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
