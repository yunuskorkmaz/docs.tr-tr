---
title: ".NET taşınabilirlik Çözümleyicisi - .NET"
description: "Çeşitli .NET uygulamalarını arasında nasıl taşınabilir kodunuz: değerlendirilecek .NET taşınabilirlik Çözümleyicisi aracını kullanmayı öğrenin."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fef0ddb05cd95c2db5492004c46951bb69ea01d8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="the-net-portability-analyzer"></a><span data-ttu-id="8459c-104">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="8459c-104">The .NET Portability Analyzer</span></span>

<span data-ttu-id="8459c-105">Birden çok platform Kitaplıklarınızı olmak istersiniz?</span><span class="sxs-lookup"><span data-stu-id="8459c-105">Want to make your libraries multi-platform?</span></span> <span data-ttu-id="8459c-106">Ne kadar iş uygulamanızın diğer .NET uygulamaları ile uyumlu hale getirmek için gereken görmek mi istiyorsunuz?</span><span class="sxs-lookup"><span data-stu-id="8459c-106">Want to see how much work is required to make your application compatible with other .NET implementations?</span></span> <span data-ttu-id="8459c-107">[.NET taşınabilirlik Çözümleyicisi](http://go.microsoft.com/fwlink/?LinkID=507467) nasıl programınızı .NET uygulamaları arasında derlemeleri çözümleyerek esnektir üzerinde ayrıntılı bir rapor sağlayan bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="8459c-107">The [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) is a tool that provides you with a detailed report on how flexible your program is across .NET implementations by analyzing assemblies.</span></span> <span data-ttu-id="8459c-108">Taşınabilirlik Çözümleyicisi Visual Studio uzantısı ve bir konsol uygulaması olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="8459c-108">The Portability Analyzer is offered as a Visual Studio Extension and as a console app.</span></span>

## <a name="new-targets"></a><span data-ttu-id="8459c-109">Yeni hedefler</span><span class="sxs-lookup"><span data-stu-id="8459c-109">New targets</span></span>

* <span data-ttu-id="8459c-110">[.NET core](https://dotnetfoundation.org/net-core): modüler bir tasarıma sahiptir, yan yana uygular ve platformlar arası senaryolar hedefler.</span><span class="sxs-lookup"><span data-stu-id="8459c-110">[.NET Core](https://dotnetfoundation.org/net-core): Has a modular design, employs side-by-side, and targets cross-platform scenarios.</span></span> <span data-ttu-id="8459c-111">Yan yana diğer uygulamalar bozmadan yeni .NET Core sürümleri benimsemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8459c-111">Side-by-side allows you to adopt new .NET Core versions without breaking other apps.</span></span>
* <span data-ttu-id="8459c-112">[ASP.NET Core](https://dotnetfoundation.org/asp-net-core): bir çerçevedir modern web-böylece geliştiriciler aynı avantajları vermiş .NET Core üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8459c-112">[ASP.NET Core](https://dotnetfoundation.org/asp-net-core): is a modern web-framework built on .NET Core thus giving developers the same benefits.</span></span>
* <span data-ttu-id="8459c-113">[Evrensel Windows platformu](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): x64 ve ARM makineler .NET yerel'ın statik derleme kullanarak çalışan Windows mağazası uygulamalarınızı performansını artırma.</span><span class="sxs-lookup"><span data-stu-id="8459c-113">[Universal Windows Platform](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): Improve performance of your Windows Store apps that run on x64 and ARM machines by using .NET Native’s static compilation.</span></span> 
* <span data-ttu-id="8459c-114">.NET core + Platform uzantıları: .NET ekosistemi WCF ve ASP.NET Core, FSharp ve Azure gibi diğer API'lerin yanı sıra .NET Core API'ları içerir.</span><span class="sxs-lookup"><span data-stu-id="8459c-114">.NET Core + Platform Extensions: Includes the .NET Core APIs in addition to other APIs in the .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>
* <span data-ttu-id="8459c-115">.NET standart + Platform uzantıları: WCF ve ASP.NET Core, FSharp ve Azure gibi diğer .NET ekosistemi yanı sıra .NET standart API'lerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8459c-115">.NET Standard + Platform Extensions: Includes the .NET Standard APIs in addition to other .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>

## <a name="how-to-use-portability-analyzer"></a><span data-ttu-id="8459c-116">Taşınabilirlik Çözümleyicisi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="8459c-116">How to use Portability Analyzer</span></span>

<span data-ttu-id="8459c-117">.NET taşınabilirlik Analyzer'ı kullanmaya başlamak için önce uzantısını yükleyip gerek [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=507467).</span><span class="sxs-lookup"><span data-stu-id="8459c-117">To begin using the .NET Portability Analyzer, you first need to download and install the extension from the [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=507467).</span></span> <span data-ttu-id="8459c-118">Visual Studio 2015 ve Visual Studio 2017 üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8459c-118">It works on Visual Studio 2015 and Visual Studio 2017.</span></span> <span data-ttu-id="8459c-119">Visual Studio yapılandırma **Çözümle** > **taşınabilirlik Çözümleyicisi ayarları** ve hedef platformları seçin.</span><span class="sxs-lookup"><span data-stu-id="8459c-119">You can configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms.</span></span>

![Taşınabilirlik ekran görüntüsü](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="8459c-121">Tüm projenizi analiz etmek için projenize sağ tıklayın **Çözüm Gezgini** seçip **analiz derleme taşınabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="8459c-121">To analyze your entire project, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="8459c-122">Aksi takdirde, Git **Çözümle** menü ve Seç **analiz derleme taşınabilirlik**.</span><span class="sxs-lookup"><span data-stu-id="8459c-122">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="8459c-123">Buradan, projenizin çalıştırılabilir veya DLL seçin.</span><span class="sxs-lookup"><span data-stu-id="8459c-123">From there, select your project’s executable or DLL.</span></span>

![Taşınabilirlik Çözüm Gezgini](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="8459c-125">Analiz çalıştırdıktan sonra .NET taşınabilirlik raporunuzu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8459c-125">After running the analysis, you will see your .NET Portability Report.</span></span> <span data-ttu-id="8459c-126">Yalnızca hedef platformu tarafından desteklenmeyen türlerini listede görünür ve önerileri gözden geçirebilirsiniz **iletileri** sekmesinde **hata listesi**.</span><span class="sxs-lookup"><span data-stu-id="8459c-126">Only types that are unsupported by a target platform appear in the list and you can review recommendations in the **Messages** tab in the **Error List**.</span></span> <span data-ttu-id="8459c-127">Sorunlu alanları doğrudan da atlayabilirsiniz **iletileri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="8459c-127">You can also jump to problem areas directly from the **Messages** tab.</span></span>

![Taşınabilirlik raporu](./media/portability-analyzer/portability-report.png)

<span data-ttu-id="8459c-129">Visual Studio kullanmak istemiyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="8459c-129">Don’t want to use Visual Studio?</span></span> <span data-ttu-id="8459c-130">Komut isteminden taşınabilirlik Çözümleyicisi'ni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8459c-130">You can also use the Portability Analyzer from the command prompt.</span></span> <span data-ttu-id="8459c-131">Yalnızca karşıdan [API taşınabilirlik Çözümleyicisi](http://www.microsoft.com/download/details.aspx?id=42678).</span><span class="sxs-lookup"><span data-stu-id="8459c-131">Just download the [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678).</span></span>

*   <span data-ttu-id="8459c-132">Geçerli dizin çözümlemek için aşağıdaki komutu yazın:`\...\ApiPort.exe analyze -f .`</span><span class="sxs-lookup"><span data-stu-id="8459c-132">Type the following command to analyze the current directory: `\...\ApiPort.exe analyze -f .`</span></span>
*   <span data-ttu-id="8459c-133">Belirli bir .dll dosyaları listesini çözümlemek için aşağıdaki komutu yazın:`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span><span class="sxs-lookup"><span data-stu-id="8459c-133">To analyze a specific list of .dll files, type the following command: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span></span>

<span data-ttu-id="8459c-134">.NET taşınabilirlik raporunuzu bir Excel dosyası olarak kaydedilir (*.xlsx*) geçerli dizininizde.</span><span class="sxs-lookup"><span data-stu-id="8459c-134">Your .NET Portability Report is saved as an Excel file (*.xlsx*) in your current directory.</span></span> <span data-ttu-id="8459c-135">**Ayrıntıları** Excel çalışma kitabı sekmesi daha fazla bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="8459c-135">The **Details** tab in the Excel Workbook contains more information.</span></span>

<span data-ttu-id="8459c-136">.NET taşınabilirlik Çözümleyicisi hakkında daha fazla bilgi için ziyaret [GitHub belgelerine](https://github.com/Microsoft/dotnet-apiport#documentation) ve [A kısa bakabilir .NET taşınabilirlik Çözümleyicisi](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span><span class="sxs-lookup"><span data-stu-id="8459c-136">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>
