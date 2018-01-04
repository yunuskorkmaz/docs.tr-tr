---
title: "Visual Studio 2017 Hello World uygulamanızla yayımlama"
description: "Yayımlama uygulamanızı çalıştırmak için gerekli dosyaları kümesini oluşturur."
keywords: "Yayımlama, dağıtım .NET, .NET core konsol uygulaması"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.workload: dotnetcore
ms.openlocfilehash: 40479d85f9b31fcc80e3d12537126941878a09a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="4bbab-104">Visual Studio 2017 Hello World uygulamanızla yayımlama</span><span class="sxs-lookup"><span data-stu-id="4bbab-104">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="4bbab-105">İçinde [bir C# Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile yapı](with-visual-studio.md) veya [.NET Core Visual Studio 2017'de Visual Basic Hello World uygulamayla yapı](vb-with-visual-studio.md), Hello World konsol uygulaması yerleşik .</span><span class="sxs-lookup"><span data-stu-id="4bbab-105">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="4bbab-106">İçinde [Visual Studio 2017 ile C# Hello World uygulamanızda hata ayıklama](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısı kullanarak test.</span><span class="sxs-lookup"><span data-stu-id="4bbab-106">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="4bbab-107">Beklendiği gibi çalıştığını emin, diğer kullanıcılar bunu çalıştırabilmeniz için yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bbab-107">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="4bbab-108">Uygulamanızı çalıştırmak için gerekli dosyaları kümesini yayımlama oluşturur ve bir hedef makine kopyalayarak dosyaları dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bbab-108">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="4bbab-109">Yayımlama ve uygulamanızı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="4bbab-109">To publish and run your application:</span></span> 

1. <span data-ttu-id="4bbab-110">Visual Studio sürümü, uygulamanızın oluşturuyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="4bbab-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="4bbab-111">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını değiştirme **hata ayıklama** için **sürüm**.</span><span class="sxs-lookup"><span data-stu-id="4bbab-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="4bbab-113">Sağ **HelloWorld** proje (HelloWorld çözümü değil) ve seçin **Yayımla** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="4bbab-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="4bbab-114">Öğesini de seçebilirsiniz **yayımlama HelloWorld** ana Visual Studio'dan **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="4bbab-114">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="4bbab-117">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="4bbab-117">Open a console window.</span></span> <span data-ttu-id="4bbab-118">Örneğin **aramak için buraya yazın** metin kutusunda Windows görev çubuğundaki, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açın **komut istemi** Masaüstü uygulama veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4bbab-118">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="4bbab-119">Yayımlanan uygulamayı gidin `bin\release\PublishOutput` uygulamanızın proje dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="4bbab-119">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="4bbab-120">Aşağıdaki şekilde gösterildiği gibi yayımlanmış çıktı aşağıdaki dört dosya içerir:</span><span class="sxs-lookup"><span data-stu-id="4bbab-120">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="4bbab-121">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="4bbab-121">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="4bbab-122">Uygulamanın çalışma zamanı bağımlılıkları dosyası.</span><span class="sxs-lookup"><span data-stu-id="4bbab-122">The application's runtime dependencies file.</span></span> <span data-ttu-id="4bbab-123">.NET Core bileşenleri tanımlar ve (uygulamanızın içeren dinamik bağlantı kitaplığı dahil) kitaplıkları uygulamanızı çalıştırmak için gerekli.</span><span class="sxs-lookup"><span data-stu-id="4bbab-123">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="4bbab-124">Daha fazla bilgi için bkz: [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4bbab-124">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="4bbab-125">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="4bbab-125">*HelloWorld.dll*</span></span>

         <span data-ttu-id="4bbab-126">Uygulamanızı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="4bbab-126">The file that contains your application.</span></span> <span data-ttu-id="4bbab-127">Girerek yürütülebilir bir dinamik bağlantı kitaplığı olan `dotnet HelloWorld.dll` bir konsol penceresinde komutu.</span><span class="sxs-lookup"><span data-stu-id="4bbab-127">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="4bbab-128">*HelloWorld.pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="4bbab-128">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="4bbab-129">Hata ayıklama simgeleri içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="4bbab-129">A file that contains debug symbols.</span></span> <span data-ttu-id="4bbab-130">Yayımlanmış bir sürüm, uygulamanızın hatalarını ayıklama gerek gerektiğinde, kaydetmelisiniz rağmen bu dosya, uygulamanızın birlikte dağıtmak için gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="4bbab-130">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="4bbab-131">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="4bbab-131">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="4bbab-132">Uygulamanın çalışma zamanı yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4bbab-132">The application's runtime configuration file.</span></span> <span data-ttu-id="4bbab-133">Uygulamanızı çalıştırmak için oluşturulan .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4bbab-133">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="4bbab-134">Daha fazla bilgi için bkz: [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4bbab-134">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Yayımlanmış dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="4bbab-136">Yayımlama işlemi yayımlanan uygulama sistemde yüklü .NET Core ile .NET Core tarafından desteklenen herhangi bir platformda çalıştırılacağı dağıtım türü olan bir framework bağımlı dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4bbab-136">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="4bbab-137">Kullanıcılar, uygulamanızın vererek çalıştırabilirsiniz `dotnet HelloWorld.dll` bir konsol penceresinden komutu.</span><span class="sxs-lookup"><span data-stu-id="4bbab-137">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="4bbab-138">Yayımlama ve .NET Core uygulamaları dağıtma hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="4bbab-138">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
