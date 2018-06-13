---
title: Roslyn .NET çözümleyiciler - temel
description: Sorunları bulmak ve bu sorunları düzeltmelerin önerilen temel Roslyn Çözümleyicileri hakkında bilgi edinin.
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ec153b8fed08ef245a3a0f58970b4e3955dfacb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567269"
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="aa92d-103">Çözümleyiciler Roslyn dayalı</span><span class="sxs-lookup"><span data-stu-id="aa92d-103">The Roslyn based Analyzers</span></span>

<span data-ttu-id="aa92d-104">Roslyn tabanlı çözümleyiciler sorunları bulmak ve düzeltmeleri önermek için projenizin kaynak kodu çözümlemek için .NET derleyici SDK'sı (Roslyn API) kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa92d-104">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="aa92d-105">Farklı sınıflar API Uyumluluk için güvenlik sorunlarının hatalara neden olabilecek uygulamalar arasında değişen sorunların farklı çözümleyiciler arayın.</span><span class="sxs-lookup"><span data-stu-id="aa92d-105">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="aa92d-106">Çözümleyiciler Roslyn tabanlı hem de etkileşimli ve derlemeleri sırasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="aa92d-106">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="aa92d-107">Çözümleyici Visual Studio'da veya komut satırı derlemeleri farklı bir Rehber sağlanır.</span><span class="sxs-lookup"><span data-stu-id="aa92d-107">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="aa92d-108">Visual Studio'da kodu düzenlerken sorunları tetiklemek kod oluşturur oluşturmaz olası sorunları yakalama değişiklik yapmak gibi çözümleyiciler çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aa92d-108">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="aa92d-109">Tüm sorunları, herhangi bir sorun altında dalgalı çizgiler ile vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="aa92d-109">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="aa92d-110">Visual Studio bir ampul görüntüler ve üzerine tıkladığınızda Çözümleyicisi bu sorunun olası düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="aa92d-110">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="aa92d-111">Projeyi derlerken Visual Studio'da ya da komut satırından, tüm kaynak kodunu analiz edilir ve Çözümleyicisi olası sorunları tam bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa92d-111">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="aa92d-112">Aşağıdaki şekilde bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa92d-112">The following figure shows one example.</span></span>

![framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

<span data-ttu-id="aa92d-114">Roslyn tabanlı çözümleyiciler hatalar, uyarılar ve bilgiler sorunun önem derecesine göre olarak olası sorunları bildirin.</span><span class="sxs-lookup"><span data-stu-id="aa92d-114">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="aa92d-115">Projenizdeki NuGet paketlerini Roslyn tabanlı çözümleyiciler yükleyin.</span><span class="sxs-lookup"><span data-stu-id="aa92d-115">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="aa92d-116">Yapılandırılmış Çözümleyicileri ve her Çözümleyicisi için herhangi bir ayarı geri ve bu proje için her geliştiricinin makinede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aa92d-116">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="aa92d-117">Roslyn tabanlı Çözümleyicileri için kullanıcı deneyimi kod analiz kitaplıkları'nın eski sürümleri FxCop ve güvenlik analiz araçları, ister kullanılandan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="aa92d-117">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="aa92d-118">Açıkça Roslyn tabanlı çözümleyiciler çalışması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aa92d-118">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="aa92d-119">Visual Studio'da "Çözümle" menüsünden "Kod Analizi Çalıştır" menü öğelerini kullanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="aa92d-119">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="aa92d-120">Çalışırken Roslyn tabanlı çözümleyiciler asychronously çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aa92d-120">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="aa92d-121">Belirli çözümleyicileri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="aa92d-121">More information on specific analyzers</span></span>

<span data-ttu-id="aa92d-122">Aşağıdaki çözümleyiciler, bu bölümde ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="aa92d-122">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="aa92d-123">[API Çözümleyicisi](api-analyzer.md): Bu Çözümleyicisi kodunuzu olası uyumluluk riskler açısından inceler veya kullanım dışı API'lerinin kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa92d-123">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="aa92d-124">[Framework Çözümleyicisi](framework-analyzer.md): .NET Framework uygulamaları yönelik yönergeleri izleyen emin olmak için kodunuzu bu Çözümleyicisi inceler.</span><span class="sxs-lookup"><span data-stu-id="aa92d-124">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="aa92d-125">Bu kurallar birkaç tabanlı güvenlik önerileri içerir.</span><span class="sxs-lookup"><span data-stu-id="aa92d-125">These rules include several security-based recommendations.</span></span>
