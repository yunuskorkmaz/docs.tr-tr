---
title: 'Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2397662c79af208f2528f6eedcd5995cfac9526c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363104"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme
Bir ses veya video dosyası yürütmek için kullandığınız bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer>. Yükleme ve ortam yürütmek için iki yolu vardır. İlk kullanmaktır bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> kendilerini ve ikinci tarafından kendi yoludur <xref:System.Windows.Media.MediaTimeline> ile kullanılacak <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Görüntü gibi uygulamanız ile medya dağıtırken, bir medya dosyası bir proje kaynak olarak kullanamazsınız. Proje dosyanızda, bunun yerine ortam türünü ayarlamalısınız `Content` ayarlayıp `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> video dosyası bir kez oynatmak için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Medya üzerinde ek zamanlama denetim kazanmak için kullanmak bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleri. <xref:System.Windows.Media.MediaTimeline> Video yinelenmesi gerektiğini belirtmenize olanak sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> video tekrar tekrar oynatmak için nesneleri.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Kullandığınızda, Not bir <xref:System.Windows.Media.MediaTimeline>, etkileşimli kullandığınız <xref:System.Windows.Media.Animation.ClockController> döndürüldüğü <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.MediaClock> etkileşimli yöntemlerinin yerine medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.VideoDrawing>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
