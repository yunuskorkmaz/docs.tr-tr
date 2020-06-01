---
title: .NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama
description: Yayımlama, .NET Core uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 745fb2af332afa278c78ec9baeea7230fe725c02
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241506"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a><span data-ttu-id="0acc0-103">Öğretici: Visual Studio ile .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="0acc0-103">Tutorial: Publish a .NET Core console application with Visual Studio</span></span>

<span data-ttu-id="0acc0-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0acc0-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="0acc0-105">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0acc0-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="0acc0-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0acc0-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0acc0-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="0acc0-107">Prerequisites</span></span>

- <span data-ttu-id="0acc0-108">Bu öğretici, [Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0acc0-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="0acc0-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="0acc0-109">Publish the app</span></span>

1. <span data-ttu-id="0acc0-110">Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0acc0-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="0acc0-111">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="0acc0-113">**HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="0acc0-115">**Yayımla** sayfasının **hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-115">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Visual Studio 'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="0acc0-117">**Yayımla** sayfasının **konum** sekmesinde **son**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-117">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Visual Studio yayımlama sayfası konum sekmesi](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="0acc0-119">**Yayımla** penceresinin **Yayımla** sekmesinde **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-119">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="0acc0-121">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="0acc0-121">Inspect the files</span></span>

<span data-ttu-id="0acc0-122">Yayımlama işlemi, yayımlanmış uygulamanın .NET Core çalışma zamanı yüklü olan makinede çalıştığı bir dağıtım türü olan çerçeveye bağımlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0acc0-122">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="0acc0-123">Kullanıcılar, çalıştırılabilir dosyayı çift tıklayarak veya komut isteminden komutu vererek, yayımlanan uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .</span><span class="sxs-lookup"><span data-stu-id="0acc0-123">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="0acc0-124">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0acc0-124">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="0acc0-125">**Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-125">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="0acc0-126">Proje klasöründe *bin/Release/netcoreapp 3.1/Yayımla*' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-126">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Yayımlanan dosyaları gösterme Çözüm Gezgini":::

   <span data-ttu-id="0acc0-128">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="0acc0-128">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="0acc0-129">*HelloWorld. Deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="0acc0-129">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="0acc0-130">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0acc0-130">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="0acc0-131">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0acc0-131">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="0acc0-132">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="0acc0-132">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="0acc0-133">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="0acc0-133">*HelloWorld.dll*</span></span>

      <span data-ttu-id="0acc0-134">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="0acc0-134">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="0acc0-135">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-135">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="0acc0-136">Uygulamayı çalıştırma yöntemi, .NET Core çalışma zamanının yüklü olduğu tüm platformlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="0acc0-136">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="0acc0-137">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="0acc0-137">*HelloWorld.exe*</span></span>

      <span data-ttu-id="0acc0-138">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="0acc0-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="0acc0-139">Çalıştırmak için `HelloWorld.exe` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="0acc0-140">Dosya işletim sistemine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="0acc0-140">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="0acc0-141">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="0acc0-141">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="0acc0-142">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0acc0-142">This is the debug symbols file.</span></span> <span data-ttu-id="0acc0-143">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0acc0-143">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="0acc0-144">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="0acc0-144">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="0acc0-145">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0acc0-145">This is the application's run-time configuration file.</span></span> <span data-ttu-id="0acc0-146">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0acc0-146">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="0acc0-147">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0acc0-147">You can also add configuration options to it.</span></span> <span data-ttu-id="0acc0-148">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0acc0-148">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="0acc0-149">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0acc0-149">Run the published app</span></span>

1. <span data-ttu-id="0acc0-150">**Çözüm Gezgini**, *Yayımla* klasörüne sağ tıklayın ve **tam yolu Kopyala**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-150">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="0acc0-151">Bir komut istemi açın ve *Yayımla* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="0acc0-151">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="0acc0-152">`cd`Tam yolu girin ve ardından yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0acc0-152">Enter `cd` and then paste the full path.</span></span> <span data-ttu-id="0acc0-153">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0acc0-153">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="0acc0-154">Yürütülebilir dosyayı kullanarak uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0acc0-154">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="0acc0-155">Yazın `HelloWorld.exe` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0acc0-155">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="0acc0-156">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="0acc0-156">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="0acc0-157">Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="0acc0-157">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="0acc0-158">Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0acc0-158">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="0acc0-159">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="0acc0-159">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0acc0-160">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0acc0-160">Additional resources</span></span>

- [<span data-ttu-id="0acc0-161">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="0acc0-161">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="0acc0-162">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0acc0-162">Next steps</span></span>

<span data-ttu-id="0acc0-163">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="0acc0-163">In this tutorial, you published a console app.</span></span> <span data-ttu-id="0acc0-164">Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="0acc0-164">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0acc0-165">Visual Studio’da bir .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0acc0-165">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
