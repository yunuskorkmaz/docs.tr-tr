---
title: "Roslyn .NET çözümleyiciler - temel"
description: "Sorunları bulmak ve bu sorunları düzeltmelerin önerilen temel Roslyn Çözümleyicileri hakkında bilgi edinin."
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="b9d00-104">Çözümleyiciler Roslyn dayalı</span><span class="sxs-lookup"><span data-stu-id="b9d00-104">The Roslyn based Analyzers</span></span>

<span data-ttu-id="b9d00-105">Roslyn tabanlı çözümleyiciler sorunları bulmak ve düzeltmeleri önermek için projenizin kaynak kodu çözümlemek için .NET derleyici SDK'sı (Roslyn API) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b9d00-105">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="b9d00-106">Farklı sınıflar API Uyumluluk için güvenlik sorunlarının hatalara neden olabilecek uygulamalar arasında değişen sorunların farklı çözümleyiciler arayın.</span><span class="sxs-lookup"><span data-stu-id="b9d00-106">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="b9d00-107">Çözümleyiciler Roslyn tabanlı hem de etkileşimli ve derlemeleri sırasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="b9d00-107">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="b9d00-108">Çözümleyici Visual Studio'da veya komut satırı derlemeleri farklı bir Rehber sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b9d00-108">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="b9d00-109">Visual Studio'da kodu düzenlerken sorunları tetiklemek kod oluşturur oluşturmaz olası sorunları yakalama değişiklik yapmak gibi çözümleyiciler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b9d00-109">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="b9d00-110">Tüm sorunları, herhangi bir sorun altında dalgalı çizgiler ile vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="b9d00-110">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="b9d00-111">Visual Studio bir ampul görüntüler ve üzerine tıkladığınızda Çözümleyicisi bu sorunun olası düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="b9d00-111">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="b9d00-112">Projeyi derlerken Visual Studio'da ya da komut satırından, tüm kaynak kodunu analiz edilir ve Çözümleyicisi olası sorunları tam bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9d00-112">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="b9d00-113">Aşağıdaki şekilde bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9d00-113">The following figure shows one example.</span></span>

![framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

<span data-ttu-id="b9d00-115">Roslyn tabanlı çözümleyiciler hatalar, uyarılar ve bilgiler sorunun önem derecesine göre olarak olası sorunları bildirin.</span><span class="sxs-lookup"><span data-stu-id="b9d00-115">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="b9d00-116">Projenizdeki NuGet paketlerini Roslyn tabanlı çözümleyiciler yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b9d00-116">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="b9d00-117">Yapılandırılmış Çözümleyicileri ve her Çözümleyicisi için herhangi bir ayarı geri ve bu proje için her geliştiricinin makinede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b9d00-117">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="b9d00-118">Roslyn tabanlı Çözümleyicileri için kullanıcı deneyimi kod analiz kitaplıkları'nın eski sürümleri FxCop ve güvenlik analiz araçları, ister kullanılandan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b9d00-118">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="b9d00-119">Açıkça Roslyn tabanlı çözümleyiciler çalışması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b9d00-119">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="b9d00-120">Visual Studio'da "Çözümle" menüsünden "Kod Analizi Çalıştır" menü öğelerini kullanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="b9d00-120">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="b9d00-121">Çalışırken Roslyn tabanlı çözümleyiciler asychronously çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b9d00-121">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="b9d00-122">Belirli çözümleyicileri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="b9d00-122">More information on specific analyzers</span></span>

<span data-ttu-id="b9d00-123">Aşağıdaki çözümleyiciler, bu bölümde ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="b9d00-123">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="b9d00-124">[API Çözümleyicisi](api-analyzer.md): Bu Çözümleyicisi kodunuzu olası uyumluluk riskler açısından inceler veya kullanım dışı API'lerinin kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9d00-124">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="b9d00-125">[Framework Çözümleyicisi](framework-analyzer.md): .NET Framework uygulamaları yönelik yönergeleri izleyen emin olmak için kodunuzu bu Çözümleyicisi inceler.</span><span class="sxs-lookup"><span data-stu-id="b9d00-125">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="b9d00-126">Bu kurallar birkaç tabanlı güvenlik önerileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b9d00-126">These rules include several security-based recommendations.</span></span>
