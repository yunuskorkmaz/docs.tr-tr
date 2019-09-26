---
title: Model Oluşturucu nasıl yüklenir
description: ML.NET model Oluşturucu aracını yüklemeyi öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b0d45ab7807bf84b98c58e85580d5aa04d0c5f7d
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306320"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="d11b6-103">ML.NET model Oluşturucusu nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="d11b6-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="d11b6-104">.NET uygulamalarınıza makine öğrenimi eklemek için ML.NET model Oluşturucu 'Yu yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="d11b6-105">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="d11b6-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="d11b6-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="d11b6-106">Pre-requisites</span></span>

- <span data-ttu-id="d11b6-107">Visual Studio 2017 15.9.12 veya üzeri/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d11b6-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="d11b6-108">.NET Core 2,1 veya üzeri SDK</span><span class="sxs-lookup"><span data-stu-id="d11b6-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="d11b6-109">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="d11b6-109">Limitations</span></span>

- <span data-ttu-id="d11b6-110">ML.NET model Oluşturucu uzantısı Şu anda yalnızca Windows üzerinde Visual Studio 'da çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="d11b6-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="d11b6-111">Eğitim veri kümesi sınır 1 GB</span><span class="sxs-lookup"><span data-stu-id="d11b6-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="d11b6-112">SQL Server eğitim için 100.000 satırlık bir sınıra sahiptir</span><span class="sxs-lookup"><span data-stu-id="d11b6-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="d11b6-113">Visual Studio 2017 için Microsoft SQL Server veri araçları desteklenmez</span><span class="sxs-lookup"><span data-stu-id="d11b6-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="d11b6-114">Yükleme</span><span class="sxs-lookup"><span data-stu-id="d11b6-114">Install</span></span>

<span data-ttu-id="d11b6-115">ML.NET model Oluşturucusu Visual Studio Market aracılığıyla veya Visual Studio içinden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d11b6-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="d11b6-116">Visual Studio Market</span><span class="sxs-lookup"><span data-stu-id="d11b6-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="d11b6-117">[Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=MLNET.07) 'ten indir</span><span class="sxs-lookup"><span data-stu-id="d11b6-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="d11b6-118">İlgili Visual Studio sürümüne yüklemek için istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="d11b6-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="d11b6-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d11b6-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="d11b6-120">Menü çubuğunda **Araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 Open Extensions Manager iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="d11b6-122">*Uzantı ve güncelleştirmeler* Istemi içinde *çevrimiçi* düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="d11b6-123">Arama çubuğunda *ml.net model Oluşturucu* araması yapın ve sonuçlardan ml.net model Oluşturucu (Önizleme) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 arama ve model Oluşturucu uzantısını Uzantı Yöneticisi iletişim kutusunda ara](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="d11b6-125">Yüklemeyi tamamlamaya yönelik istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="d11b6-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="d11b6-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d11b6-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="d11b6-127">Menü çubuğunda **Uzantılar** > **Yönet uzantıları** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Open Extensions Manager iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="d11b6-129">*Uzantı ve güncelleştirmeler* Istemi içinde *çevrimiçi* düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="d11b6-130">Arama çubuğuna *ml.net model Oluşturucu* yazın ml.net model Oluşturucu (Önizleme) öğesini seçin</span><span class="sxs-lookup"><span data-stu-id="d11b6-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 arama ve model Oluşturucu uzantısını Uzantı Yöneticisi iletişim kutusunda ara](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="d11b6-132">Yüklemeyi tamamlamaya yönelik istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="d11b6-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="d11b6-133">Kaldır</span><span class="sxs-lookup"><span data-stu-id="d11b6-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="d11b6-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d11b6-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="d11b6-135">Menü çubuğunda **Araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 Uzantıları Yönet iletişim kutusunu aç](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="d11b6-137">*Uzantı ve güncelleştirmeler* istemi Içinde, *yüklü* düğümü genişletin ve *Araçlar* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="d11b6-138">Araçlar listesinden ML.NET model Oluşturucu (Önizleme) öğesini seçin ve ardından *Kaldır* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 model Oluşturucu uzantısını uzantılar Yöneticisi iletişim kutusunda ara ve Kaldır](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="d11b6-140">Kaldırma işlemini gerçekleştirmek için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="d11b6-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="d11b6-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="d11b6-142">Menü çubuğunda **Uzantılar** > **Yönet uzantıları** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 Uzantıları Yönet iletişim kutusunu aç](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="d11b6-144">*Uzantı ve güncelleştirmeler* istemi Içinde, *yüklü* düğümü genişletin ve *Araçlar* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="d11b6-145">Araçlar listesinden ML.NET model Oluşturucu (Önizleme) öğesini seçin ve ardından *Kaldır* ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 model Oluşturucu uzantısını uzantılar Yöneticisi iletişim kutusunda ara ve Kaldır](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="d11b6-147">Kaldırma işlemini gerçekleştirmek için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d11b6-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="d11b6-148">Upgrade</span><span class="sxs-lookup"><span data-stu-id="d11b6-148">Upgrade</span></span>

<span data-ttu-id="d11b6-149">Yükseltme işlemi, yükleme işlemine benzer.</span><span class="sxs-lookup"><span data-stu-id="d11b6-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="d11b6-150">Visual Studio Market 'den en son sürümü indirin ya da Visual Studio 'da Extensions Manager 'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d11b6-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
