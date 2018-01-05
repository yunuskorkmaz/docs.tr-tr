---
title: "SoundPlayer Sınıfına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3dc355fbe0d8262cb24779b99375d6075f758bbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="65cc2-102">SoundPlayer Sınıfına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="65cc2-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="65cc2-103"><xref:System.Media.SoundPlayer> Sınıfı ses uygulamalarınızda kolayca eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="65cc2-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="65cc2-104"><xref:System.Media.SoundPlayer> Sınıfı .wav biçiminde bir kaynaktan veya UNC veya HTTP konumlardan ses dosyalarını çalabilir.</span><span class="sxs-lookup"><span data-stu-id="65cc2-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="65cc2-105">Ayrıca, <xref:System.Media.SoundPlayer> sınıfı, yükleme veya zaman uyumsuz olarak sesleri çal sağlar.</span><span class="sxs-lookup"><span data-stu-id="65cc2-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="65cc2-106">Aynı zamanda <xref:System.Media.SystemSounds> bip sesi dahil olmak üzere, genel sistem sesleri yürütmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="65cc2-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="65cc2-107">Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları</span><span class="sxs-lookup"><span data-stu-id="65cc2-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="65cc2-108">Ad</span><span class="sxs-lookup"><span data-stu-id="65cc2-108">Name</span></span>|<span data-ttu-id="65cc2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65cc2-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="65cc2-110"><xref:System.Media.SoundPlayer.SoundLocation%2A>özelliği</span><span class="sxs-lookup"><span data-stu-id="65cc2-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="65cc2-111">Dosya yolu veya ses Web adresi.</span><span class="sxs-lookup"><span data-stu-id="65cc2-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="65cc2-112">Kabul edilebilir değerler UNC veya HTTP olabilir.</span><span class="sxs-lookup"><span data-stu-id="65cc2-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="65cc2-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A>özelliği</span><span class="sxs-lookup"><span data-stu-id="65cc2-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="65cc2-114">Programınızı ses kendisinden önce yüklemek için bekleyeceği milisaniye sayısını bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65cc2-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="65cc2-115">Varsayılan değer 10 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="65cc2-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="65cc2-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A>özelliği</span><span class="sxs-lookup"><span data-stu-id="65cc2-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="65cc2-117">Ses yüklenmesini tamamladı olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="65cc2-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="65cc2-118"><xref:System.Media.SoundPlayer.Load%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="65cc2-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="65cc2-119">Ses zaman uyumlu olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="65cc2-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="65cc2-120"><xref:System.Media.SoundPlayer.LoadAsync%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="65cc2-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="65cc2-121">Ses zaman uyumsuz olarak yüklemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="65cc2-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="65cc2-122">Yükleme tamamlandığında, başlatır <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> olay.</span><span class="sxs-lookup"><span data-stu-id="65cc2-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="65cc2-123"><xref:System.Media.SoundPlayer.Play%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="65cc2-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="65cc2-124">Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> yeni bir iş parçacığı bir özellik.</span><span class="sxs-lookup"><span data-stu-id="65cc2-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="65cc2-125"><xref:System.Media.SoundPlayer.PlaySync%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="65cc2-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="65cc2-126">Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> geçerli iş parçacığının özelliği.</span><span class="sxs-lookup"><span data-stu-id="65cc2-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="65cc2-127"><xref:System.Media.SoundPlayer.Stop%2A>yöntemi</span><span class="sxs-lookup"><span data-stu-id="65cc2-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="65cc2-128">Şu anda yürütülen herhangi bir sesi durdurur.</span><span class="sxs-lookup"><span data-stu-id="65cc2-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="65cc2-129"><xref:System.Media.SoundPlayer.LoadCompleted>Olay</span><span class="sxs-lookup"><span data-stu-id="65cc2-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="65cc2-130">Ses yük denendikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="65cc2-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65cc2-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65cc2-131">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
