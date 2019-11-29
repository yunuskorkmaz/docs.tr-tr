---
title: Model Oluşturucu nasıl yüklenir
description: ML.NET model Oluşturucu aracını yüklemeyi öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b87f712ad7a8b2229c1d42db4bad1fe511475ac7
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552935"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="84f5d-103">ML.NET model Oluşturucusu nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="84f5d-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="84f5d-104">.NET uygulamalarınıza makine öğrenimi eklemek için ML.NET model Oluşturucu 'Yu yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="84f5d-105">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="84f5d-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84f5d-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="84f5d-106">Prerequisites</span></span>

- <span data-ttu-id="84f5d-107">Visual Studio 2017 sürüm 15.9.12 veya üzeri/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="84f5d-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="84f5d-108">.NET Core 2,1 SDK veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="84f5d-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="84f5d-109">.NET Core 3,0 SDK Şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="84f5d-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="84f5d-110">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="84f5d-110">Limitations</span></span>

- <span data-ttu-id="84f5d-111">ML.NET model Oluşturucu uzantısı Şu anda yalnızca Windows üzerinde Visual Studio 'da çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="84f5d-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="84f5d-112">Eğitim veri kümesi sınır 1 GB</span><span class="sxs-lookup"><span data-stu-id="84f5d-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="84f5d-113">SQL Server eğitim için 100.000 satırlık bir sınıra sahiptir</span><span class="sxs-lookup"><span data-stu-id="84f5d-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="84f5d-114">Visual Studio 2017 için Microsoft SQL Server veri araçları desteklenmez</span><span class="sxs-lookup"><span data-stu-id="84f5d-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="84f5d-115">yükleme</span><span class="sxs-lookup"><span data-stu-id="84f5d-115">Install</span></span>

<span data-ttu-id="84f5d-116">ML.NET model Oluşturucusu Visual Studio Market aracılığıyla veya Visual Studio içinden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="84f5d-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="84f5d-117">Visual Studio Market</span><span class="sxs-lookup"><span data-stu-id="84f5d-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="84f5d-118">[Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 'ten indir</span><span class="sxs-lookup"><span data-stu-id="84f5d-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="84f5d-119">İlgili Visual Studio sürümüne yüklemek için istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="84f5d-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="84f5d-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="84f5d-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="84f5d-121">Menü çubuğunda **araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 Open Extensions Manager iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="84f5d-123">*Uzantı ve güncelleştirmeler* Istemi içinde *çevrimiçi* düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="84f5d-124">Arama çubuğunda *ml.net model Oluşturucu* araması yapın ve sonuçlardan ml.net model Oluşturucu (Önizleme) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 arama ve model Oluşturucu uzantısını Uzantı Yöneticisi iletişim kutusunda ara](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="84f5d-126">Yüklemeyi tamamlamaya yönelik istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="84f5d-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="84f5d-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="84f5d-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="84f5d-128">Menü çubuğunda **Uzantılar** ' ı seçin > **Uzantıları Yönet**</span><span class="sxs-lookup"><span data-stu-id="84f5d-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Open Extensions Manager iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="84f5d-130">*Uzantı ve güncelleştirmeler* Istemi içinde *çevrimiçi* düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="84f5d-131">Arama çubuğuna *ml.net model Oluşturucu* yazın ml.net model Oluşturucu (Önizleme) öğesini seçin</span><span class="sxs-lookup"><span data-stu-id="84f5d-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 arama ve model Oluşturucu uzantısını Uzantı Yöneticisi iletişim kutusunda ara](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="84f5d-133">Yüklemeyi tamamlamaya yönelik istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="84f5d-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="84f5d-134">Kaldır</span><span class="sxs-lookup"><span data-stu-id="84f5d-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="84f5d-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="84f5d-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="84f5d-136">Menü çubuğunda **araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 Uzantıları Yönet iletişim kutusunu aç](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="84f5d-138">*Uzantı ve güncelleştirmeler* istemi Içinde, *yüklü* düğümü genişletin ve *Araçlar* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="84f5d-139">Araçlar listesinden ML.NET model Oluşturucu (Önizleme) öğesini seçin ve ardından *Kaldır* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 model Oluşturucu uzantısını uzantılar Yöneticisi iletişim kutusunda ara ve Kaldır](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="84f5d-141">Kaldırma işlemini gerçekleştirmek için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="84f5d-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="84f5d-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="84f5d-143">Menü çubuğunda **Uzantılar** ' ı seçin > **Uzantıları Yönet**</span><span class="sxs-lookup"><span data-stu-id="84f5d-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Uzantıları Yönet iletişim kutusunu aç](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="84f5d-145">*Uzantı ve güncelleştirmeler* istemi Içinde, *yüklü* düğümü genişletin ve *Araçlar* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="84f5d-146">Araçlar listesinden ML.NET model Oluşturucu (Önizleme) öğesini seçin ve ardından *Kaldır* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 model Oluşturucu uzantısını uzantılar Yöneticisi iletişim kutusunda ara ve Kaldır](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="84f5d-148">Kaldırma işlemini gerçekleştirmek için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="84f5d-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="84f5d-149">Upgrade</span><span class="sxs-lookup"><span data-stu-id="84f5d-149">Upgrade</span></span>

<span data-ttu-id="84f5d-150">Yükseltme işlemi, yükleme işlemine benzer.</span><span class="sxs-lookup"><span data-stu-id="84f5d-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="84f5d-151">Visual Studio Market 'den en son sürümü indirin ya da Visual Studio 'da Extensions Manager 'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="84f5d-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
