---
title: .NET Core 'a taşıma araçları
description: .NET Core 'a bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 101a110dec643d307e1c7cd807d9ed9fcfa7d845
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714315"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="63476-103">.NET Core’a taşıma konusunda yardımcı olabilecek araçlar</span><span class="sxs-lookup"><span data-stu-id="63476-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="63476-104">Bu makalede listelenen araçları, taşıma sırasında yararlı bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63476-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="63476-105">[.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) -kodunuzun, .NET Framework ve .NET Core arasında nasıl olduğunu gösteren bir rapor üreten bir araç Zinciri:</span><span class="sxs-lookup"><span data-stu-id="63476-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="63476-106">[Komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak</span><span class="sxs-lookup"><span data-stu-id="63476-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="63476-107">[Visual Studio uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) olarak</span><span class="sxs-lookup"><span data-stu-id="63476-107">As a [Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="63476-108">[.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -farklı platformlarda API 'ler için C# olası uyumluluk risklerini tespit eden ve kullanım dışı API 'Leri çağrılarını algılayan bir Roslyn Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="63476-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="63476-109">Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracı Ile .NET Core proje dosyası biçiminde daha küçük çözümler veya ayrı projeler için bağlantı kurmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63476-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="63476-110">CsprojToVs2017, üçüncü taraf bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="63476-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="63476-111">Tüm projeleriniz için çalışacağından emin olmaz ve bağlı olduğunuz davranışta hafif değişikliklere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="63476-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="63476-112">CsprojToVs2017, otomatikleştirilen temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63476-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="63476-113">Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="63476-113">It is not a guaranteed solution to migrating project file formats.</span></span>
