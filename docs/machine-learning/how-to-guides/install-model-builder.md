---
title: Model Oluşturucu nasıl yüklenir?
description: ML.NET Model Oluşturucu aracını nasıl yükleyin öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848658"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="58e98-103">Model Oluşturucu ML.NET nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="58e98-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="58e98-104">.NET uygulamalarınıza makine öğrenimi eklemek için ML.NET Model Builder'ı nasıl yükleyebilirsiniz öğrenin.</span><span class="sxs-lookup"><span data-stu-id="58e98-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="58e98-105">Model Oluşturucu şu anda Önizleme'de.</span><span class="sxs-lookup"><span data-stu-id="58e98-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58e98-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="58e98-106">Prerequisites</span></span>

- <span data-ttu-id="58e98-107">Visual Studio 2017 sürüm 15.9.12 veya sonrası / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="58e98-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="58e98-108">.NET Core 2.1 SDK veya sonrası.</span><span class="sxs-lookup"><span data-stu-id="58e98-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="58e98-109">.NET Core 3.0 SDK şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="58e98-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="58e98-110">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="58e98-110">Limitations</span></span>

- <span data-ttu-id="58e98-111">ML.NET Model Oluşturucu Uzantısı şu anda yalnızca Windows'daki Visual Studio'da çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58e98-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="58e98-112">1GB eğitim veri seti sınırı</span><span class="sxs-lookup"><span data-stu-id="58e98-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="58e98-113">SQL Server eğitim için 100 bin satır sınırı vardır</span><span class="sxs-lookup"><span data-stu-id="58e98-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="58e98-114">Visual Studio 2017 için Microsoft SQL Server Veri Araçları desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="58e98-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="58e98-115">Yükleme</span><span class="sxs-lookup"><span data-stu-id="58e98-115">Install</span></span>

<span data-ttu-id="58e98-116">ML.NET Model oluşturucu Visual Studio Marketplace üzerinden ya da Visual Studio içinde kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="58e98-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="58e98-117">Visual Studio Market</span><span class="sxs-lookup"><span data-stu-id="58e98-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="58e98-118">Visual [Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=MLNET.07) indirin</span><span class="sxs-lookup"><span data-stu-id="58e98-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="58e98-119">İlgili Visual Studio sürümüne yüklemek için istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="58e98-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="58e98-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="58e98-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="58e98-121">Menü çubuğunda **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ni** seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 açık uzantıları yöneticisi iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="58e98-123">*Uzantı ve Güncelleştirmeler* istemi *içinde, Çevrimiçi* düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="58e98-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="58e98-124">Arama çubuğunda, *model oluşturucuML.NET* ve sonuçlardan ML.NET Model Oluşturucu'yu (Önizleme) seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 arama ve uzantıları yöneticisi iletişim modeli model oluşturucu uzantısı yükleyin](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="58e98-126">Yüklemeyi tamamlamak için istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="58e98-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="58e98-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="58e98-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="58e98-128">Menü çubuğunda Uzantıları **Extensions** > **Yönet Uzantıları'nı** seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 açık uzantıları yöneticisi iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="58e98-130">*Uzantı ve Güncelleştirmeler* istemi *içinde, Çevrimiçi* düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="58e98-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="58e98-131">Arama çubuğuna *model* oluşturucuML.NET yazın ML.NET Model Oluşturucu'yu seçin (Önizleme)</span><span class="sxs-lookup"><span data-stu-id="58e98-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 arama ve uzantıları yöneticisi iletişim modeli oluşturucu uzantısı yükleyin](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="58e98-133">Yüklemeyi tamamlamak için istemleri izleyin</span><span class="sxs-lookup"><span data-stu-id="58e98-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="58e98-134">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="58e98-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="58e98-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="58e98-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="58e98-136">Menü çubuğunda **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ni** seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 açık yönet uzantıları iletişim kutusu](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="58e98-138">*Uzantı ve Güncelleştirmeler* istemi içinde, *Yüklü* düğüm genişletmek ve *Araçları* seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="58e98-139">Araçlar listesinden model oluşturucuML.NET (Önizleme) seçeneğini belirleyin ve ardından *Kaldır'ı* seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 arama ve uzantıları yöneticisi iletişim modelini model oluşturucu uzantısı kaldırmak](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="58e98-141">Yüklemeyi tamamlamak için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="58e98-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="58e98-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="58e98-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="58e98-143">Menü çubuğunda Uzantıları **Extensions** > **Yönet Uzantıları'nı** seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 açık yönet uzantıları iletişim kutusu](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="58e98-145">*Uzantı ve Güncelleştirmeler* istemi içinde, *Yüklü* düğüm genişletmek ve *Araçları* seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="58e98-146">Araçlar listesinden model oluşturucuML.NET (Önizleme) seçeneğini belirleyin ve ardından *Kaldır'ı* seçin</span><span class="sxs-lookup"><span data-stu-id="58e98-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 arama ve uzantıları yöneticisi iletişim modeli oluşturucu uzantısı kaldırmak](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="58e98-148">Yüklemeyi tamamlamak için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="58e98-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="58e98-149">Yükseltme</span><span class="sxs-lookup"><span data-stu-id="58e98-149">Upgrade</span></span>

<span data-ttu-id="58e98-150">Yükseltme işlemi yükleme işlemine benzer.</span><span class="sxs-lookup"><span data-stu-id="58e98-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="58e98-151">Visual Studio Marketplace'ten en son sürümü indirin veya Visual Studio'daki Extensions Manager'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="58e98-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
