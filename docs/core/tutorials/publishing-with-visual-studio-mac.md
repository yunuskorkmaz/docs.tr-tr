---
title: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama
description: Yayımlama, .NET Core uygulamasını çalıştırmak için gereken dosya kümesini oluşturur.
ms.date: 06/08/2020
ms.openlocfilehash: 38b656ac919dfb8b710a97c5d7fc63479e3fa367
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811411"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="c9844-103">Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="c9844-103">Tutorial: Publish a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="c9844-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9844-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="c9844-105">Yayımlama, uygulamanızı çalıştırmak için gereken dosya kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9844-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="c9844-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c9844-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c9844-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="c9844-107">Prerequisites</span></span>

- <span data-ttu-id="c9844-108">Bu öğretici, [Mac için Visual Studio bir .NET Core konsol uygulaması oluşturma](with-visual-studio-mac.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9844-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="c9844-109">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="c9844-109">Publish the app</span></span>

1. <span data-ttu-id="c9844-110">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="c9844-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="c9844-111">[Mac için Visual Studio .NET Core konsol uygulaması oluşturma](with-visual-studio-mac.md)bölümünde oluşturduğunuz HelloWorld projesini açın.</span><span class="sxs-lookup"><span data-stu-id="c9844-111">Open the HelloWorld project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="c9844-112">Visual Studio 'nun uygulamanızın yayın sürümünü oluşturmakta olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9844-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="c9844-113">Gerekirse, araç çubuğundaki derleme yapılandırma ayarını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c9844-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Yayın derlemesi seçiliyken Visual Studio araç çubuğu":::

1. <span data-ttu-id="c9844-115">Ana menüden **derleme**Yayımla klasörü ' ne tıklayın.  >  **..**</span><span class="sxs-lookup"><span data-stu-id="c9844-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio Yayımla bağlam menüsü":::

1. <span data-ttu-id="c9844-117">**Klasöre Yayımla** Iletişim kutusunda **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c9844-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio klasöre Yayımla iletişim kutusu":::

   <span data-ttu-id="c9844-119">Oluşturulan dosyaları gösteren Yayımla klasörü açılır.</span><span class="sxs-lookup"><span data-stu-id="c9844-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="klasörü Yayımla":::

1. <span data-ttu-id="c9844-121">Dişli simgesini seçin ve bağlam menüsünden **"Yayımla" adını yol adı olarak Kopyala** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c9844-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Yayımlama klasörünün yolunu Kopyala":::

## <a name="inspect-the-files"></a><span data-ttu-id="c9844-123">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="c9844-123">Inspect the files</span></span>

<span data-ttu-id="c9844-124">Yayımlama işlemi, yayımlanan uygulamanın .NET Core çalışma zamanı yüklü bir makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9844-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="c9844-125">Kullanıcılar, komut isteminden komutunu çalıştırarak yayımlanmış uygulamayı çalıştırabilir `dotnet HelloWorld.dll` .</span><span class="sxs-lookup"><span data-stu-id="c9844-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="c9844-126">Önceki görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="c9844-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="c9844-127">\* ÜzerindeHelloWorld.deps.js\*</span><span class="sxs-lookup"><span data-stu-id="c9844-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="c9844-128">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9844-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="c9844-129">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9844-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="c9844-130">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="c9844-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="c9844-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="c9844-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="c9844-132">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="c9844-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="c9844-133">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="c9844-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="c9844-134">Uygulamayı çalıştırma yöntemi, .NET Core çalışma zamanının yüklü olduğu tüm platformlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="c9844-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

* <span data-ttu-id="c9844-135">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c9844-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="c9844-136">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9844-136">This is the debug symbols file.</span></span> <span data-ttu-id="c9844-137">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9844-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="c9844-138">\* ÜzerindeHelloWorld.runtimeconfig.js\*</span><span class="sxs-lookup"><span data-stu-id="c9844-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="c9844-139">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9844-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="c9844-140">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9844-140">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="c9844-141">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9844-141">You can also add configuration options to it.</span></span> <span data-ttu-id="c9844-142">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="c9844-142">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="c9844-143">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c9844-143">Run the published app</span></span>

1. <span data-ttu-id="c9844-144">Bir Terminal açın ve *Yayımla* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="c9844-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="c9844-145">Bunu yapmak için, `cd` daha önce kopyaladığınız yolu girin ve yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9844-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="c9844-146">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c9844-146">For example:</span></span>

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. <span data-ttu-id="c9844-147">Şu komutu kullanarak uygulamayı çalıştırın `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="c9844-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="c9844-148">Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c9844-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="c9844-149">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="c9844-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c9844-150">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c9844-150">Additional resources</span></span>

- [<span data-ttu-id="c9844-151">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="c9844-151">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="c9844-152">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c9844-152">Next steps</span></span>

<span data-ttu-id="c9844-153">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="c9844-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="c9844-154">Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c9844-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c9844-155">Mac için Visual Studio 'da .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9844-155">Create a .NET Standard library in Visual Studio for mac</span></span>](library-with-visual-studio-mac.md)
