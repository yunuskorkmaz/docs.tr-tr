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
ms.openlocfilehash: e4ef8c12f3e52faa7cf09058a98abae65b0dcfce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005131"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a><span data-ttu-id="ce981-103">Öğretici: Visual Studio ile .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="ce981-103">Tutorial: Publish a .NET Core console application with Visual Studio</span></span>

<span data-ttu-id="ce981-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ce981-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="ce981-105">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce981-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="ce981-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ce981-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce981-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="ce981-107">Prerequisites</span></span>

- <span data-ttu-id="ce981-108">Bu öğretici, [Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce981-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="ce981-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="ce981-109">Publish the app</span></span>

1. <span data-ttu-id="ce981-110">Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ce981-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="ce981-111">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce981-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="ce981-113">**HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ce981-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="ce981-115">**Yayımla** sayfasının **hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ce981-115">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Visual Studio 'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="ce981-117">**Yayımla** sayfasının **konum** sekmesinde **son**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="ce981-117">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Visual Studio yayımlama sayfası konum sekmesi](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="ce981-119">**Yayımla** penceresinin **Yayımla** sekmesinde **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ce981-119">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="ce981-121">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="ce981-121">Inspect the files</span></span>

<span data-ttu-id="ce981-122">Yayımlama işlemi, yayımlanmış uygulamanın .NET Core çalışma zamanı yüklü olan makinede çalıştığı bir dağıtım türü olan çerçeveye bağımlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce981-122">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="ce981-123">Kullanıcılar, çalıştırılabilir dosyayı çift tıklayarak veya komut isteminden komutu vererek, yayımlanan uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .</span><span class="sxs-lookup"><span data-stu-id="ce981-123">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="ce981-124">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ce981-124">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="ce981-125">**Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ce981-125">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="ce981-126">Proje klasöründe *bin/Release/netcoreapp 3.1/Yayımla*' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="ce981-126">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Yayımlanan dosyaları gösterme Çözüm Gezgini":::

   <span data-ttu-id="ce981-128">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="ce981-128">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="ce981-129">*HelloWorld. Deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="ce981-129">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="ce981-130">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce981-130">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="ce981-131">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce981-131">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="ce981-132">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="ce981-132">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="ce981-133">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="ce981-133">*HelloWorld.dll*</span></span>

         <span data-ttu-id="ce981-134">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="ce981-134">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="ce981-135">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="ce981-135">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="ce981-136">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="ce981-136">*HelloWorld.exe*</span></span>

         <span data-ttu-id="ce981-137">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="ce981-137">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="ce981-138">Çalıştırmak için `HelloWorld.exe` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="ce981-138">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="ce981-139">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="ce981-139">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="ce981-140">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce981-140">This is the debug symbols file.</span></span> <span data-ttu-id="ce981-141">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce981-141">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="ce981-142">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="ce981-142">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="ce981-143">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce981-143">This is the application's run-time configuration file.</span></span> <span data-ttu-id="ce981-144">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce981-144">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="ce981-145">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce981-145">You can also add configuration options to it.</span></span> <span data-ttu-id="ce981-146">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="ce981-146">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="ce981-147">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ce981-147">Run the published app</span></span>

1. <span data-ttu-id="ce981-148">**Çözüm Gezgini**, *Yayımla* klasörüne sağ tıklayın ve **tam yolu Kopyala**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ce981-148">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="ce981-149">Bir komut istemi açın ve *Yayımla* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="ce981-149">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="ce981-150">`cd`Tam yolu girin ve ardından yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ce981-150">Enter `cd` and then paste the full path.</span></span> <span data-ttu-id="ce981-151">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ce981-151">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="ce981-152">Yürütülebilir dosyayı kullanarak uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ce981-152">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="ce981-153">Yazın `HelloWorld.exe` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ce981-153">Enter `HelloWorld.exe` and press Enter.</span></span>

   1. <span data-ttu-id="ce981-154">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="ce981-154">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="ce981-155">Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="ce981-155">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="ce981-156">Yazın `dotnet HelloWorld.dll` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ce981-156">Enter `dotnet HelloWorld.dll` and press Enter.</span></span>

   1. <span data-ttu-id="ce981-157">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="ce981-157">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ce981-158">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ce981-158">Additional resources</span></span>

- [<span data-ttu-id="ce981-159">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="ce981-159">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="ce981-160">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ce981-160">Next steps</span></span>

<span data-ttu-id="ce981-161">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="ce981-161">In this tutorial, you published a console app.</span></span> <span data-ttu-id="ce981-162">Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ce981-162">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce981-163">Visual Studio’da bir .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce981-163">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
