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
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="9c56e-103">.NET Core’a taşıma konusunda yardımcı olabilecek araçlar</span><span class="sxs-lookup"><span data-stu-id="9c56e-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="9c56e-104">Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9c56e-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="9c56e-105">[.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) -kodunuzun, .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç Zinciri:</span><span class="sxs-lookup"><span data-stu-id="9c56e-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="9c56e-106">[Komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak</span><span class="sxs-lookup"><span data-stu-id="9c56e-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="9c56e-107">[Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) olarak</span><span class="sxs-lookup"><span data-stu-id="9c56e-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="9c56e-108">[Platform uyumluluğu Çözümleyicisi](../../standard/analyzers/platform-compat-analyzer.md) -geliştiricilere API 'nin kullanılamadığı bir çağrı sitemlerine ait platforma özel API 'ler kullandıklarında bildiren bir Roslyn Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9c56e-108">[Platform compatibility analyzer](../../standard/analyzers/platform-compat-analyzer.md) - A Roslyn analyzer that informs developers when they use platform-specific APIs from call sites where the API might not be available.</span></span>
- <span data-ttu-id="9c56e-109">[.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -platformlar arası uygulamalarda ve kitaplıklarda platform uyumluluk sorunlarını algılamaya yardımcı olabilecek bir Roslyn Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9c56e-109">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that can help detect platform compatibility issues in cross-platform apps and libraries.</span></span>
- <span data-ttu-id="9c56e-110">[TRY-Convert](https://www.nuget.org/packages/try-convert/) -bir projeyi veya tüm çözümü .NET SDK 'sına dönüştürebileceğiniz bir .NET Core küresel Aracı, masaüstü uygulamalarını .NET Core 'a taşıma da dahil.</span><span class="sxs-lookup"><span data-stu-id="9c56e-110">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="9c56e-111">Daha karmaşık bir yapıya sahipseniz (özel görevler, hedefler veya içeri aktarmalar gibi), .NET Core ile uyumlu olmayan birçok proje türünü reddederse, bu önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9c56e-111">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
