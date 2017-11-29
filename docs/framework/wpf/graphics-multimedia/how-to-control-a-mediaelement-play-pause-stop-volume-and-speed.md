---
title: "Nasıl yapılır: MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7362c57afa3d5615ffaa0616823a954a2d577cfe
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
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
 [Film şeridi kullanarak MediaElement'i denetleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
