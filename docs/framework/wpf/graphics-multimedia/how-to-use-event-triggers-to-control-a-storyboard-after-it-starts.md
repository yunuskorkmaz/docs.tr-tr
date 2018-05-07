---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: c864668026c4f8bb58a4d6c4c36f96fb07445a9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma
Bu örnek nasıl denetleneceğini gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra. Başlamak için bir <xref:System.Windows.Media.Animation.Storyboard> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanmak <xref:System.Windows.Media.Animation.BeginStoryboard>, nesneleri ve özellikleri hale getirmeyi ve film şeridi başlar animasyonları dağıtır. Size, <xref:System.Windows.Media.Animation.BeginStoryboard> belirterek bir isim kendi <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliği, onu bir denetlenebilir film şeridi yapın. Başladıktan sonra film şeridi etkileşimli olarak denetleyebilirsiniz.  
  
 İle birlikte aşağıdaki film şeridi eylemlerini kullanmak <xref:System.Windows.EventTrigger> film şeridi denetlemek için nesneleri.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridi duraklatır.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış film şeridi sürdürür.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Film şeridi hızını değiştirir.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Varsa, film şeridi dolgu süresinin sonuna ilerletir.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Film şeridi durdurur.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Kaynakları serbest bırakma film şeridi kaldırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkileşimli olarak film şeridi denetlemek için denetlenebilir film şeridi eylemleri kullanır.  
  
 **Not:** , kod kullanarak bir film şeridi denetleme bir örnek için bkz [bir film şeridi sonra onu başlatır ITS etkileşimli yöntemlerini kullanarak denetim](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Ek örnekler için bkz: [animasyon örnek Galerisi](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [Görsel Taslağı Başladıktan Sonra Etkileşimli Yöntemlerini Kullanarak Denetleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
