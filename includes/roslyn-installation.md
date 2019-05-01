---
ms.openlocfilehash: 72acd0029d0189de1c724856572957f111b9d18f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675902"
---
## <a name="installation-instructions"></a><span data-ttu-id="979d8-101">Yükleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="979d8-101">Installation instructions</span></span> 

<span data-ttu-id="979d8-102">Bulmak için iki farklı yolu vardır **.NET derleyici Platformu SDK'sı** içinde **Visual Studio yükleyicisi**:</span><span class="sxs-lookup"><span data-stu-id="979d8-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-workloads-view"></a><span data-ttu-id="979d8-103">İş yükleri görünümünü kullanarak yükleme</span><span class="sxs-lookup"><span data-stu-id="979d8-103">Install using the Workloads view</span></span>

<span data-ttu-id="979d8-104">.NET derleyici Platformu SDK'sı, Visual Studio uzantısı geliştirme iş yükünün parçası otomatik olarak seçili değildir.</span><span class="sxs-lookup"><span data-stu-id="979d8-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="979d8-105">İsteğe bağlı bir bileşen seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="979d8-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="979d8-106">Çalıştırma **Visual Studio yükleyicisi**</span><span class="sxs-lookup"><span data-stu-id="979d8-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="979d8-107">Seçin **değiştirme**</span><span class="sxs-lookup"><span data-stu-id="979d8-107">Select **Modify**</span></span> 
1. <span data-ttu-id="979d8-108">Denetleme **Visual Studio uzantısı geliştirme** iş yükü.</span><span class="sxs-lookup"><span data-stu-id="979d8-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="979d8-109">Açık **Visual Studio uzantısı geliştirme** Özet ağaç düğümü.</span><span class="sxs-lookup"><span data-stu-id="979d8-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="979d8-110">İçin kutuyu **.NET derleyici Platformu SDK'sı**.</span><span class="sxs-lookup"><span data-stu-id="979d8-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="979d8-111">Bu son isteğe bağlı bileşenler altında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="979d8-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="979d8-112">Bunu Ayrıca isteğe bağlı olarak, istersiniz **DGML düzenleyici** görselleştiricisindeki grafikleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="979d8-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="979d8-113">Açık **tek tek bileşenler** Özet ağaç düğümü.</span><span class="sxs-lookup"><span data-stu-id="979d8-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="979d8-114">İçin kutuyu **DGML Düzenleyici**</span><span class="sxs-lookup"><span data-stu-id="979d8-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-individual-components-tab"></a><span data-ttu-id="979d8-115">Bağımsız bileşenler sekmesinde kullanarak yükleme</span><span class="sxs-lookup"><span data-stu-id="979d8-115">Install using the Individual components tab</span></span>

1. <span data-ttu-id="979d8-116">Çalıştırma **Visual Studio yükleyicisi**</span><span class="sxs-lookup"><span data-stu-id="979d8-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="979d8-117">Seçin **değiştirme**</span><span class="sxs-lookup"><span data-stu-id="979d8-117">Select **Modify**</span></span> 
1. <span data-ttu-id="979d8-118">Seçin **tek tek bileşenler** sekmesi</span><span class="sxs-lookup"><span data-stu-id="979d8-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="979d8-119">İçin kutuyu **.NET derleyici Platformu SDK'sı**.</span><span class="sxs-lookup"><span data-stu-id="979d8-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="979d8-120">Üst altında bulabilirsiniz **derleyiciler, derleme araçları ve çalışma zamanları** bölümü.</span><span class="sxs-lookup"><span data-stu-id="979d8-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="979d8-121">Bunu Ayrıca isteğe bağlı olarak, istersiniz **DGML düzenleyici** görselleştiricisindeki grafikleri görüntülemek için:</span><span class="sxs-lookup"><span data-stu-id="979d8-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="979d8-122">İçin kutuyu **DGML düzenleyici**.</span><span class="sxs-lookup"><span data-stu-id="979d8-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="979d8-123">Bunun altında bulabilirsiniz **kod Araçları** bölümü.</span><span class="sxs-lookup"><span data-stu-id="979d8-123">You'll find it under the **Code tools** section.</span></span>
