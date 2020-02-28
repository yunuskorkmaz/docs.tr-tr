---
title: .NET Core 'a taşıma araçları
description: .NET Core 'a bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157524"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>.NET Core’a taşıma konusunda yardımcı olabilecek araçlar

Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:

- [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) -kodunuzun, .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç Zinciri:
  - [Komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak
  - [Visual Studio uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) olarak
- [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -farklı platformlarda API 'ler için C# olası uyumluluk risklerini tespit eden ve kullanım dışı API 'Leri çağrılarını algılayan bir Roslyn Çözümleyicisi.

Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracı Ile .NET Core proje dosyası biçiminde daha küçük çözümler veya ayrı projeler için bağlantı kurmayı deneyebilirsiniz.

> [!WARNING]
> CsprojToVs2017, üçüncü taraf bir araçtır. Tüm projeleriniz için çalışacağından emin olmaz ve bağlı olduğunuz davranışta hafif değişikliklere neden olabilir. CsprojToVs2017, otomatikleştirilen temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanılmalıdır. Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.
