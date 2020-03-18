---
title: .NET Core'a taşıma araçları
description: .NET Core bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157524"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>.NET Core’a taşıma konusunda yardımcı olabilecek araçlar

Bu makalede listelenen araçları taşıma yaparken yararlı bulabilirsiniz:

- [.NET Taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) - Kodunuzu .NET Framework ve .NET Core arasında ne kadar taşınabilir olduğuna dair bir rapor oluşturabilen bir araç zinciri:
  - Komut [satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak
  - Visual [Studio uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) olarak
- [.NET API çözümleyicisi](../../standard/analyzers/api-analyzer.md) - Farklı platformlarda C# API'leri için olası uyumluluk risklerini keşfeden ve amortismana alınan API'lere yönelik çağrıları algılayan bir Roslyn çözümleyicisi.

Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracıyla daha küçük çözümleri veya tek tek projeleri .NET Core proje dosya biçimine taşımayı deneyebilirsiniz.

> [!WARNING]
> CsprojToVs2017 üçüncü taraf bir araçtır. Tüm projeleriniz için çalışacağının garantisi yoktur ve bağlı olduğunuz davranışta ince değişikliklere neden olabilir. CsprojToVs2017, otomatikleştirilebilen temel şeyleri otomatikleştiren bir _başlangıç noktası_ olarak kullanılmalıdır. Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.
