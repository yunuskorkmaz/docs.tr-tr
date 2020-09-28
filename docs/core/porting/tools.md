---
title: .NET Core 'a taşıma araçları
description: .NET Core 'a bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: b8678ec72fe5d910d5f8cff4768106e7496f9276
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406134"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>.NET Core’a taşıma konusunda yardımcı olabilecek araçlar

Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:

- [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) -kodunuzun, .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç Zinciri:
  - [Komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak
  - [Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) olarak
- [Platform uyumluluğu Çözümleyicisi](../../standard/analyzers/platform-compat-analyzer.md) -geliştiricilere API 'nin kullanılamadığı bir çağrı sitemlerine ait platforma özel API 'ler kullandıklarında bildiren bir Roslyn Çözümleyicisi.
- [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -platformlar arası uygulamalarda ve kitaplıklarda platform uyumluluk sorunlarını algılamaya yardımcı olabilecek bir Roslyn Çözümleyicisi.
- [TRY-Convert](https://www.nuget.org/packages/try-convert/) -bir projeyi veya tüm çözümü .NET SDK 'sına dönüştürebileceğiniz bir .NET Core küresel Aracı, masaüstü uygulamalarını .NET Core 'a taşıma da dahil. Daha karmaşık bir yapıya sahipseniz (özel görevler, hedefler veya içeri aktarmalar gibi), .NET Core ile uyumlu olmayan birçok proje türünü reddederse, bu önerilmez.
