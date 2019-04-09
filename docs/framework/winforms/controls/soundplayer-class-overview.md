---
title: SoundPlayer Sınıfına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195013"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="98f22-102">SoundPlayer Sınıfına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="98f22-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="98f22-103"><xref:System.Media.SoundPlayer> Sınıfı sesleri uygulamalarınıza kolayca dahil etmenize imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="98f22-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="98f22-104"><xref:System.Media.SoundPlayer> Sınıfı .wav biçimindeki bir kaynak ya da UNC veya HTTP konumlardan ses dosyaları çalabilir.</span><span class="sxs-lookup"><span data-stu-id="98f22-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="98f22-105">Ayrıca, <xref:System.Media.SoundPlayer> sınıfı yüklenemiyor veya zaman uyumsuz olarak sesleri çalmak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="98f22-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="98f22-106">Ayrıca <xref:System.Media.SystemSounds> bip sesi dahil olmak üzere, genel sistem sesleri oynatmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="98f22-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="98f22-107">Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları</span><span class="sxs-lookup"><span data-stu-id="98f22-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="98f22-108">Ad</span><span class="sxs-lookup"><span data-stu-id="98f22-108">Name</span></span>|<span data-ttu-id="98f22-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98f22-109">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> <span data-ttu-id="98f22-110">özellik</span><span class="sxs-lookup"><span data-stu-id="98f22-110">property</span></span>|<span data-ttu-id="98f22-111">Dosya yolu veya ses Web adresi.</span><span class="sxs-lookup"><span data-stu-id="98f22-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="98f22-112">Kabul edilebilir değerler, UNC veya HTTP olabilir.</span><span class="sxs-lookup"><span data-stu-id="98f22-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> <span data-ttu-id="98f22-113">özellik</span><span class="sxs-lookup"><span data-stu-id="98f22-113">property</span></span>|<span data-ttu-id="98f22-114">Programınızı ses önceki yükleme için bekleyeceği milisaniye sayısını, özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98f22-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="98f22-115">Varsayılan değer 10 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="98f22-115">The default is 10 seconds.</span></span>|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> <span data-ttu-id="98f22-116">özellik</span><span class="sxs-lookup"><span data-stu-id="98f22-116">property</span></span>|<span data-ttu-id="98f22-117">Ses yüklenmesini tamamladı gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="98f22-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<xref:System.Media.SoundPlayer.Load%2A> <span data-ttu-id="98f22-118">yöntemi</span><span class="sxs-lookup"><span data-stu-id="98f22-118">method</span></span>|<span data-ttu-id="98f22-119">Ses zaman uyumlu olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="98f22-119">Loads a sound synchronously.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> <span data-ttu-id="98f22-120">yöntemi</span><span class="sxs-lookup"><span data-stu-id="98f22-120">method</span></span>|<span data-ttu-id="98f22-121">Zaman uyumsuz ses yükleme başlar.</span><span class="sxs-lookup"><span data-stu-id="98f22-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="98f22-122">Yükleme tamamlandığında, bilmemektedir <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> olay.</span><span class="sxs-lookup"><span data-stu-id="98f22-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<xref:System.Media.SoundPlayer.Play%2A> <span data-ttu-id="98f22-123">yöntemi</span><span class="sxs-lookup"><span data-stu-id="98f22-123">method</span></span>|<span data-ttu-id="98f22-124">Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> yeni bir dizi özelliği.</span><span class="sxs-lookup"><span data-stu-id="98f22-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> <span data-ttu-id="98f22-125">yöntemi</span><span class="sxs-lookup"><span data-stu-id="98f22-125">method</span></span>|<span data-ttu-id="98f22-126">Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> geçerli iş parçacığındaki özelliği.</span><span class="sxs-lookup"><span data-stu-id="98f22-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<xref:System.Media.SoundPlayer.Stop%2A> <span data-ttu-id="98f22-127">yöntemi</span><span class="sxs-lookup"><span data-stu-id="98f22-127">method</span></span>|<span data-ttu-id="98f22-128">Şu anda yürütülen herhangi bir sesi durdurur.</span><span class="sxs-lookup"><span data-stu-id="98f22-128">Stops any sound currently playing.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadCompleted> <span data-ttu-id="98f22-129">olay</span><span class="sxs-lookup"><span data-stu-id="98f22-129">event</span></span>|<span data-ttu-id="98f22-130">Ses yükünü denendikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="98f22-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98f22-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98f22-131">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
