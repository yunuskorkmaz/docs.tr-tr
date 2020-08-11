---
title: "Öğretici: .NET Core küresel aracı 'nı yükleyip kullanma"
description: .NET aracını genel araç olarak yüklemeyi ve kullanmayı öğrenin.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 28e34a4e5a0344e314c5d23228c1af5839db991c
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062775"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="401ab-103">Öğretici: .NET Core CLI kullanarak .NET Core küresel aracı 'nı yükleyip kullanın</span><span class="sxs-lookup"><span data-stu-id="401ab-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="401ab-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="401ab-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="401ab-105">Bu öğreticide, genel bir aracın nasıl yükleneceği ve kullanılacağı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="401ab-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="401ab-106">[Bu serinin ilk öğreticisinde](global-tools-how-to-create.md)oluşturduğunuz bir aracı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="401ab-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="401ab-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="401ab-107">Prerequisites</span></span>

* <span data-ttu-id="401ab-108">[Bu serinin ilk öğreticisini](global-tools-how-to-create.md)doldurun.</span><span class="sxs-lookup"><span data-stu-id="401ab-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="401ab-109">Aracı genel araç olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="401ab-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="401ab-110">*Microsoft. botsay* proje klasöründeki [DotNet aracı install](dotnet-tool-install.md) komutunu çalıştırarak aracı paketten çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="401ab-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="401ab-111">`--global`Parametresi, .NET Core CLI araç ikililerini otomatik olarak PATH ortam değişkenine eklenen varsayılan bir konuma yüklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="401ab-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="401ab-112">`--add-source`Parametresi, .NET Core CLI NuGet paketleri için ek bir kaynak akışı olarak *./nupkg* dizinini geçici olarak kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="401ab-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="401ab-113">Paketinize, Nuget.org sitesinde değil, yalnızca *./nupkg* dizininde bulunduğunuzdan emin olmak için benzersiz bir ad verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="401ab-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="401ab-114">Çıktı, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösterir:</span><span class="sxs-lookup"><span data-stu-id="401ab-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="401ab-115">Aracı çağır:</span><span class="sxs-lookup"><span data-stu-id="401ab-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="401ab-116">Bu komut başarısız olursa, yolu yenilemek için yeni bir Terminal açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="401ab-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="401ab-117">[DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="401ab-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="401ab-118">Aracı özel bir konumda yüklü olan küresel bir araç olarak kullanın</span><span class="sxs-lookup"><span data-stu-id="401ab-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="401ab-119">Aracı paketten yükler.</span><span class="sxs-lookup"><span data-stu-id="401ab-119">Install the tool from the package.</span></span>

   <span data-ttu-id="401ab-120">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="401ab-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="401ab-121">Linux veya macOS 'ta:</span><span class="sxs-lookup"><span data-stu-id="401ab-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="401ab-122">`--tool-path`Parametresi, .NET Core CLI araç ikililerini belirtilen konuma yüklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="401ab-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="401ab-123">Dizin yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="401ab-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="401ab-124">Bu dizin, PATH ortam değişkenine otomatik olarak eklenmez.</span><span class="sxs-lookup"><span data-stu-id="401ab-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="401ab-125">Çıktı, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösterir:</span><span class="sxs-lookup"><span data-stu-id="401ab-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="401ab-126">Aracı çağır:</span><span class="sxs-lookup"><span data-stu-id="401ab-126">Invoke the tool:</span></span>

   <span data-ttu-id="401ab-127">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="401ab-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="401ab-128">Linux veya macOS 'ta:</span><span class="sxs-lookup"><span data-stu-id="401ab-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="401ab-129">[DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="401ab-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="401ab-130">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="401ab-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="401ab-131">Linux veya macOS 'ta:</span><span class="sxs-lookup"><span data-stu-id="401ab-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="401ab-132">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="401ab-132">Troubleshoot</span></span>

<span data-ttu-id="401ab-133">Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET Core araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="401ab-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="401ab-134">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="401ab-134">Next steps</span></span>

<span data-ttu-id="401ab-135">Bu öğreticide, bir aracı bir genel araç olarak yüklediniz ve kullandınız.</span><span class="sxs-lookup"><span data-stu-id="401ab-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="401ab-136">Aynı aracı yerel bir araç olarak yüklemek ve kullanmak için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="401ab-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="401ab-137">Yerel araçları yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="401ab-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
