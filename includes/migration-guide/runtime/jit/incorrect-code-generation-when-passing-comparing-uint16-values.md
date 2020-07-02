---
ms.openlocfilehash: c20d5fb3d700ba7649e423a79e4598b327c50a00
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622271"
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
