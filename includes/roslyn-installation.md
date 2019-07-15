---
ms.openlocfilehash: dab6b435a885d862d08f94dd31de79625f19bcc0
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870500"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="33897-101">Yükleme yönergeleri - Visual Studio yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="33897-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="33897-102">Bulmak için iki farklı yolu vardır **.NET derleyici Platformu SDK'sı** içinde **Visual Studio yükleyicisi**:</span><span class="sxs-lookup"><span data-stu-id="33897-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="33897-103">Visual Studio Yükleyicisi'ni kullanarak yükleyin - iş yüklerini görüntüleyin</span><span class="sxs-lookup"><span data-stu-id="33897-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="33897-104">.NET derleyici Platformu SDK'sı, Visual Studio uzantısı geliştirme iş yükünün parçası otomatik olarak seçili değildir.</span><span class="sxs-lookup"><span data-stu-id="33897-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="33897-105">İsteğe bağlı bir bileşen seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="33897-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="33897-106">Çalıştırma **Visual Studio yükleyicisi**</span><span class="sxs-lookup"><span data-stu-id="33897-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="33897-107">Seçin **değiştirme**</span><span class="sxs-lookup"><span data-stu-id="33897-107">Select **Modify**</span></span> 
1. <span data-ttu-id="33897-108">Denetleme **Visual Studio uzantısı geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="33897-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="33897-109">Açık **Visual Studio uzantısı geliştirme** Özet ağaç düğümü.</span><span class="sxs-lookup"><span data-stu-id="33897-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="33897-110">İçin kutuyu **.NET derleyici Platformu SDK'sı**.</span><span class="sxs-lookup"><span data-stu-id="33897-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="33897-111">Bu son isteğe bağlı bileşenler altında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33897-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="33897-112">Bunu Ayrıca isteğe bağlı olarak, istersiniz **DGML düzenleyici** görselleştiricisindeki grafikleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="33897-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="33897-113">Açık **tek tek bileşenler** Özet ağaç düğümü.</span><span class="sxs-lookup"><span data-stu-id="33897-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="33897-114">İçin kutuyu **DGML Düzenleyici**</span><span class="sxs-lookup"><span data-stu-id="33897-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="33897-115">Visual Studio yükleyicisi - bağımsız bileşenler sekmesinde kullanarak yükleme</span><span class="sxs-lookup"><span data-stu-id="33897-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="33897-116">Çalıştırma **Visual Studio yükleyicisi**</span><span class="sxs-lookup"><span data-stu-id="33897-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="33897-117">Seçin **değiştirme**</span><span class="sxs-lookup"><span data-stu-id="33897-117">Select **Modify**</span></span> 
1. <span data-ttu-id="33897-118">Seçin **tek tek bileşenler** sekmesi</span><span class="sxs-lookup"><span data-stu-id="33897-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="33897-119">İçin kutuyu **.NET derleyici Platformu SDK'sı**.</span><span class="sxs-lookup"><span data-stu-id="33897-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="33897-120">Üst altında bulabilirsiniz **derleyiciler, derleme araçları ve çalışma zamanları** bölümü.</span><span class="sxs-lookup"><span data-stu-id="33897-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="33897-121">Bunu Ayrıca isteğe bağlı olarak, istersiniz **DGML düzenleyici** görselleştiricisindeki grafikleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="33897-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="33897-122">İçin kutuyu **DGML düzenleyici**.</span><span class="sxs-lookup"><span data-stu-id="33897-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="33897-123">Bunun altında bulabilirsiniz **kod Araçları** bölümü.</span><span class="sxs-lookup"><span data-stu-id="33897-123">You'll find it under the **Code tools** section.</span></span>
