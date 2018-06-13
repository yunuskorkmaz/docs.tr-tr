---
title: Visual Studio 2017 Hello World uygulamanızla yayımlama
description: Yayımlama uygulamanızı çalıştırmak için gerekli dosyaları kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.openlocfilehash: 11421c8820dd562ba1dbb5900ba1e9bf944b45d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212137"
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="82952-103">Visual Studio 2017 Hello World uygulamanızla yayımlama</span><span class="sxs-lookup"><span data-stu-id="82952-103">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="82952-104">İçinde [bir C# Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile yapı](with-visual-studio.md) veya [.NET Core Visual Studio 2017'de Visual Basic Hello World uygulamayla yapı](vb-with-visual-studio.md), Hello World konsol uygulaması yerleşik .</span><span class="sxs-lookup"><span data-stu-id="82952-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="82952-105">İçinde [Visual Studio 2017 ile C# Hello World uygulamanızda hata ayıklama](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısı kullanarak test.</span><span class="sxs-lookup"><span data-stu-id="82952-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="82952-106">Beklendiği gibi çalıştığını emin, diğer kullanıcılar bunu çalıştırabilmeniz için yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82952-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="82952-107">Uygulamanızı çalıştırmak için gerekli dosyaları kümesini yayımlama oluşturur ve bir hedef makine kopyalayarak dosyaları dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82952-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="82952-108">Yayımlama ve uygulamanızı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="82952-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="82952-109">Visual Studio sürümü, uygulamanızın oluşturuyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="82952-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="82952-110">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını değiştirme **hata ayıklama** için **sürüm**.</span><span class="sxs-lookup"><span data-stu-id="82952-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="82952-112">Sağ **HelloWorld** proje (HelloWorld çözümü değil) ve seçin **Yayımla** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="82952-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="82952-113">Öğesini de seçebilirsiniz **yayımlama HelloWorld** ana Visual Studio'dan **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="82952-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="82952-116">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="82952-116">Open a console window.</span></span> <span data-ttu-id="82952-117">Örneğin **aramak için buraya yazın** metin kutusunda Windows görev çubuğundaki, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açın **komut istemi** Masaüstü uygulama veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="82952-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="82952-118">Yayımlanan uygulamayı gidin `bin\release\PublishOutput` uygulamanızın proje dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="82952-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="82952-119">Aşağıdaki şekilde gösterildiği gibi yayımlanmış çıktı aşağıdaki dört dosya içerir:</span><span class="sxs-lookup"><span data-stu-id="82952-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="82952-120">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="82952-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="82952-121">Uygulamanın çalışma zamanı bağımlılıkları dosyası.</span><span class="sxs-lookup"><span data-stu-id="82952-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="82952-122">.NET Core bileşenleri tanımlar ve (uygulamanızın içeren dinamik bağlantı kitaplığı dahil) kitaplıkları uygulamanızı çalıştırmak için gerekli.</span><span class="sxs-lookup"><span data-stu-id="82952-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="82952-123">Daha fazla bilgi için bkz: [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="82952-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="82952-124">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="82952-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="82952-125">Uygulamanızı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="82952-125">The file that contains your application.</span></span> <span data-ttu-id="82952-126">Girerek yürütülebilir bir dinamik bağlantı kitaplığı olan `dotnet HelloWorld.dll` bir konsol penceresinde komutu.</span><span class="sxs-lookup"><span data-stu-id="82952-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="82952-127">*HelloWorld.pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="82952-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="82952-128">Hata ayıklama simgeleri içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="82952-128">A file that contains debug symbols.</span></span> <span data-ttu-id="82952-129">Yayımlanmış bir sürüm, uygulamanızın hatalarını ayıklama gerek gerektiğinde, kaydetmelisiniz rağmen bu dosya, uygulamanızın birlikte dağıtmak için gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="82952-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="82952-130">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="82952-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="82952-131">Uygulamanın çalışma zamanı yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="82952-131">The application's runtime configuration file.</span></span> <span data-ttu-id="82952-132">Uygulamanızı çalıştırmak için oluşturulan .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82952-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="82952-133">Daha fazla bilgi için bkz: [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="82952-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Yayımlanmış dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="82952-135">Yayımlama işlemi yayımlanan uygulama sistemde yüklü .NET Core ile .NET Core tarafından desteklenen herhangi bir platformda çalıştırılacağı dağıtım türü olan bir framework bağımlı dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82952-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="82952-136">Kullanıcılar, uygulamanızın vererek çalıştırabilirsiniz `dotnet HelloWorld.dll` bir konsol penceresinden komutu.</span><span class="sxs-lookup"><span data-stu-id="82952-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="82952-137">Yayımlama ve .NET Core uygulamaları dağıtma hakkında daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="82952-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
