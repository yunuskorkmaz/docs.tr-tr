---
title: Visual Studio Code kullanarak bir .NET Core konsol uygulaması yayımlama
description: Yayımlama, .NET Core uygulamasını çalıştırmak için gereken dosya kümesini oluşturur.
ms.date: 07/04/2020
ms.openlocfilehash: 79c69546b79de3d702fb4bb6550e615d8d59fa74
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495531"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="d1178-103">Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="d1178-103">Tutorial: Publish a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="d1178-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1178-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="d1178-105">Yayımlama, bir uygulamayı çalıştırmak için gereken dosyalar kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1178-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="d1178-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d1178-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="d1178-107">.NET Core CLI, uygulamayı yayımlamak için kullanılır, bu nedenle bu öğreticiyi Visual Studio Code dışında bir kod düzenleyicisiyle takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1178-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1178-108">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="d1178-108">Prerequisites</span></span>

- <span data-ttu-id="d1178-109">Bu öğretici, [Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1178-109">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="d1178-110">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="d1178-110">Publish the app</span></span>

1. <span data-ttu-id="d1178-111">Visual Studio Code’u başlatma.</span><span class="sxs-lookup"><span data-stu-id="d1178-111">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="d1178-112">[Visual Studio Code kullanarak .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz *HelloWorld* proje klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="d1178-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="d1178-113">Ana menüden **Görünüm**  >  **terminali** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="d1178-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="d1178-114">Terminal *HelloWorld* klasöründe açılır.</span><span class="sxs-lookup"><span data-stu-id="d1178-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="d1178-115">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d1178-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="d1178-116">Varsayılan derleme yapılandırması *hata ayıklayın*, bu nedenle bu komut *yayın* derleme yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1178-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="d1178-117">Yayın derleme yapılandırmasından alınan çıktıda minimum sembolik hata ayıklama bilgileri bulunur ve tamamen iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1178-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="d1178-118">Komut çıktısı aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="d1178-118">The command output is similar to the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="d1178-119">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="d1178-119">Inspect the files</span></span>

<span data-ttu-id="d1178-120">Varsayılan olarak, yayımlama işlemi, yayımlanan uygulamanın .NET Core çalışma zamanı yüklü bir makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1178-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="d1178-121">Yayımlanan uygulamayı çalıştırmak için yürütülebilir dosyayı kullanabilir veya komutu `dotnet HelloWorld.dll` komut isteminden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1178-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="d1178-122">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d1178-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="d1178-123">Sol gezinti çubuğunda **Gezgin** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d1178-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="d1178-124">*Bin/Release/netcoreapp 3.1/Yayımla*' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="d1178-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Yayımlanan dosyaları gösteren gezgin":::

   <span data-ttu-id="d1178-126">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="d1178-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="d1178-127">\* ÜzerindeHelloWorld.deps.js\*</span><span class="sxs-lookup"><span data-stu-id="d1178-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="d1178-128">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d1178-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="d1178-129">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1178-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="d1178-130">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="d1178-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="d1178-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="d1178-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="d1178-132">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d1178-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="d1178-133">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="d1178-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="d1178-134">Uygulamayı çalıştırma yöntemi, .NET Core çalışma zamanının yüklü olduğu tüm platformlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="d1178-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="d1178-135">*HelloWorld.exe* (Linux üzerinde*HelloWorld* , MacOS 'ta oluşturulmaz.)</span><span class="sxs-lookup"><span data-stu-id="d1178-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="d1178-136">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d1178-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="d1178-137">Dosya işletim sistemine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="d1178-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="d1178-138">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="d1178-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="d1178-139">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d1178-139">This is the debug symbols file.</span></span> <span data-ttu-id="d1178-140">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1178-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="d1178-141">\* ÜzerindeHelloWorld.runtimeconfig.js\*</span><span class="sxs-lookup"><span data-stu-id="d1178-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="d1178-142">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d1178-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="d1178-143">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1178-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="d1178-144">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1178-144">You can also add configuration options to it.</span></span> <span data-ttu-id="d1178-145">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="d1178-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="d1178-146">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d1178-146">Run the published app</span></span>

1. <span data-ttu-id="d1178-147">**Gezgin**'de *Yayımla* klasörüne sağ tıklayın (MacOS ' a<kbd>CTRL tuşunu basılı</kbd>olarak) ve **terminalde aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d1178-147">In **Explorer**, right-click the *publish* folder (<kbd>Ctrl</kbd>-click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Terminalde aç 'ı gösteren bağlam menüsü":::

1. <span data-ttu-id="d1178-149">Windows veya Linux 'ta, yürütülebilir dosyayı kullanarak uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d1178-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="d1178-150">Windows 'ta yazın `.\HelloWorld.exe` ve ENTER tuşuna <kbd>Enter</kbd>basın.</span><span class="sxs-lookup"><span data-stu-id="d1178-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d1178-151">Linux 'ta yazın `./HelloWorld` ve ENTER tuşuna <kbd>Enter</kbd>basın.</span><span class="sxs-lookup"><span data-stu-id="d1178-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d1178-152">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="d1178-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="d1178-153">Herhangi bir platformda, komutunu kullanarak uygulamayı çalıştırın  [`dotnet`](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="d1178-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="d1178-154">Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d1178-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="d1178-155">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="d1178-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d1178-156">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d1178-156">Additional resources</span></span>

- [<span data-ttu-id="d1178-157">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d1178-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="d1178-158">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d1178-158">Next steps</span></span>

<span data-ttu-id="d1178-159">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="d1178-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="d1178-160">Sonraki öğreticide, bir sınıf kitaplığı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="d1178-160">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1178-161">Visual Studio Code kullanarak .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1178-161">Create a .NET Standard library using Visual Studio Code</span></span>](library-with-visual-studio-code.md)
