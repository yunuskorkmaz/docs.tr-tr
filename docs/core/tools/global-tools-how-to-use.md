---
title: 'Öğretici: Bir .NET Core global aracı nı yükleyin ve kullanın'
description: Bir .NET aracını genel bir araç olarak nasıl yükleyip kullanacağınızı öğrenin.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156744"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="43ccc-103">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="43ccc-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="43ccc-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="43ccc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="43ccc-105">Bu öğretici, genel bir aracı nasıl yükleyip kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="43ccc-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="43ccc-106">[Bu serinin ilk öğretici](global-tools-how-to-create.md)oluşturduğunuz bir araç kullanın.</span><span class="sxs-lookup"><span data-stu-id="43ccc-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43ccc-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="43ccc-107">Prerequisites</span></span>

* <span data-ttu-id="43ccc-108">Bu [serinin ilk öğretici](global-tools-how-to-create.md)tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="43ccc-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="43ccc-109">Aracı genel bir araç olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="43ccc-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="43ccc-110">*microsoft.botsay* proje klasöründe [dotnet aracı yükleme](dotnet-tool-install.md) komutunu çalıştırarak paketi paketten aracı yükleyin:</span><span class="sxs-lookup"><span data-stu-id="43ccc-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="43ccc-111">Parametre ,NET `--global` Core CLI'ye araç ikililerini PATH ortamı değişkenine otomatik olarak eklenen varsayılan bir konuma yüklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="43ccc-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="43ccc-112">Parametre .NET `--add-source` Core CLI'ye *./nupkg* dizinini NuGet paketleri için ek kaynak akışı olarak geçici olarak kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="43ccc-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="43ccc-113">Paketinize, paketinizin Nuget.org sitesinde değil, yalnızca *./nupkg* dizininde bulunduğundan emin olmak için benzersiz bir ad verdiniz.</span><span class="sxs-lookup"><span data-stu-id="43ccc-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="43ccc-114">Çıktı, aracı çağırmak için kullanılan komutu ve yüklenen sürümü gösterir:</span><span class="sxs-lookup"><span data-stu-id="43ccc-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="43ccc-115">Aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="43ccc-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="43ccc-116">Bu komut başarısız olursa, PATH'i yenilemek için yeni bir terminal açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="43ccc-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="43ccc-117">[Dotnet aracını kaldır](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="43ccc-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="43ccc-118">Aracı özel bir konuma yüklenen genel bir araç olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="43ccc-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="43ccc-119">Paketi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="43ccc-119">Install the tool from the package.</span></span>

   <span data-ttu-id="43ccc-120">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="43ccc-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="43ccc-121">Linux veya macOS'ta:</span><span class="sxs-lookup"><span data-stu-id="43ccc-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="43ccc-122">`--tool-path` Parametre .NET Core CLI'ye takım ikililerini belirtilen konuma yüklemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="43ccc-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="43ccc-123">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="43ccc-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="43ccc-124">Bu dizin, PATH ortamı değişkenine otomatik olarak eklenmez.</span><span class="sxs-lookup"><span data-stu-id="43ccc-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="43ccc-125">Çıktı, aracı çağırmak için kullanılan komutu ve yüklenen sürümü gösterir:</span><span class="sxs-lookup"><span data-stu-id="43ccc-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="43ccc-126">Aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="43ccc-126">Invoke the tool:</span></span>

   <span data-ttu-id="43ccc-127">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="43ccc-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="43ccc-128">Linux veya macOS'ta:</span><span class="sxs-lookup"><span data-stu-id="43ccc-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="43ccc-129">[Dotnet aracını kaldır](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="43ccc-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="43ccc-130">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="43ccc-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="43ccc-131">Linux veya macOS'ta:</span><span class="sxs-lookup"><span data-stu-id="43ccc-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="43ccc-132">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="43ccc-132">Troubleshoot</span></span>

<span data-ttu-id="43ccc-133">Öğreticiyi izlerken bir hata iletisi alırsanız, [Sorun Giderme .NET Core araç kullanım sorunlarına](troubleshoot-usage-issues.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="43ccc-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="43ccc-134">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="43ccc-134">Next steps</span></span>

<span data-ttu-id="43ccc-135">Bu öğreticide, bir aracı genel bir araç olarak yüklemiş ve kullanmışsınız.</span><span class="sxs-lookup"><span data-stu-id="43ccc-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="43ccc-136">Yerel bir araçla aynı aracı yüklemek ve kullanmak için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="43ccc-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43ccc-137">Yerel araçları yükleme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="43ccc-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
