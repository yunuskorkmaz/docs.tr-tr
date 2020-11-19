---
title: Visual Studio kullanarak bir .NET konsol uygulaması yayımlama
description: .NET uygulamasını çalıştırmak için gereken dosya kümesini oluşturmak için Visual Studio 'Yu nasıl kullanacağınızı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: b0c6bd85ddf86f0eb11c56f01abb74a7e9786363
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916035"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio"></a><span data-ttu-id="77642-103">Öğretici: Visual Studio kullanarak bir .NET konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="77642-103">Tutorial: Publish a .NET console application using Visual Studio</span></span>

<span data-ttu-id="77642-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77642-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="77642-105">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77642-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="77642-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="77642-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="77642-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="77642-107">Prerequisites</span></span>

- <span data-ttu-id="77642-108">Bu öğretici, [Visual Studio kullanarak bir .NET konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77642-108">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="77642-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="77642-109">Publish the app</span></span>

1. <span data-ttu-id="77642-110">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="77642-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="77642-111">[Visual Studio kullanarak .NET konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz *HelloWorld* projesini açın.</span><span class="sxs-lookup"><span data-stu-id="77642-111">Open the *HelloWorld* project that you created in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="77642-112">Visual Studio 'Nun yayın derleme yapılandırması ' nı kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="77642-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="77642-113">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="77642-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/visual-studio-toolbar-release.png" alt-text="Yayın derlemesi seçiliyken Visual Studio araç çubuğu":::

1. <span data-ttu-id="77642-115">**HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-context-menu.png" alt-text="Visual Studio Yayımla bağlam menüsü":::

1. <span data-ttu-id="77642-117">**Yayımla** sayfasının **hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/pick-publish-target.png" alt-text="Visual Studio 'da bir yayımlama hedefi seçin":::

1. <span data-ttu-id="77642-119">**Yayımla** sayfasının **belirli hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-119">On the **Specific Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/pick-specific-publish-target.png" alt-text="Visual Studio 'da belirli yayımlama hedefini seçme":::

1. <span data-ttu-id="77642-121">**Yayımla** sayfasının **konum** sekmesinde **son**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-121">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-page-loc-tab.png" alt-text="Visual Studio yayımlama sayfası konum sekmesi":::

1. <span data-ttu-id="77642-123">**Yayımla** penceresinin **Yayımla** sekmesinde **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-123">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-page.png" alt-text="Visual Studio Yayımla penceresi":::

## <a name="inspect-the-files"></a><span data-ttu-id="77642-125">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="77642-125">Inspect the files</span></span>

<span data-ttu-id="77642-126">Varsayılan olarak, yayımlama işlemi, yayımlanan uygulamanın .NET çalışma zamanının yüklü olduğu makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77642-126">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET runtime installed.</span></span> <span data-ttu-id="77642-127">Kullanıcılar, çalıştırılabilir dosyayı çift tıklayarak veya komut isteminden komutu vererek, yayımlanan uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .</span><span class="sxs-lookup"><span data-stu-id="77642-127">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="77642-128">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="77642-128">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="77642-129">**Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-129">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="77642-130">Proje klasöründe, *bin/Release/net 5.0/Publish*' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="77642-130">In the project folder, expand *bin/Release/net5.0/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Yayımlanan dosyaları gösterme Çözüm Gezgini":::

   <span data-ttu-id="77642-132">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="77642-132">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="77642-133">*ÜzerindeHelloWorld.deps.js*</span><span class="sxs-lookup"><span data-stu-id="77642-133">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="77642-134">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="77642-134">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="77642-135">Uygulamayı çalıştırmak için gereken .NET bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77642-135">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="77642-136">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="77642-136">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="77642-137">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="77642-137">*HelloWorld.dll*</span></span>

      <span data-ttu-id="77642-138">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="77642-138">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="77642-139">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="77642-139">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="77642-140">Uygulamayı çalıştırma yöntemi, .NET çalışma zamanının yüklü olduğu tüm platformlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="77642-140">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

   * <span data-ttu-id="77642-141">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="77642-141">*HelloWorld.exe*</span></span>

      <span data-ttu-id="77642-142">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="77642-142">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="77642-143">Çalıştırmak için `HelloWorld.exe` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="77642-143">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="77642-144">Dosya işletim sistemine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="77642-144">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="77642-145">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="77642-145">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="77642-146">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="77642-146">This is the debug symbols file.</span></span> <span data-ttu-id="77642-147">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="77642-147">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="77642-148">*ÜzerindeHelloWorld.runtimeconfig.js*</span><span class="sxs-lookup"><span data-stu-id="77642-148">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="77642-149">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="77642-149">This is the application's run-time configuration file.</span></span> <span data-ttu-id="77642-150">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77642-150">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="77642-151">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77642-151">You can also add configuration options to it.</span></span> <span data-ttu-id="77642-152">Daha fazla bilgi için bkz. [.NET çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="77642-152">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="77642-153">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="77642-153">Run the published app</span></span>

1. <span data-ttu-id="77642-154">**Çözüm Gezgini**, *Yayımla* klasörüne sağ tıklayın ve **tam yolu Kopyala**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="77642-154">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="77642-155">Bir komut istemi açın ve *Yayımla* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="77642-155">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="77642-156">Bunu yapmak için `cd` tam yolu girin ve ardından yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="77642-156">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="77642-157">Örnek:</span><span class="sxs-lookup"><span data-stu-id="77642-157">For example:</span></span>

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="77642-158">Yürütülebilir dosyayı kullanarak uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="77642-158">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="77642-159">Yazın `HelloWorld.exe` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="77642-159">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="77642-160">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="77642-160">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="77642-161">Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="77642-161">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="77642-162">Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="77642-162">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="77642-163">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="77642-163">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="77642-164">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="77642-164">Additional resources</span></span>

- [<span data-ttu-id="77642-165">.NET uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="77642-165">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="77642-166">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="77642-166">Next steps</span></span>

<span data-ttu-id="77642-167">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="77642-167">In this tutorial, you published a console app.</span></span> <span data-ttu-id="77642-168">Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="77642-168">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77642-169">Visual Studio kullanarak .NET sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="77642-169">Create a .NET class library using Visual Studio</span></span>](library-with-visual-studio.md)
