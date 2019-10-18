---
title: .NET Core 'a taşıma araçları
description: .NET Core 'a bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 0478719617741946768cfe8e220a1dd402667998
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521341"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>.NET Core’a taşıma konusunda yardımcı olabilecek araçlar

Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:

- [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) - [Visual Studio uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) olarak bir [komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak, kodunuzun .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç zinciri.
- [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -farklı platformlarda API 'ler için C# olası uyumluluk risklerini tespit eden ve kullanım dışı API 'Leri çağrılarını algılayan bir Roslyn Çözümleyicisi.

Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracı Ile .NET Core proje dosyası biçiminde daha küçük çözümler veya ayrı projeler için bağlantı kurmayı deneyebilirsiniz.

> [!WARNING] 
> CsprojToVs2017, üçüncü taraf bir araçtır. Tüm projeleriniz için çalışacağından emin olmaz ve bağlı olduğunuz davranışta hafif değişikliklere neden olabilir. CsprojToVs2017, otomatikleştirilen temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanılmalıdır. Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.
