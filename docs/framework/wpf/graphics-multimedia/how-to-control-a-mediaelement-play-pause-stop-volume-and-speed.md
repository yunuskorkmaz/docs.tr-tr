---
title: 'Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi'
description: Windows Presentation Foundation 'da (WPF) medyanın yürütülmesini denetleme. Başlat, durdur, Duraklat, geri atla ve hacmi ve hızı ayarla.
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
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853607"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi
Aşağıdaki örnek, kullanılarak medyanın nasıl çalınmasının nasıl yapıldığını gösterir <xref:System.Windows.Controls.MediaElement> . Örnek, medyada oynamanızı, duraklatmanızı, durdurmayı ve atlamayı, ayrıca birim ve hız oranını ayarlamayı sağlayan basit bir medya oynatıcı oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod Kullanıcı arabirimini oluşturur.  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>Özelliğinin, <xref:System.Windows.Controls.MediaElement> `Manual` medyayı etkileşimli olarak durdurabileceği, duraklatılacağı ve oynatacak şekilde ayarlanması gerekir.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, örnek UI denetimlerinin işlevselliğini uygular. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A> Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemleri sırasıyla medyayı çalmak, duraklatmak ve durdurmak için kullanılır. Özelliğinin değiştirilmesi <xref:System.Windows.Controls.MediaElement.Position%2A> , <xref:System.Windows.Controls.MediaElement> medyada atlamanızı sağlar. Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslak Kullanarak MediaElement'i Denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md)
