---
title: Visual Studio Code bir .NET Core Merhaba Dünya uygulaması yayımlama
description: Yayımlama, .NET Core uygulamasını çalıştırmak için gereken dosya kümesini oluşturur.
ms.date: 05/28/2020
ms.openlocfilehash: b49b12bf41e3ea7be8dbc459eb7d9b1fbef25790
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84246684"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio-code"></a><span data-ttu-id="1ad19-103">Öğretici: Visual Studio Code bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="1ad19-103">Tutorial: Publish a .NET Core console application with Visual Studio Code</span></span>

<span data-ttu-id="1ad19-104">Bu öğreticide, diğer kullanıcıların çalışması için bir konsol uygulamasının nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ad19-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="1ad19-105">Yayımlama, bir uygulamayı çalıştırmak için gereken dosyalar kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ad19-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="1ad19-106">Dosyaları dağıtmak için, onları hedef makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="1ad19-107">.NET Core CLI, uygulamayı yayımlamak için kullanılır, bu nedenle bu öğreticiyi Visual Studio Code dışında bir kod düzenleyicisiyle takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad19-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ad19-108">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="1ad19-108">Prerequisites</span></span>

- <span data-ttu-id="1ad19-109">Bu öğretici, [Visual Studio Code bir .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ad19-109">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="1ad19-110">Uygulamayı yayımlama</span><span class="sxs-lookup"><span data-stu-id="1ad19-110">Publish the app</span></span>

1. <span data-ttu-id="1ad19-111">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="1ad19-112">[Visual Studio Code .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz *HelloWorld* proje klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="1ad19-113">Ana menüden **Görünüm**  >  **terminali** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="1ad19-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="1ad19-114">Terminal *HelloWorld* klasöründe açılır.</span><span class="sxs-lookup"><span data-stu-id="1ad19-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="1ad19-115">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1ad19-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="1ad19-116">Varsayılan derleme yapılandırması *hata ayıklayın*, bu nedenle bu komut *yayın* derleme yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ad19-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="1ad19-117">Yayın derleme yapılandırmasından alınan çıktıda minimum sembolik hata ayıklama bilgileri bulunur ve tamamen iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1ad19-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="1ad19-118">Komut çıktısı aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="1ad19-118">The command output is similar to the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="1ad19-119">Dosyaları inceleyin</span><span class="sxs-lookup"><span data-stu-id="1ad19-119">Inspect the files</span></span>

<span data-ttu-id="1ad19-120">Varsayılan olarak, yayımlama işlemi, yayımlanan uygulamanın .NET Core çalışma zamanı yüklü bir makinede çalıştığı bir dağıtım türü olan çerçeveye bağlı bir dağıtım oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ad19-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="1ad19-121">Yayımlanan uygulamayı çalıştırmak için yürütülebilir dosyayı kullanabilir veya komutu `dotnet HelloWorld.dll` komut isteminden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad19-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="1ad19-122">Aşağıdaki adımlarda, yayımlama işlemi tarafından oluşturulan dosyalara bakacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1ad19-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="1ad19-123">Sol gezinti çubuğunda **Gezgin** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1ad19-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="1ad19-124">*Bin/Release/netcoreapp 3.1/Yayımla*' yı genişletin.</span><span class="sxs-lookup"><span data-stu-id="1ad19-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Yayımlanan dosyaları gösteren gezgin":::

   <span data-ttu-id="1ad19-126">Görüntüde gösterildiği gibi, yayımlanan çıktı aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="1ad19-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="1ad19-127">*HelloWorld. Deps. JSON*</span><span class="sxs-lookup"><span data-stu-id="1ad19-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="1ad19-128">Bu, uygulamanın çalışma zamanı bağımlılıkları dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ad19-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="1ad19-129">Uygulamayı çalıştırmak için gereken .NET Core bileşenlerini ve kitaplıklarını (uygulamanızı içeren dinamik bağlantı kitaplığı dahil) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ad19-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="1ad19-130">Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="1ad19-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="1ad19-131">*HelloWorld. dll*</span><span class="sxs-lookup"><span data-stu-id="1ad19-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="1ad19-132">Bu, uygulamanın [çerçeveye bağımlı dağıtım](../deploying/deploy-with-cli.md#framework-dependent-deployment) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1ad19-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="1ad19-133">Bu dinamik bağlantı kitaplığını yürütmek için `dotnet HelloWorld.dll` bir komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="1ad19-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="1ad19-134">Uygulamayı çalıştırma yöntemi, .NET Core çalışma zamanının yüklü olduğu tüm platformlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="1ad19-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="1ad19-135">*HelloWorld. exe* (Linux üzerinde*HelloWorld* , MacOS üzerinde oluşturulmaz.)</span><span class="sxs-lookup"><span data-stu-id="1ad19-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="1ad19-136">Bu, uygulamanın [çerçeveye bağımlı yürütülebilir](../deploying/deploy-with-cli.md#framework-dependent-executable) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1ad19-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="1ad19-137">Dosya işletim sistemine özgüdür.</span><span class="sxs-lookup"><span data-stu-id="1ad19-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="1ad19-138">*HelloWorld. pdb* (dağıtım için isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="1ad19-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="1ad19-139">Bu, hata ayıklama sembolleri dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ad19-139">This is the debug symbols file.</span></span> <span data-ttu-id="1ad19-140">Bu dosyayı uygulamanızla birlikte dağıtmanız gerekmez, ancak uygulamanızın yayımlanan sürümünde hata ayıklaması yapmanız gereken bir olaya kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ad19-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="1ad19-141">*HelloWorld. runtimeconfig. JSON*</span><span class="sxs-lookup"><span data-stu-id="1ad19-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="1ad19-142">Bu, uygulamanın çalışma zamanı yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ad19-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="1ad19-143">Uygulamanızın üzerinde çalışmak üzere oluşturulduğu .NET Core sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ad19-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="1ad19-144">Ayrıca, buna yapılandırma seçenekleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad19-144">You can also add configuration options to it.</span></span> <span data-ttu-id="1ad19-145">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="1ad19-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="1ad19-146">Yayımlanan uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1ad19-146">Run the published app</span></span>

1. <span data-ttu-id="1ad19-147">**Gezgin**'de *Yayımla* klasörüne sağ tıklayın (veya MacOS 'ta <kbd>CTRL</kbd>+ tıklama) ve **terminalde aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1ad19-147">In **Explorer**, right-click the *publish* folder (or <kbd>Ctrl</kbd>+click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Terminalde aç 'ı gösteren bağlam menüsü":::

1. <span data-ttu-id="1ad19-149">Windows veya Linux 'ta, yürütülebilir dosyayı kullanarak uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="1ad19-150">Windows 'ta yazın `.\HelloWorld.exe` ve ENTER tuşuna <kbd>Enter</kbd>basın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="1ad19-151">Linux 'ta yazın `./HelloWorld` ve ENTER tuşuna <kbd>Enter</kbd>basın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="1ad19-152">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="1ad19-153">Herhangi bir platformda, komutunu kullanarak uygulamayı çalıştırın [`dotnet`](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="1ad19-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="1ad19-154">Yazın `dotnet HelloWorld.dll` ve ENTER <kbd>Enter</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="1ad19-155">İstemine yanıt olarak bir ad girin ve çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="1ad19-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1ad19-156">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1ad19-156">Additional resources</span></span>

- [<span data-ttu-id="1ad19-157">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="1ad19-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="1ad19-158">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1ad19-158">Next steps</span></span>

<span data-ttu-id="1ad19-159">Bu öğreticide bir konsol uygulaması yayımladınız.</span><span class="sxs-lookup"><span data-stu-id="1ad19-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="1ad19-160">Kitaplıklar oluşturmayı öğrenmek için bkz. [.NET Core CLI kitaplıklar geliştirme](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="1ad19-160">To learn how to build libraries, see [Develop libraries with the .NET Core CLI](libraries.md).</span></span>

<!--In the next tutorial, you create a class library.

> [!div class="nextstepaction"]
> [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md)
-->
