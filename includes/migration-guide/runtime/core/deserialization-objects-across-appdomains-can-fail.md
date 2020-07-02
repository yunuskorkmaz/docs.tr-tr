---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620561"
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
