---
title: 'Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: beeddc658f16d8b52142a8a79f9c61e4f7070b01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561397"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi
Aşağıdaki örnek, medya kullanma kayıttan yürütmeyi denetlemek gösterilmiştir bir <xref:System.Windows.Controls.MediaElement>. Örnek yürütmek, duraklatmak, durdurmak ve İleri ve geri ortamda Atla yanı sıra, ses ve hız oranını ayarlamak olanak sağlayan bir basit medya oynatıcı oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod UI oluşturur.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Özelliği <xref:System.Windows.Controls.MediaElement> ayarlanmalıdır `Manual` etkileşimli olarak durdurmak oluşturabilmek, duraklatma ve medya yürütme.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnek UI denetimlerinin işlevlerini uygular. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemleri sırasıyla yürütmek, duraklatma ve ortam durdurmak için kullanılır. Değiştirme <xref:System.Windows.Controls.MediaElement.Position%2A> özelliği <xref:System.Windows.Controls.MediaElement> ortamda atlamanızı sağlar. Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medya sesi ve kayıttan yürütme hızını ayarlamak için kullanılır.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görsel Taslak Kullanarak MediaElement'i Denetleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
