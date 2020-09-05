---
ms.openlocfilehash: 018c99d60dc8926cae2682dc9c035e25fba711e5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497075"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>UInt16 değerlerini geçirirken ve karşılaştırırken yanlış kod oluşturma

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' de tanıtılan değişiklikler nedeniyle, bazı durumlarda, .NET Framework 4,7 üzerinde çalışan uygulamalarda JıT derleyicisi tarafından oluşturulan kod, yanlış bir şekilde iki <code>T:System.UInt16</code> değeri karşılaştırır. Daha fazla bilgi için bkz. [sorun #11508: ushort args GitHub.com üzerinde geçirilirken ve karşılaştırılırken sessiz hatalı CodeGen](https://github.com/dotnet/coreclr/issues/11508) .

#### <a name="suggestion"></a>Öneri

.NET Framework 4,7 ' de 16 bit işaretsiz değerlerin karşılaştırılmasının sorun yaşarsanız .NET Framework 4.7.1 yükseltin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
