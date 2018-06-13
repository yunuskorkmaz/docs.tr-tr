---
title: SoundPlayer Sınıfına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 31ce87303b7b96cfd14d4daf07fd21c9de91a548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535970"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="c1740-102">SoundPlayer Sınıfına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1740-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="c1740-103"><xref:System.Media.SoundPlayer> Sınıfı ses uygulamalarınızda kolayca eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1740-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="c1740-104"><xref:System.Media.SoundPlayer> Sınıfı .wav biçiminde bir kaynaktan veya UNC veya HTTP konumlardan ses dosyalarını çalabilir.</span><span class="sxs-lookup"><span data-stu-id="c1740-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="c1740-105">Ayrıca, <xref:System.Media.SoundPlayer> sınıfı, yükleme veya zaman uyumsuz olarak sesleri çal sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1740-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="c1740-106">Aynı zamanda <xref:System.Media.SystemSounds> bip sesi dahil olmak üzere, genel sistem sesleri yürütmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c1740-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="c1740-107">Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları</span><span class="sxs-lookup"><span data-stu-id="c1740-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="c1740-108">Ad</span><span class="sxs-lookup"><span data-stu-id="c1740-108">Name</span></span>|<span data-ttu-id="c1740-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1740-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c1740-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="c1740-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="c1740-111">Dosya yolu veya ses Web adresi.</span><span class="sxs-lookup"><span data-stu-id="c1740-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="c1740-112">Kabul edilebilir değerler UNC veya HTTP olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1740-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="c1740-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="c1740-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="c1740-114">Programınızı ses kendisinden önce yüklemek için bekleyeceği milisaniye sayısını bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c1740-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="c1740-115">Varsayılan değer 10 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="c1740-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="c1740-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Özelliği</span><span class="sxs-lookup"><span data-stu-id="c1740-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="c1740-117">Ses yüklenmesini tamamladı olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c1740-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="c1740-118"><xref:System.Media.SoundPlayer.Load%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1740-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="c1740-119">Ses zaman uyumlu olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="c1740-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="c1740-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1740-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="c1740-121">Ses zaman uyumsuz olarak yüklemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="c1740-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="c1740-122">Yükleme tamamlandığında, başlatır <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> olay.</span><span class="sxs-lookup"><span data-stu-id="c1740-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="c1740-123"><xref:System.Media.SoundPlayer.Play%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1740-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="c1740-124">Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> yeni bir iş parçacığı bir özellik.</span><span class="sxs-lookup"><span data-stu-id="c1740-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="c1740-125"><xref:System.Media.SoundPlayer.PlaySync%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1740-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="c1740-126">Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> geçerli iş parçacığının özelliği.</span><span class="sxs-lookup"><span data-stu-id="c1740-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="c1740-127"><xref:System.Media.SoundPlayer.Stop%2A> Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1740-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="c1740-128">Şu anda yürütülen herhangi bir sesi durdurur.</span><span class="sxs-lookup"><span data-stu-id="c1740-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="c1740-129"><xref:System.Media.SoundPlayer.LoadCompleted> Olay</span><span class="sxs-lookup"><span data-stu-id="c1740-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="c1740-130">Ses yük denendikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c1740-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1740-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1740-131">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
