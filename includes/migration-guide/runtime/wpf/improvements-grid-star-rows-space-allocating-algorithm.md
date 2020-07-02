---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622093"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Kılavuz yıldıza yönelik iyileştirmeler-satırlar alan ayırma algoritması

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' de tanıtılan bir hata, [boyutları ayırma algoritmasında](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)düzeltildi) <xref:System.Windows.Controls.Grid> .  Boş satırlar içeren bir ızgara gibi bazı durumlarda, <code>Height=&quot;Auto&quot;</code> satırlar yanlış konuma düzenleniyordu, muhtemelen ızgara dışında.

#### <a name="suggestion"></a>Öneri

Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4,8 veya sonraki bir sürümde çalışmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|
