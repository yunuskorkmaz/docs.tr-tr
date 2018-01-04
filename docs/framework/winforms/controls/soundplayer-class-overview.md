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
# <a name="soundplayer-class-overview"></a>SoundPlayer Sınıfına Genel Bakış
<xref:System.Media.SoundPlayer> Sınıfı ses uygulamalarınızda kolayca eklemenizi sağlar.  
  
 <xref:System.Media.SoundPlayer> Sınıfı .wav biçiminde bir kaynaktan veya UNC veya HTTP konumlardan ses dosyalarını çalabilir. Ayrıca, <xref:System.Media.SoundPlayer> sınıfı, yükleme veya zaman uyumsuz olarak sesleri çal sağlar.  
  
 Aynı zamanda <xref:System.Media.SystemSounds> bip sesi dahil olmak üzere, genel sistem sesleri yürütmek için sınıf.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A>özelliği|Dosya yolu veya ses Web adresi. Kabul edilebilir değerler UNC veya HTTP olabilir.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A>özelliği|Programınızı ses kendisinden önce yüklemek için bekleyeceği milisaniye sayısını bir özel durum oluşturur. Varsayılan değer 10 saniyedir.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A>özelliği|Ses yüklenmesini tamamladı olup olmadığını gösteren bir Boole değeri.|  
|<xref:System.Media.SoundPlayer.Load%2A>yöntemi|Ses zaman uyumlu olarak yükler.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A>yöntemi|Ses zaman uyumsuz olarak yüklemeye başlar. Yükleme tamamlandığında, başlatır <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> olay.|  
|<xref:System.Media.SoundPlayer.Play%2A>yöntemi|Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> yeni bir iş parçacığı bir özellik.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A>yöntemi|Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> geçerli iş parçacığının özelliği.|  
|<xref:System.Media.SoundPlayer.Stop%2A>yöntemi|Şu anda yürütülen herhangi bir sesi durdurur.|  
|<xref:System.Media.SoundPlayer.LoadCompleted>Olay|Ses yük denendikten sonra oluşturulur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
