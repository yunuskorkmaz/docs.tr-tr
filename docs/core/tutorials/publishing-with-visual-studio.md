---
title: Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama
description: Yayımlama, .NET Core uygulamasını çalıştırmak için gereken dosya kümesini oluşturur.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 44646a307d230db395b55b9dec5acfd168605940
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701290"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="f2bcd-103">Öğretici: Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="f2bcd-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="f2bcd-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="f2bcd-105">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="f2bcd-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2bcd-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f2bcd-107">Prerequisites</span></span>

- <span data-ttu-id="f2bcd-108">Bu öğretici, [Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="f2bcd-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="f2bcd-109">Publish the app</span></span>

1. <span data-ttu-id="f2bcd-110">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="f2bcd-111">[Visual Studio 'da .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz *HelloWorld* projesini açın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="f2bcd-112">Visual Studio 'Nun yayın derleme yapılandırması ' nı kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="f2bcd-113">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Yayın derlemesi seçiliyken Visual Studio araç çubuğu](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="f2bcd-115">**HelloWorld** projesine (HelloWorld çözümüne değil) sağ tıklayın ve menüden **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Visual Studio Yayımla bağlam menüsü](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="f2bcd-117">**Yayımla** sayfasının **hedef** sekmesinde **klasör**' i seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Visual Studio 'da bir yayımlama hedefi seçin](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="f2bcd-119">**Yayımla** sayfasının **konum** sekmesinde **son**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Visual Studio yayımlama sayfası konum sekmesi](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="f2bcd-121">**Yayımla** penceresinin **Yayımla** sekmesinde **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Visual Studio Yayımla penceresi](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="f2bcd-123">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="f2bcd-123">Inspect the files</span></span>

<span data-ttu-id="f2bcd-124">Varsayılan olarak, yayımlama işlemi, yayımlanan uygulamanın .NET Core çalışma zamanının yüklü olduğu makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="f2bcd-125">Kullanıcılar, çalıştırılabilir dosyayı çift tıklayarak veya komut isteminden komutu vererek, yayımlanan uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .</span><span class="sxs-lookup"><span data-stu-id="f2bcd-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="f2bcd-126">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="f2bcd-127">**Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="f2bcd-128">Proje klasöründe *bin/Release/netcoreapp 3.1/Yayımla*' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Yayımlanan dosyaları gösterme Çözüm Gezgini":::

   <span data-ttu-id="f2bcd-130">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="f2bcd-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="f2bcd-131">*ÜzerindeHelloWorld.deps.js*</span><span class="sxs-lookup"><span data-stu-id="f2bcd-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="f2bcd-132">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="f2bcd-133">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="f2bcd-134">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="f2bcd-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="f2bcd-135">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="f2bcd-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="f2bcd-136">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="f2bcd-137">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="f2bcd-138">Uygulamayı çalıştırma yöntemi, .NET Core çalışma zamanının yüklü olduğu tüm platformlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="f2bcd-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="f2bcd-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="f2bcd-140">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="f2bcd-141">Çalıştırmak için `HelloWorld.exe` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="f2bcd-142">Dosya işletim sistemine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="f2bcd-143">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f2bcd-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="f2bcd-144">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-144">This is the debug symbols file.</span></span> <span data-ttu-id="f2bcd-145">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="f2bcd-146">*ÜzerindeHelloWorld.runtimeconfig.js*</span><span class="sxs-lookup"><span data-stu-id="f2bcd-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="f2bcd-147">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="f2bcd-148">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="f2bcd-149">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-149">You can also add configuration options to it.</span></span> <span data-ttu-id="f2bcd-150">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f2bcd-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="f2bcd-151">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f2bcd-151">Run the published app</span></span>

1. <span data-ttu-id="f2bcd-152">**Çözüm Gezgini**, *Yayımla* klasörüne sağ tıklayın ve **tam yolu Kopyala**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="f2bcd-153">Bir komut istemi açın ve *Yayımla* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="f2bcd-154">Bunu yapmak için `cd` tam yolu girin ve ardından yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="f2bcd-155">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f2bcd-155">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="f2bcd-156">Yürütülebilir dosyayı kullanarak uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f2bcd-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="f2bcd-157">Yazın `HelloWorld.exe` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f2bcd-158">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="f2bcd-159">Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="f2bcd-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="f2bcd-160">Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f2bcd-161">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f2bcd-162">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f2bcd-162">Additional resources</span></span>

- [<span data-ttu-id="f2bcd-163">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="f2bcd-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="f2bcd-164">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f2bcd-164">Next steps</span></span>

<span data-ttu-id="f2bcd-165">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="f2bcd-166">Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f2bcd-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2bcd-167">Visual Studio’da bir .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2bcd-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
