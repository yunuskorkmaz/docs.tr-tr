---
title: Visual Studio 2017 ile Merhaba Dünya uygulamanızı yayımlama
description: Yayımlama, uygulamanızı çalıştırmak için gereken dosyaları kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet
ms.openlocfilehash: e44ae69c9cd8f0767e369791737cef9b4c33f963
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706349"
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="4586d-103">Visual Studio 2017 ile Merhaba Dünya uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="4586d-103">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="4586d-104">İçinde [Visual Studio 2017'de .NET Core ile bir C# Merhaba Dünya uygulaması derleme](with-visual-studio.md) veya [Visual Studio 2017'de .NET Core ile bir Visual Basic Merhaba Dünya uygulaması derleme](vb-with-visual-studio.md), bir Hello World konsol uygulamanızı oluşturdunuz .</span><span class="sxs-lookup"><span data-stu-id="4586d-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="4586d-105">İçinde [Visual Studio 2017 ile C# Merhaba Dünya uygulamanızın hatalarını](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısını kullanarak test.</span><span class="sxs-lookup"><span data-stu-id="4586d-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="4586d-106">Artık beklendiği gibi çalıştığından emin olduğunuza göre diğer kullanıcıların çalıştırabilmek yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4586d-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="4586d-107">Uygulamanızı çalıştırmak için gereken dosyaları kümesini yayımlama oluşturur ve bir hedef makineye kopyalayarak dosyaları dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4586d-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="4586d-108">Yayımlama ve uygulamanızı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="4586d-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="4586d-109">Visual Studio, uygulamanızın sürümünü oluşturuyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="4586d-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="4586d-110">Gerekirse araç çubuğundaki derleme yapılandırma ayarını değiştirme **hata ayıklama** için **yayın**.</span><span class="sxs-lookup"><span data-stu-id="4586d-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="4586d-112">Sağ **HelloWorld** seçin ve proje (HelloWorld çözümü değil) **Yayımla** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="4586d-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="4586d-113">Belirleyebilirsiniz **yayımlama HelloWorld** ana Visual Studio'dan **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="4586d-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio araç çubuğu](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="4586d-116">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="4586d-116">Open a console window.</span></span> <span data-ttu-id="4586d-117">Örneğin **aramak için buraya yazın** metin kutusunda Windows görev çubuğunda, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açıyor **komut istemi** Masaüstü uygulama veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4586d-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="4586d-118">Yayımlanan uygulamayı gidin `bin\release\PublishOutput` uygulamanızın proje dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="4586d-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="4586d-119">Aşağıdaki şekilde gösterildiği gibi yayımlanmış çıktısı aşağıdaki dört dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="4586d-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="4586d-120">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="4586d-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="4586d-121">Uygulamanın çalışma zamanı bağımlılıkları dosyası.</span><span class="sxs-lookup"><span data-stu-id="4586d-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="4586d-122">.NET Core bileşenlerinin tanımlar ve kitaplıkları (uygulamanızı içeren bir dinamik bağlantı kitaplığı dahil), uygulamanızı çalıştırmak gerekli.</span><span class="sxs-lookup"><span data-stu-id="4586d-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="4586d-123">Daha fazla bilgi için [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4586d-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="4586d-124">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="4586d-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="4586d-125">Uygulamanızı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="4586d-125">The file that contains your application.</span></span> <span data-ttu-id="4586d-126">Girerek yürütülebilecek bir dinamik bağlantı kitaplığı, `dotnet HelloWorld.dll` konsol penceresinde komutu.</span><span class="sxs-lookup"><span data-stu-id="4586d-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="4586d-127">*HelloWorld.pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="4586d-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="4586d-128">Hata ayıklama sembollerini içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="4586d-128">A file that contains debug symbols.</span></span> <span data-ttu-id="4586d-129">Uygulamanızın yayımlanmış sürümünün hata ayıklama yapmanız durumunda, kaydetmeniz gerekir ancak bu dosya, uygulamanızın yanı sıra dağıtmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4586d-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="4586d-130">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="4586d-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="4586d-131">Uygulamanın çalışma zamanı yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4586d-131">The application's runtime configuration file.</span></span> <span data-ttu-id="4586d-132">Bu, uygulamanızı çalıştırmak için oluşturulmuş bir .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4586d-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="4586d-133">Daha fazla bilgi için [çalışma zamanı yapılandırma dosyalarını](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4586d-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Yayımlanan dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="4586d-135">Yayımlama işlemi dağıtım türünde yayımlanan uygulama için sistemde yüklü .NET Core ile .NET Core tarafından desteklenen herhangi bir platformda çalıştıracağınız bir framework bağımlı dağıtımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4586d-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="4586d-136">Kullanıcılar, uygulamanızı yayımlayarak çalıştırabilirsiniz `dotnet HelloWorld.dll` bir konsol penceresi komutu.</span><span class="sxs-lookup"><span data-stu-id="4586d-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="4586d-137">.NET Core uygulamaları dağıtma ve yayımlama hakkında daha fazla bilgi için bkz. [.NET Core uygulaması dağıtımını](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="4586d-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
