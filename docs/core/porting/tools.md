---
title: .NET Core 'a taşıma araçları
description: .NET Core 'a bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795592"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>.NET Core’a taşıma konusunda yardımcı olabilecek araçlar

Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:

- [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) -kodunuzun, .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç Zinciri:
  - [Komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak
  - [Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) olarak
- [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -farklı platformlarda C# API 'leri için olası uyumluluk risklerini tespit eden ve kullanım dışı API 'leri çağrılarını algılayan bir Roslyn Çözümleyicisi.
- [TRY-Convert](https://www.nuget.org/packages/try-convert/) -bir projeyi veya tüm çözümü .NET SDK 'sına dönüştürebileceğiniz bir .NET Core küresel Aracı, masaüstü uygulamalarını .NET Core 'a taşıma da dahil. Daha karmaşık bir yapıya sahipseniz (özel görevler, hedefler veya içeri aktarmalar gibi), .NET Core ile uyumlu olmayan birçok proje türünü reddederse, bu önerilmez.
