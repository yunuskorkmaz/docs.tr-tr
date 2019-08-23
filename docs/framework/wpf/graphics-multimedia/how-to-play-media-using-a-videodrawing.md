---
title: 'Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956962"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme
Ses veya video dosyası oynatmak için bir <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>ve kullanın. Medyayı yüklemek ve oynatmak için kullanabileceğiniz iki yol vardır. Birincisi <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>, ve ' ı kendi başlarına ve ikinci şekilde, ve ile kullanmak için kendi oluşturmanız gerekir. <xref:System.Windows.Media.VideoDrawing>  
  
> [!NOTE]
> Medyayı uygulamanızla dağıtırken, bir görüntü gibi bir proje kaynağı olarak bir medya dosyası kullanamazsınız. Proje dosyanızda, bunun yerine medya `Content` türünü olarak ayarlamanız ve ya `Always`da olarak `PreserveNewest` ayarlamanız `CopyToOutputDirectory` gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir video <xref:System.Windows.Media.VideoDrawing> dosyasını bir <xref:System.Windows.Media.MediaPlayer> kez çalmak için bir ve bir kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetimi kazanmak için, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleriyle bir kullanın. Videonun yinelenmesi gerekip gerekmediğini belirtmenizi sağlar.<xref:System.Windows.Media.MediaTimeline>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> bir videoyu art arda oynatmak <xref:System.Windows.Media.VideoDrawing> için ve nesneleriyle birlikte kullanır.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <xref:System.Windows.Media.MediaTimeline>' I kullandığınızda, ' ın <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliğinden <xref:System.Windows.Media.MediaClock> döndürülen etkileşimli <xref:System.Windows.Media.Animation.ClockController> öğesini, uygulamasının <xref:System.Windows.Media.MediaPlayer>etkileşimli yöntemleri yerine medya kayıttan yürütmeyi denetlemek için kullanacağınızı unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.VideoDrawing>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
