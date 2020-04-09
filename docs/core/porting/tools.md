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
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="f6301-103">.NET Core’a taşıma konusunda yardımcı olabilecek araçlar</span><span class="sxs-lookup"><span data-stu-id="f6301-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="f6301-104">Bu makalede listelenen araçları taşıma yaparken yararlı bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f6301-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="f6301-105">[.NET Taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) - Kodunuzu .NET Framework ve .NET Core arasında ne kadar taşınabilir olduğuna dair bir rapor oluşturabilen bir araç zinciri:</span><span class="sxs-lookup"><span data-stu-id="f6301-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="f6301-106">Komut [satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) olarak</span><span class="sxs-lookup"><span data-stu-id="f6301-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="f6301-107">Visual [Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) olarak</span><span class="sxs-lookup"><span data-stu-id="f6301-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="f6301-108">[.NET API çözümleyicisi](../../standard/analyzers/api-analyzer.md) - Farklı platformlarda C# API'leri için olası uyumluluk risklerini keşfeden ve amortismana alınan API'lere yönelik çağrıları algılayan bir Roslyn çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f6301-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="f6301-109">Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracıyla daha küçük çözümleri veya tek tek projeleri .NET Core proje dosya biçimine taşımayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6301-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="f6301-110">CsprojToVs2017 üçüncü taraf bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="f6301-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="f6301-111">Tüm projeleriniz için çalışacağının garantisi yoktur ve bağlı olduğunuz davranışta ince değişikliklere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6301-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="f6301-112">CsprojToVs2017, otomatikleştirilebilen temel şeyleri otomatikleştiren bir _başlangıç noktası_ olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6301-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="f6301-113">Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="f6301-113">It is not a guaranteed solution to migrating project file formats.</span></span>
