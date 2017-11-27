---
title: "Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2753db8e06c8c1b50c6e5cee17330d421e88511f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme
Bir ses veya video dosyasını oynatmak için kullandığınız bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer>. Yük ve medya yürütmek için iki yolu vardır. İlk kullanmaktır bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> kendilerini ve ikinci yolu kendi oluşturmaktır <xref:System.Windows.Media.MediaTimeline> ile kullanılacak <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Bir görüntü gibi medyayı uygulamanız ile dağıtırken, bir medya dosyasını proje kaynağı olarak kullanamazsınız. Proje dosyanızda, bunun yerine medya türü ayarlamalısınız `Content` ve `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> bir video dosyası bir kez oynatmak için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetim kazanmak için bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleri. <xref:System.Windows.Media.MediaTimeline> Video yinelenmesi gerektiğini belirtmenize olanak sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> art arda çalmasına nesneleri.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Kullandığınızda, Not bir <xref:System.Windows.Media.MediaTimeline>, etkileşimli kullandığınız <xref:System.Windows.Media.Animation.ClockController> döndürülen <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.MediaClock> etkileşimli yöntemlerinin yerine medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.VideoDrawing>  
 [Çizim nesnelerine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
