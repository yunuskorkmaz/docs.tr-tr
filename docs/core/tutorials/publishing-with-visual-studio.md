---
title: .NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156640"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="d2d46-103">.NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama</span><span class="sxs-lookup"><span data-stu-id="d2d46-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="d2d46-104">[Visual Studio 'da .NET Core ile Merhaba Dünya uygulaması oluşturma](with-visual-studio.md)bölümünde, bir Merhaba Dünya konsol uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d2d46-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="d2d46-105">[Visual Studio ile Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md)yaparken, Visual Studio hata ayıklayıcısını kullanarak test edersiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d46-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="d2d46-106">Artık beklendiği gibi çalıştığından emin olduğunuza göre, diğer kullanıcıların çalıştırabilmesi için onu yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d46-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="d2d46-107">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2d46-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="d2d46-108">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d2d46-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="d2d46-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="d2d46-109">Publish the app</span></span>

1. <span data-ttu-id="d2d46-110">Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d2d46-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="d2d46-111">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="d2d46-113">**HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="d2d46-114">(Ana **Yapı** menüsünden **HelloWorld Yayımla** ' yı da seçebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="d2d46-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="d2d46-116">**Bir yayımlama hedefi** seçin sayfasında **klasör**' i seçin ve ardından **Profil oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Visual Studio 'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="d2d46-118">**Yayımla** sayfasında **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-118">On the **Publish** page, select **Publish**.</span></span>

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="d2d46-120">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="d2d46-120">Inspect the files</span></span>

<span data-ttu-id="d2d46-121">Yayımlama işlemi, yayımlanmış uygulamanın sistemde .NET Core tarafından desteklenen herhangi bir platformda çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2d46-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="d2d46-122">Kullanıcılar çalıştırılabilir dosyayı çift tıklayarak veya bir komut isteminden `dotnet HelloWorld.dll` komutunu yayımlayarak, yayımlanan uygulamayı çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="d2d46-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="d2d46-123">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d2d46-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="d2d46-124">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d2d46-124">Open a command prompt.</span></span>

   <span data-ttu-id="d2d46-125">Komut istemi açmak için bir yol, Windows görev çubuğundaki arama kutusuna **komut istemi** (veya Short için **cmd** ) girmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="d2d46-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="d2d46-126">Masaüstü uygulamasını **komut istemi** ' ni seçin veya arama sonuçlarında zaten seçiliyse **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2d46-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="d2d46-127">Uygulamanın proje dizininin *Bin\release\netcoreapp3.1\publish* alt dizininde yayınlanan uygulamaya gidin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Yayımlanan dosyaları gösteren konsol penceresi](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="d2d46-129">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="d2d46-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="d2d46-130">*HelloWorld. Deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="d2d46-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="d2d46-131">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d2d46-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="d2d46-132">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2d46-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="d2d46-133">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="d2d46-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="d2d46-134">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="d2d46-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="d2d46-135">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d2d46-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="d2d46-136">Bu dinamik bağlantı kitaplığını yürütmek için, komut istemine `dotnet HelloWorld.dll` girin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="d2d46-137">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="d2d46-137">*HelloWorld.exe*</span></span>

         <span data-ttu-id="d2d46-138">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d2d46-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="d2d46-139">Çalıştırmak için, komut istemine `HelloWorld.exe` girin.</span><span class="sxs-lookup"><span data-stu-id="d2d46-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="d2d46-140">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="d2d46-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="d2d46-141">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d2d46-141">This is the debug symbols file.</span></span> <span data-ttu-id="d2d46-142">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2d46-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="d2d46-143">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="d2d46-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="d2d46-144">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d2d46-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="d2d46-145">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2d46-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="d2d46-146">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d46-146">You can also add configuration options to it.</span></span> <span data-ttu-id="d2d46-147">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d2d46-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d2d46-148">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d2d46-148">Additional resources</span></span>

- [<span data-ttu-id="d2d46-149">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d2d46-149">.NET Core application deployment</span></span>](../deploying/index.md)
