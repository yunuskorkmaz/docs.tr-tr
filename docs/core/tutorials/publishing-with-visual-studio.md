---
title: .NET Core Merhaba Dünya uygulamanızı Visual Studio 2017 ile yayımlama
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660482"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="8cf77-103">.NET Core Merhaba Dünya uygulamanızı Visual Studio 2017 ile yayımlama</span><span class="sxs-lookup"><span data-stu-id="8cf77-103">Publish your .NET Core Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="8cf77-104">Visual [studio 2017 C# ' de .net Core ile Merhaba Dünya bir uygulama oluşturun](with-visual-studio.md) veya [Visual Studio 2017 ' de .NET Core ile Visual Basic Merhaba Dünya uygulaması oluşturun](vb-with-visual-studio.md)Merhaba Dünya konsol uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8cf77-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="8cf77-105">[Visual studio 2017 C# Ile Merhaba Dünya uygulamanızda hata ayıklayın](debugging-with-visual-studio.md), Visual Studio hata ayıklayıcısını kullanarak test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf77-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="8cf77-106">Artık beklendiği gibi çalıştığından emin olduğunuza göre, diğer kullanıcıların çalıştırabilmesi için onu yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf77-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="8cf77-107">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur ve dosyaları bir hedef makineye kopyalayarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf77-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="8cf77-108">Uygulamanızı yayımlamak ve çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="8cf77-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="8cf77-109">Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8cf77-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="8cf77-110">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8cf77-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="8cf77-112">**HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="8cf77-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="8cf77-113">Ana Visual Studio **Build** menüsünden **HelloWorld Yayımla** ' yı da seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cf77-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-settings-window.png)

1. <span data-ttu-id="8cf77-116">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="8cf77-116">Open a console window.</span></span> <span data-ttu-id="8cf77-117">Örneğin, burada, Windows görev çubuğundaki metin kutusuna **aramak için yazın** , (veya `cmd` kısaca `Command Prompt` ) girin ve **komut istemi** masaüstü uygulamasını seçerek veya ' de seçili ise ENTER tuşuna basarak bir konsol penceresi açın. Arama sonuçları.</span><span class="sxs-lookup"><span data-stu-id="8cf77-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="8cf77-118">Uygulamanızın proje dizininin `bin\release\PublishOutput` alt dizininde yayınlanan uygulamaya gidin.</span><span class="sxs-lookup"><span data-stu-id="8cf77-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="8cf77-119">Aşağıdaki şekilde gösterildiği gibi, yayımlanan çıktı aşağıdaki dört dosyayı içerir:</span><span class="sxs-lookup"><span data-stu-id="8cf77-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="8cf77-120">*HelloWorld. Deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="8cf77-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="8cf77-121">Uygulamanın çalışma zamanı bağımlılıkları dosyası.</span><span class="sxs-lookup"><span data-stu-id="8cf77-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="8cf77-122">Uygulamanızı çalıştırmak için gerekli olan .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8cf77-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="8cf77-123">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="8cf77-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="8cf77-124">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="8cf77-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="8cf77-125">Uygulamanızı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="8cf77-125">The file that contains your application.</span></span> <span data-ttu-id="8cf77-126">Bir konsol penceresinde `dotnet HelloWorld.dll` komut girilerek yürütülebilecek bir dinamik bağlantı kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="8cf77-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="8cf77-127">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="8cf77-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="8cf77-128">Hata ayıklama sembolleri içeren bir dosya.</span><span class="sxs-lookup"><span data-stu-id="8cf77-128">A file that contains debug symbols.</span></span> <span data-ttu-id="8cf77-129">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8cf77-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="8cf77-130">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="8cf77-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="8cf77-131">Uygulamanın çalışma zamanı yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="8cf77-131">The application's runtime configuration file.</span></span> <span data-ttu-id="8cf77-132">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8cf77-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="8cf77-133">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="8cf77-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Yayımlanan dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

<span data-ttu-id="8cf77-135">Yayımlama işlemi, yayımlanan uygulamanın .NET Core tarafından sistemde yüklü olan herhangi bir platformda çalışacağı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8cf77-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="8cf77-136">Kullanıcılar, `dotnet HelloWorld.dll` bir konsol penceresinden komutu yayımlayarak uygulamanızı çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="8cf77-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="8cf77-137">.NET Core uygulamalarını yayımlama ve dağıtma hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8cf77-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../deploying/index.md).</span></span>
