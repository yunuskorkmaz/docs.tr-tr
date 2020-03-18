---
title: .NET Core Hello World uygulamanızı Visual Studio ile yayınlayın
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156640"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="a2d44-103">.NET Core Hello World uygulamanızı Visual Studio ile yayınlayın</span><span class="sxs-lookup"><span data-stu-id="a2d44-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="a2d44-104">[Visual Studio'da .NET Core ile Hello World uygulaması oluşturun,](with-visual-studio.md)Hello World konsol uytun.</span><span class="sxs-lookup"><span data-stu-id="a2d44-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="a2d44-105">[Visual Studio ile Hello World uygulama hata ayıklama](debugging-with-visual-studio.md)olarak, Visual Studio hata ayıklama kullanarak test etti.</span><span class="sxs-lookup"><span data-stu-id="a2d44-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="a2d44-106">Beklendiği gibi çalıştığından emin olduğunuza göre, diğer kullanıcıların çalıştırabilmesi için yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2d44-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="a2d44-107">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2d44-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="a2d44-108">Dosyaları dağıtmak için, bunları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a2d44-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="a2d44-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="a2d44-109">Publish the app</span></span>

1. <span data-ttu-id="a2d44-110">Visual Studio'nun uygulamanızın Sürüm sürümünü oluşturmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a2d44-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="a2d44-111">Gerekirse, araç çubuğundaki yapı yapılandırma ayarını **Hata Ayıklama'dan** **Release'e**değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Sürüm yapısı seçili Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="a2d44-113">**HelloWorld** projesine (HelloWorld çözümü değil) sağ tıklayın ve menüden **Yayınla'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="a2d44-114">(Ana **Yapı** menüsünden **HelloWorld'ü** Yayımla'yı da seçebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="a2d44-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Visual Studio Bağlam menüsünü yayımla](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="a2d44-116">**Yayımlama hedef** sayfasını seç'te **Klasör'ü**seçin ve ardından **Profil Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Visual Studio'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="a2d44-118">**Yayımla** sayfasında **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-118">On the **Publish** page, select **Publish**.</span></span>

   ![Visual Studio Yayımlama penceresi](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="a2d44-120">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="a2d44-120">Inspect the files</span></span>

<span data-ttu-id="a2d44-121">Yayımlama işlemi, yayımlanan uygulamanın .NET Core tarafından desteklenen ve .NET Core tarafından desteklenen ve sistemde yüklü olan herhangi bir platformda çalıştığı bir dağıtım türü olan çerçeveye bağımlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2d44-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="a2d44-122">Kullanıcılar, çalıştırılabilir uygulamayı çift tıklatarak veya `dotnet HelloWorld.dll` komut isteminden komut vererek yayınlanan uygulamayı çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="a2d44-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="a2d44-123">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a2d44-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="a2d44-124">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="a2d44-124">Open a command prompt.</span></span>

   <span data-ttu-id="a2d44-125">Komut istemini açmanın bir yolu, Windows görev çubuğundaki arama kutusuna **Komut İstemi** (veya kısaca **cmd)** girmektir.</span><span class="sxs-lookup"><span data-stu-id="a2d44-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="a2d44-126">Komut **İstem** masaüstü uygulamasını seçin veya arama sonuçlarında zaten seçiliyse **Enter** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a2d44-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="a2d44-127">*Bin\Release\netcoreapp3.1\publish* alt dizininde yayınlanan uygulamaya gidin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Yayımlanmış dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="a2d44-129">Resimde görüldüğü gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="a2d44-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="a2d44-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="a2d44-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="a2d44-131">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a2d44-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="a2d44-132">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2d44-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="a2d44-133">Daha fazla bilgi için [Runtime yapılandırma dosyalarına](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a2d44-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="a2d44-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="a2d44-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="a2d44-135">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a2d44-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="a2d44-136">Bu dinamik bağlantı kitaplığını `dotnet HelloWorld.dll` yürütmek için komut istemiyle girin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="a2d44-137">*MerhabaWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="a2d44-137">*HelloWorld.exe*</span></span>

         <span data-ttu-id="a2d44-138">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a2d44-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="a2d44-139">Çalıştırmak için komut `HelloWorld.exe` istemiyle girin.</span><span class="sxs-lookup"><span data-stu-id="a2d44-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="a2d44-140">*HelloWorld.pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="a2d44-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="a2d44-141">Bu hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a2d44-141">This is the debug symbols file.</span></span> <span data-ttu-id="a2d44-142">Uygulamanızın yayımlanmış sürümünü hata ayıklamanız gerektiğinde bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a2d44-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="a2d44-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="a2d44-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="a2d44-144">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a2d44-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="a2d44-145">Uygulamanızın üzerinde çalışmak üzere oluşturulmuş olduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2d44-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="a2d44-146">Yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2d44-146">You can also add configuration options to it.</span></span> <span data-ttu-id="a2d44-147">Daha fazla bilgi için [.NET Core çalışma zamanı yapılandırma ayarlarına](../run-time-config/index.md#runtimeconfigjson)bakın.</span><span class="sxs-lookup"><span data-stu-id="a2d44-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a2d44-148">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a2d44-148">Additional resources</span></span>

- [<span data-ttu-id="a2d44-149">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="a2d44-149">.NET Core application deployment</span></span>](../deploying/index.md)
