---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617273"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework sürümün .NET Framework sürümüyle eşleşmesi gerekir

#### <a name="details"></a>Ayrıntılar

Entity Framework (EF) sürümü .NET Framework sürümüyle eşleşmelidir. Entity Framework 5 .NET Framework 4,5 için önerilir. İçinde .NET Framework 4,5 projesinde EF 4. x ile ilgili bazı bilinen sorunlar vardır <xref:System.ComponentModel.DataAnnotations> . .NET Framework 4,5 ' de, bunlar farklı bir derlemeye taşınmıştır, bu nedenle hangi ek açıklamaların kullanılacağını belirleyen sorunlar var.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,5 için Entity Framework 5 sürümüne yükseltin

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |
