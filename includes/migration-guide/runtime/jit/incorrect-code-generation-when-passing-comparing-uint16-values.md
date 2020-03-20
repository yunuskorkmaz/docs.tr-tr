---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802542"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>UInt16 değerlerini aktarırken ve karşılaştırırken yanlış kod oluşturma

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7'de yapılan değişiklikler nedeniyle, bazı durumlarda .NET Framework 4.7 üzerinde çalışan uygulamalarda JIT derleyicisi tarafından oluşturulan kod iki <code>T:System.UInt16</code> değeri yanlış karşılaştırır. Daha fazla bilgi için, [bkz: #11508 Sorun: GitHub.com ushort args geçerken ve karşılaştırırken sessiz kötü codegen.](https://github.com/dotnet/coreclr/issues/11508)|
|Öneri|.NET Framework 4.7'deki 16 bit imzasız değerlerin karşılaştırılmasında sorunlarla karşılaşırsanız,.NET Framework 4.7.1'e yükseltin.|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Çalışma Zamanı|
