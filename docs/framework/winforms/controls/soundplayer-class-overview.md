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
# <a name="soundplayer-class-overview"></a>SoundPlayer Sınıfına Genel Bakış
<xref:System.Media.SoundPlayer> Sınıfı ses uygulamalarınızda kolayca eklemenizi sağlar.  
  
 <xref:System.Media.SoundPlayer> Sınıfı .wav biçiminde bir kaynaktan veya UNC veya HTTP konumlardan ses dosyalarını çalabilir. Ayrıca, <xref:System.Media.SoundPlayer> sınıfı, yükleme veya zaman uyumsuz olarak sesleri çal sağlar.  
  
 Aynı zamanda <xref:System.Media.SystemSounds> bip sesi dahil olmak üzere, genel sistem sesleri yürütmek için sınıf.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> Özelliği|Dosya yolu veya ses Web adresi. Kabul edilebilir değerler UNC veya HTTP olabilir.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> Özelliği|Programınızı ses kendisinden önce yüklemek için bekleyeceği milisaniye sayısını bir özel durum oluşturur. Varsayılan değer 10 saniyedir.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Özelliği|Ses yüklenmesini tamamladı olup olmadığını gösteren bir Boole değeri.|  
|<xref:System.Media.SoundPlayer.Load%2A> Yöntemi|Ses zaman uyumlu olarak yükler.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> Yöntemi|Ses zaman uyumsuz olarak yüklemeye başlar. Yükleme tamamlandığında, başlatır <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> olay.|  
|<xref:System.Media.SoundPlayer.Play%2A> Yöntemi|Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> yeni bir iş parçacığı bir özellik.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> Yöntemi|Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> geçerli iş parçacığının özelliği.|  
|<xref:System.Media.SoundPlayer.Stop%2A> Yöntemi|Şu anda yürütülen herhangi bir sesi durdurur.|  
|<xref:System.Media.SoundPlayer.LoadCompleted> Olay|Ses yük denendikten sonra oluşturulur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
