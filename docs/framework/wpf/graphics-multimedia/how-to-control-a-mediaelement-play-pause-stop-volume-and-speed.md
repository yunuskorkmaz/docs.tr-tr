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
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182864"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi
Aşağıdaki örnek kullanmanın medya kayıttan yürütmeyi denetlemek nasıl gösterir bir <xref:System.Windows.Controls.MediaElement>. Örnek Yürüt, Duraklat, Durdur ve ortamı geri ve İleri Atla yanı sıra, ses ve hız oranını ayarlamak olanak tanıyan bir basit bir medya yürütücüsü oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kullanıcı Arabirimi oluşturur.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Özelliği <xref:System.Windows.Controls.MediaElement> ayarlanmalıdır `Manual` etkileşimli olarak Durdur oluşturabilmek, duraklatmak ve medya yürütme.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği UI denetimleri işlevselliğini uygular. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, Ve <xref:System.Windows.Controls.MediaElement.Stop%2A> yöntemlerini sırasıyla Yürüt, Duraklat ve medya durdurmak için kullanılır. Değiştirme <xref:System.Windows.Controls.MediaElement.Position%2A> özelliği <xref:System.Windows.Controls.MediaElement> ortamda atlamanızı geçici bir çözüm sağlar. Son olarak, <xref:System.Windows.Controls.MediaElement.Volume%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri medyanın birim ve kayıttan yürütme hızını ayarlamak için kullanılır.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslak Kullanarak MediaElement'i Denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md)
