---
title: .NET Core'a taşıma araçları
description: .NET Core bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 64bad7600d8e17ada83d4bd8bc56762fd1789f43
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989135"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>.NET Core’a taşıma konusunda yardımcı olabilecek araçlar

Bu makalede listelenen araçları taşıma yaparken yararlı bulabilirsiniz:

- [.NET Taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) - Kodunuzu .NET Framework ve .NET Core arasında ne kadar taşınabilir olduğuna dair bir rapor oluşturabilen bir araç zinciri:
  - Komut [satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak
  - Visual [Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) olarak
- [.NET API çözümleyicisi](../../standard/analyzers/api-analyzer.md) - Farklı platformlarda C# API'leri için olası uyumluluk risklerini keşfeden ve amortismana alınan API'lere yönelik çağrıları algılayan bir Roslyn çözümleyicisi.

Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracıyla daha küçük çözümleri veya tek tek projeleri .NET Core proje dosya biçimine taşımayı deneyebilirsiniz.

> [!WARNING]
> CsprojToVs2017 üçüncü taraf bir araçtır. Tüm projeleriniz için çalışacağının garantisi yoktur ve bağlı olduğunuz davranışta ince değişikliklere neden olabilir. CsprojToVs2017, otomatikleştirilebilen temel şeyleri otomatikleştiren bir _başlangıç noktası_ olarak kullanılmalıdır. Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.
