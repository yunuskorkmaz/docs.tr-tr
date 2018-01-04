---
title: "Nasıl yapılır: Video ile bir Alanı Boyama"
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
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a72843547d934aeaeec062eec1241e402baf56bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a>Nasıl yapılır: Video ile bir Alanı Boyama
Bu örnek, bir alanı ortam ile boyamak gösterilmektedir. Bir alanı ortam ile boyamak için bir yoldur kullanmak için bir <xref:System.Windows.Controls.MediaElement> ile birlikte bir <xref:System.Windows.Media.VisualBrush>. Kullanmak <xref:System.Windows.Controls.MediaElement> yüklemek ve medya yürütme ve ayarlamak için kullanmak için <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği <xref:System.Windows.Media.VisualBrush>. Daha sonra <xref:System.Windows.Media.VisualBrush> bir alanı yüklü ortam ile boyamak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.VisualBrush> boyamak için <xref:System.Windows.Controls.TextBlock.Foreground%2A> , bir <xref:System.Windows.Controls.TextBlock> video denetimiyle. Bu örnek ayarlar <xref:System.Windows.Controls.MediaElement.IsMuted%2A> özelliği <xref:System.Windows.Controls.MediaElement> için `true` böylece ses üretilmez.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>Örnek  
 Çünkü <xref:System.Windows.Media.VisualBrush> devraldığı <xref:System.Windows.Media.TileBrush> sınıfı, birkaç döşeme modu sağlar. Ayarlayarak <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği bir <xref:System.Windows.Media.VisualBrush> için <xref:System.Windows.Media.TileMode.Tile> ayarlayarak kendi <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliği boyama alandan daha küçük bir değere döşeli bir desen oluşturabilirsiniz.  
  
 Aşağıdaki örnek, önceki örnekte, hariç eşdeğerdir <xref:System.Windows.Media.VisualBrush> video bir desen oluşturur.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Uygulamanız için bir medya dosyası gibi bir içerik dosyası ekleme hakkında bilgi için bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md). Medya dosyası eklediğinizde, onu eklemeniz gerekir kaynak dosyası olarak değil bir içerik dosyası olarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.VisualBrush>  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush’a Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [Multimedyaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
