---
title: Mürekkep Toplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: d441f606a577a2c0506a0f9ae510b3ea1045bba9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541076"
---
# <a name="collecting-ink"></a>Mürekkep Toplama
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform dijital mürekkep işlevselliğini önemli bir parçası toplar. Bu konu Windows Presentation Foundation (WPF) mürekkep topluluğu için yöntemleri açıklar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Aşağıdaki örnekler kullanmak için önce yüklemelisiniz [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] ve [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Uygulamaları yazmak nasıl anlamanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. İle çalışmaya başlama hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="using-the-inkcanvas-element"></a>InkCanvas öğesi kullanma  
 <xref:System.Windows.Controls.InkCanvas> Öğesi sağlar mürekkep toplamak için en kolay yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.InkCanvas> Öğesi benzer [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) nesnesinin [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] ve önceki sürümleri.  
  
 Kullanım bir <xref:System.Windows.Controls.InkCanvas> mürekkep girişi almak ve görüntülemek için öğesi. Yaygın olarak mürekkep mürekkep vuruşları üretmek için dönüştürücü ile etkileşime giren bir kalem kullanımı ile de girin. Ayrıca, fare kalem yerine kullanılabilir. Oluşturulan vuruşları olarak temsil edilir <xref:System.Windows.Ink.Stroke> nesneleri ve hem program aracılığıyla kullanıcı girişi tarafından yönetilebilir. <xref:System.Windows.Controls.InkCanvas> Seçin, değiştirin veya varolan bir silmek kullanıcıların sağlayan <xref:System.Windows.Ink.Stroke>.  
  
 XAML kullanarak mürekkep koleksiyonunu eklediğiniz gibi kolayca ayarlayabileceğiniz bir `InkCanvas` , ağaç öğesi. Aşağıdaki örnek, bir <xref:System.Windows.Controls.InkCanvas> varsayılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturulan proje [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` Öğesi, alt öğeler, neredeyse her tür XAML öğesine mürekkep ek açıklama özellikleri eklemek olası hale getirerek de içerebilir. Örneğin, bir metin öğesine mürekkep özelliklerini eklemek için yalnızca bir alt kolaylaştırır bir <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 Bir resmi mürekkep ile işaretleme desteği ekleme oldukça kolaydır.  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>InkCollection Modları  
 <xref:System.Windows.Controls.InkCanvas> Aracılığıyla çeşitli giriş modları için destek sağlar, <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> özelliği.  
  
### <a name="manipulating-ink"></a>Mürekkep düzenleme  
 <xref:System.Windows.Controls.InkCanvas> Birçok mürekkep düzenleme işlemleri için destek sağlar. Örneğin, <xref:System.Windows.Controls.InkCanvas> destekler geri kalem arkası silme işlevselliği öğesine eklemek için gereken ek kod olmadan.  
  
#### <a name="selection"></a>Seçim  
 Seçim modunu ayarlama ayarı olarak basit <xref:System.Windows.Controls.InkCanvasEditingMode> özelliğine **seçin**. Aşağıdaki kod değerine göre düzenleme modunu ayarlar bir <xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 Kullanım <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> mürekkep vuruşları görünümünü değiştirmek için özellik. Örneğin, <xref:System.Windows.Ink.DrawingAttributes.Color%2A> üyesi <xref:System.Windows.Ink.DrawingAttributes> işlenen rengini ayarlar <xref:System.Windows.Ink.Stroke>. Aşağıdaki örnek, seçili vuruşları rengi kırmızı değiştirir.  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Özelliği yüksekliğini, genişlik ve oluşturulması için vuruşları rengi gibi özelliklere erişim sağlar bir <xref:System.Windows.Controls.InkCanvas>. Kere değiştirdiğinizde <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, girilen tüm gelecekteki vuruşları <xref:System.Windows.Controls.InkCanvas> yeni özellik değerleri ile işlenir.  
  
 Değiştirme yanı sıra <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> arka plan kod dosyasına belirtmek için XAML sözdizimini kullanabilirsiniz <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri. Aşağıdaki XAML kodu nasıl ayarlanacağını gösterir <xref:System.Windows.Ink.DrawingAttributes.Color%2A> özelliği. Bu kodu kullanmak için yeni bir oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Visual Studio 2005'te "HelloInkCanvas" adlı projesi. Window1.xaml dosyasındaki kodu aşağıdaki kodla değiştirin.  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 Ardından, Window1 sınıfı içindeki dosyanın arkasındaki kodda aşağıdaki düğmesi olay işleyicileri ekleyin.  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 Bu kodu kopyaladıktan sonra basın **F5** Microsoft Visual Studio 2005 hata ayıklayıcıda programı çalıştırmak için.  
  
 Bildirim nasıl <xref:System.Windows.Controls.StackPanel> düğmeleri üstüne yerleştirir <xref:System.Windows.Controls.InkCanvas>. Düğmeleri üst mürekkep çalışırsanız <xref:System.Windows.Controls.InkCanvas> mürekkep düğmelerin arkasında işler ve toplar. Düğmeleri eşdüzey öğelerinin olmasıdır <xref:System.Windows.Controls.InkCanvas> alt aksine. Ayrıca, mürekkep arkasına çizilir şekilde düğmeleri z sırayla daha yüksektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
