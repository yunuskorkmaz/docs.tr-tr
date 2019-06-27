---
title: Model oluşturucuyu yükleme
description: ML.NET Model Oluşturucu aracı yüklemeyi öğrenin
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410652"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="f3369-103">ML.NET Model oluşturucuyu yükleme</span><span class="sxs-lookup"><span data-stu-id="f3369-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="f3369-104">Machine learning .NET uygulamalarınıza eklemek için ML.NET Model Oluşturucu yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="f3369-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="f3369-105">Model Oluşturucu şu anda Önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="f3369-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f3369-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f3369-106">Pre-requisites</span></span>

- <span data-ttu-id="f3369-107">Visual Studio 2017 15.9.12 veya üzeri / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="f3369-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="f3369-108">.NET core 2.1 veya üzeri SDK'sı</span><span class="sxs-lookup"><span data-stu-id="f3369-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="f3369-109">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="f3369-109">Limitations</span></span>

- <span data-ttu-id="f3369-110">ML.NET Model Oluşturucu uzantısı şu anda yalnızca Visual Studio Windows üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f3369-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="f3369-111">Eğitim veri kümesi sınırını 1 GB</span><span class="sxs-lookup"><span data-stu-id="f3369-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="f3369-112">SQL Server eğitimi için 100 bin satır sınırı vardır.</span><span class="sxs-lookup"><span data-stu-id="f3369-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="f3369-113">Visual Studio 2017 için Microsoft SQL Server veri araçları desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f3369-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="f3369-114">Yükleme</span><span class="sxs-lookup"><span data-stu-id="f3369-114">Install</span></span>

<span data-ttu-id="f3369-115">Visual Studio Market aracılığıyla veya içinden ML.NET Model Oluşturucu yüklenebilir Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3369-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="f3369-116">Visual Studio Market</span><span class="sxs-lookup"><span data-stu-id="f3369-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="f3369-117">İndirmesine [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="f3369-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="f3369-118">İlgili Visual Studio sürümünü yüklemek için istemleri takip edin</span><span class="sxs-lookup"><span data-stu-id="f3369-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="f3369-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f3369-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="f3369-120">Menü çubuğunda **Araçları** > **Uzantılar ve güncelleştirmeler**</span><span class="sxs-lookup"><span data-stu-id="f3369-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="f3369-121">İçinde *uzantı ve güncelleştirmeler* anında, select *çevrimiçi* düğümü.</span><span class="sxs-lookup"><span data-stu-id="f3369-121">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="f3369-122">Arama çubuğunda arama *ML.NET Model Oluşturucu* sonuçlarından ML.NET Model Oluşturucu (Önizleme) seçin.</span><span class="sxs-lookup"><span data-stu-id="f3369-122">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="f3369-123">Yüklemeyi tamamlamak için istemleri takip edin</span><span class="sxs-lookup"><span data-stu-id="f3369-123">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="f3369-124">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="f3369-124">Visual Studio 2019</span></span>

1. <span data-ttu-id="f3369-125">Menü çubuğunda, seçin **uzantıları** > **uzantıları Yönet**</span><span class="sxs-lookup"><span data-stu-id="f3369-125">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="f3369-126">İçinde *uzantı ve güncelleştirmeler* anında, select *çevrimiçi* düğümü.</span><span class="sxs-lookup"><span data-stu-id="f3369-126">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="f3369-127">Tür *ML.NET Model Oluşturucu* ML.NET Model Oluşturucu (Önizleme) arama çubuğuna seçin</span><span class="sxs-lookup"><span data-stu-id="f3369-127">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="f3369-128">Yüklemeyi tamamlamak için istemleri takip edin</span><span class="sxs-lookup"><span data-stu-id="f3369-128">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="f3369-129">Kaldır</span><span class="sxs-lookup"><span data-stu-id="f3369-129">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="f3369-130">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f3369-130">Visual Studio 2017</span></span>

1. <span data-ttu-id="f3369-131">Menü çubuğunda, seçin **Araçları** > **Uzantılar ve güncelleştirmeler**</span><span class="sxs-lookup"><span data-stu-id="f3369-131">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="f3369-132">İçinde *uzantı ve güncelleştirmeler* isteminde, genişletme *yüklü* düğümünü seçip alt *araçları*</span><span class="sxs-lookup"><span data-stu-id="f3369-132">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="f3369-133">Araçları listesinden ML.NET Model Oluşturucu (Önizleme) seçin ve ardından seçin *Kaldır*</span><span class="sxs-lookup"><span data-stu-id="f3369-133">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="f3369-134">Kaldırma işlemini tamamlamak için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f3369-134">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="f3369-135">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="f3369-135">Visual Studio 2019</span></span>

1. <span data-ttu-id="f3369-136">Menü çubuğunda, seçin **uzantıları** > **uzantıları Yönet**</span><span class="sxs-lookup"><span data-stu-id="f3369-136">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="f3369-137">İçinde *uzantı ve güncelleştirmeler* isteminde, genişletme *yüklü* düğümünü seçip alt *araçları*</span><span class="sxs-lookup"><span data-stu-id="f3369-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="f3369-138">Araçları listesinden ML.NET Model Oluşturucu (Önizleme) seçin ve ardından seçin *Kaldır*</span><span class="sxs-lookup"><span data-stu-id="f3369-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="f3369-139">Kaldırma işlemini tamamlamak için istemleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f3369-139">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="f3369-140">Upgrade</span><span class="sxs-lookup"><span data-stu-id="f3369-140">Upgrade</span></span>

<span data-ttu-id="f3369-141">Yükseltme işlemi, yükleme işlemine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f3369-141">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="f3369-142">Visual Studio Market'ten en son sürümü yükleyin ya da Visual Studio Uzantı Yöneticisi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3369-142">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
