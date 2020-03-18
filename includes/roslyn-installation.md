---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526782"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="fdab2-101">Kurulum talimatları - Visual Studio Installer</span><span class="sxs-lookup"><span data-stu-id="fdab2-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="fdab2-102">**Visual Studio Installer'da** **.NET Derleyici Platformu SDK'yı** bulmanın iki farklı yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="fdab2-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="fdab2-103">Visual Studio Installer kullanarak yükleyin - İş yükleri görünümü</span><span class="sxs-lookup"><span data-stu-id="fdab2-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="fdab2-104">.NET Derleyici Platformu SDK, Visual Studio uzantısı geliştirme iş yükünün bir parçası olarak otomatik olarak seçilmez.</span><span class="sxs-lookup"><span data-stu-id="fdab2-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="fdab2-105">İsteğe bağlı bir bileşen olarak seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdab2-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="fdab2-106">**Görsel Stüdyo Yükleyici çalıştırın**</span><span class="sxs-lookup"><span data-stu-id="fdab2-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="fdab2-107">**Değiştir'i** seçin</span><span class="sxs-lookup"><span data-stu-id="fdab2-107">Select **Modify**</span></span>
1. <span data-ttu-id="fdab2-108">Visual **Studio uzantısı geliştirme** iş yükünü kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="fdab2-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="fdab2-109">Özet ağacındaki **Visual Studio uzantı geliştirme** düğümlerini açın.</span><span class="sxs-lookup"><span data-stu-id="fdab2-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="fdab2-110">**.NET Derleyici Platformu SDK**için kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="fdab2-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="fdab2-111">İsteğe bağlı bileşenlerin altında son bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fdab2-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="fdab2-112">İsteğe bağlı olarak, **DGML düzenleyicisinin** görselleştiricide grafikler görüntülemesini de istersiniz:</span><span class="sxs-lookup"><span data-stu-id="fdab2-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="fdab2-113">Özet ağacındaki **Tek bileşen** düğümlerini açın.</span><span class="sxs-lookup"><span data-stu-id="fdab2-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="fdab2-114">**DGML düzenleyicisi** için kutuyu işaretleyin</span><span class="sxs-lookup"><span data-stu-id="fdab2-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="fdab2-115">Visual Studio Installer kullanarak yükleyin - Tek tek bileşenler sekmesi</span><span class="sxs-lookup"><span data-stu-id="fdab2-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="fdab2-116">**Görsel Stüdyo Yükleyici çalıştırın**</span><span class="sxs-lookup"><span data-stu-id="fdab2-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="fdab2-117">**Değiştir'i** seçin</span><span class="sxs-lookup"><span data-stu-id="fdab2-117">Select **Modify**</span></span>
1. <span data-ttu-id="fdab2-118">Bireysel **bileşenler** sekmesini seçin</span><span class="sxs-lookup"><span data-stu-id="fdab2-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="fdab2-119">**.NET Derleyici Platformu SDK**için kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="fdab2-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="fdab2-120">**Derleyiciler, oluşturma araçları ve çalışma süreleri** bölümünün altında en üstte bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdab2-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="fdab2-121">İsteğe bağlı olarak, **DGML düzenleyicisinin** görselleştiricide grafikler görüntülemesini de istersiniz:</span><span class="sxs-lookup"><span data-stu-id="fdab2-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="fdab2-122">**DGML düzenleyicisi**için kutuyu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="fdab2-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="fdab2-123">**Kod araçları** bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdab2-123">You'll find it under the **Code tools** section.</span></span>
