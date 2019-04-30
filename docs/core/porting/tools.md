---
title: .NET Core'a taşıma araçları
description: .NET Core için bağlantı noktası için kullanabileceğiniz araçlardan bazıları hakkında bilgi edinin
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 88e3edb0442b3326a77323fe4b6396f3eb1ca767
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663121"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="af522-103">.NET Core'a taşıma ile yardımcı olacak araçlar</span><span class="sxs-lookup"><span data-stu-id="af522-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="af522-104">Bu makale faydalı taşırken listelenen araçlar bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="af522-104">You may find the tools listed in this article helpful when porting:</span></span>

* <span data-ttu-id="af522-105">[.NET portability Analyzer](../../standard/analyzers/portability-analyzer.md), nasıl taşınabilir kod .NET Framework ve .NET Core arasında olan bir rapor oluşturabilen bir araç zinciri:  Olarak bir [komut satırı aracını](https://github.com/Microsoft/dotnet-apiport/releases) olarak bir [Visual Studio uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="af522-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:  As a [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) As a [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
* <span data-ttu-id="af522-106">[.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) -olası uyumluluk bulur bir Roslyn çözümleyicinizi risklerini için C# farklı platformlarda API'leri ve kullanım dışı API'lere giden çağrıların algılar.</span><span class="sxs-lookup"><span data-stu-id="af522-106">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="af522-107">Ayrıca, bağlantı noktası daha küçük çözümleri veya .NET Core proje dosyası biçimi ile tek tek projelere deneyebilirsiniz [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracı.</span><span class="sxs-lookup"><span data-stu-id="af522-107">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="af522-108">CsprojToVs2017 üçüncü taraf bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="af522-108">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="af522-109">Tüm projeleriniz için çalışacak bir garanti yoktur ve ince değişiklikler, bağımlı davranış neden.</span><span class="sxs-lookup"><span data-stu-id="af522-109">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="af522-110">CsprojToVs2017 olarak kullanılmalıdır bir _başlangıç noktası_ otomatikleştirilebilir temel işlemleri otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="af522-110">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="af522-111">Bu geçişi proje dosya biçimleri için garantili bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="af522-111">It is not a guaranteed solution to migrating project file formats.</span></span>