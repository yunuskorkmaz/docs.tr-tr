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
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="c315e-103">.NET Core’a taşıma konusunda yardımcı olabilecek araçlar</span><span class="sxs-lookup"><span data-stu-id="c315e-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="c315e-104">Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c315e-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="c315e-105">[.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) -kodunuzun, .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç Zinciri:</span><span class="sxs-lookup"><span data-stu-id="c315e-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="c315e-106">[Komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak</span><span class="sxs-lookup"><span data-stu-id="c315e-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="c315e-107">[Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) olarak</span><span class="sxs-lookup"><span data-stu-id="c315e-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="c315e-108">[.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -farklı platformlarda C# API 'leri için olası uyumluluk risklerini tespit eden ve kullanım dışı API 'leri çağrılarını algılayan bir Roslyn Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c315e-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>
- <span data-ttu-id="c315e-109">[TRY-Convert](https://www.nuget.org/packages/try-convert/) -bir projeyi veya tüm çözümü .NET SDK 'sına dönüştürebileceğiniz bir .NET Core küresel Aracı, masaüstü uygulamalarını .NET Core 'a taşıma da dahil.</span><span class="sxs-lookup"><span data-stu-id="c315e-109">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="c315e-110">Daha karmaşık bir yapıya sahipseniz (özel görevler, hedefler veya içeri aktarmalar gibi), .NET Core ile uyumlu olmayan birçok proje türünü reddederse, bu önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c315e-110">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
