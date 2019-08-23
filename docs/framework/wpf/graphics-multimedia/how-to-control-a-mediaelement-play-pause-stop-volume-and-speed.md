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
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930158"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi
Aşağıdaki örnek, kullanılarak <xref:System.Windows.Controls.MediaElement>medyanın nasıl çalınmasının nasıl yapıldığını gösterir. Örnek, medyada oynamanızı, duraklatmanızı, durdurmayı ve atlamayı, ayrıca birim ve hız oranını ayarlamayı sağlayan basit bir medya oynatıcı oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod Kullanıcı arabirimini oluşturur.  
  
> [!NOTE]
> Özelliğinin, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> medyayı etkileşimli olarak durdurabileceği, duraklatılacağı ve oynatacak şekilde ayarlanması `Manual`gerekir. <xref:System.Windows.Controls.MediaElement>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, örnek UI denetimlerinin işlevselliğini uygular. <xref:System.Windows.Controls.MediaElement.Play%2A>, Veyöntemleri<xref:System.Windows.Controls.MediaElement.Stop%2A> sırasıyla medyayı çalmak, duraklatmak ve durdurmak için kullanılır. <xref:System.Windows.Controls.MediaElement.Pause%2A> Özelliğinin değiştirilmesi, <xref:System.Windows.Controls.MediaElement> medyada atlamanızı sağlar. <xref:System.Windows.Controls.MediaElement.Position%2A> Son olarak, <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>veözellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır. <xref:System.Windows.Controls.MediaElement.Volume%2A>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslak Kullanarak MediaElement'i Denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md)
