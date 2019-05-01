---
title: SoundPlayer Sınıfına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972009"
---
# <a name="soundplayer-class-overview"></a>SoundPlayer Sınıfına Genel Bakış
<xref:System.Media.SoundPlayer> Sınıfı sesleri uygulamalarınıza kolayca dahil etmenize imkan sağlar.  
  
 <xref:System.Media.SoundPlayer> Sınıfı .wav biçimindeki bir kaynak ya da UNC veya HTTP konumlardan ses dosyaları çalabilir. Ayrıca, <xref:System.Media.SoundPlayer> sınıfı yüklenemiyor veya zaman uyumsuz olarak sesleri çalmak olanak sağlar.  
  
 Ayrıca <xref:System.Media.SystemSounds> bip sesi dahil olmak üzere, genel sistem sesleri oynatmak için sınıf.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Yaygın olarak kullanılan özellikleri, yöntemleri ve olayları  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> Özelliği|Dosya yolu veya ses Web adresi. Kabul edilebilir değerler, UNC veya HTTP olabilir.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> Özelliği|Programınızı ses önceki yükleme için bekleyeceği milisaniye sayısını, özel durum oluşturur. Varsayılan değer 10 saniyedir.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Özelliği|Ses yüklenmesini tamamladı gösteren bir Boole değeri.|  
|<xref:System.Media.SoundPlayer.Load%2A> Yöntemi|Ses zaman uyumlu olarak yükler.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> Yöntemi|Zaman uyumsuz ses yükleme başlar. Yükleme tamamlandığında, bilmemektedir <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> olay.|  
|<xref:System.Media.SoundPlayer.Play%2A> Yöntemi|Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> yeni bir dizi özelliği.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> Yöntemi|Belirtilen ses çalar <xref:System.Media.SoundPlayer.SoundLocation%2A> veya <xref:System.Media.SoundPlayer.Stream%2A> geçerli iş parçacığındaki özelliği.|  
|<xref:System.Media.SoundPlayer.Stop%2A> Yöntemi|Şu anda yürütülen herhangi bir sesi durdurur.|  
|<xref:System.Media.SoundPlayer.LoadCompleted> Olay|Ses yükünü denendikten sonra oluşturulur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
