---
title: WPF uygulamalarında mürekkep toplama
ms.date: 08/15/2018
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
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787450"
---
# <a name="collect-ink"></a>Mürekkep toplama

[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform dijital mürekkep işlevselliğini önemli bir parçası toplar. Bu konu, Windows Presentation Foundation (WPF) mürekkep koleksiyonu için yöntemleri açıklar.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki örnekleri kullanmak için önce Visual Studio yüklemeniz gerekir ve [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. WPF uygulamaları yazmak nasıl de anlamanız gerekir. WPF ile çalışmaya başlama hakkında daha fazla bilgi için bkz. [izlenecek yol: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>InkCanvas öğesi kullanma

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> Öğesi mürekkep ' WPF'de toplamak için kolay bir yol sağlar. Kullanım bir <xref:System.Windows.Controls.InkCanvas> mürekkep girişi almak ve görüntülemek için öğesi. Mürekkep vuruşlarını üretmek için dönüştürücü ile etkileşime giren bir ekran kalemi genelindeki mürekkep yaygın olarak girdiğiniz. Ayrıca, fare, ekran kalemi yerine kullanılabilir. Oluşturulan vuruşlar olarak temsil edilmektedir <xref:System.Windows.Ink.Stroke> nesneleri ve programlı ve kullanıcı tarafından giriş yönetilebilir. <xref:System.Windows.Controls.InkCanvas> Seçin, değiştirmek veya mevcut bir silme olanağı sağlayan <xref:System.Windows.Ink.Stroke>.

XAML kullanarak mürekkep koleksiyonunu ekleme gibi kolayca ayarlayabileceğiniz bir **InkCanvas** ağacınıza öğesi. Aşağıdaki örnek ekler bir <xref:System.Windows.Controls.InkCanvas> Visual Studio'da oluşturulan bir varsayılan WPF projesi:

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas** öğesi mürekkep ek açıklama özellikleri neredeyse tüm XAML öğe türüne eklemenizi olası hale getirerek, alt öğelerini içerebilir. Örneğin, bir metin öğesine mürekkep özelliklerini eklemek için yalnızca bir alt öğesi kolaylaştırır bir <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Mürekkep ile görüntü işaretleme desteği eklemek oldukça kolaydır:

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>InkCollection Modları

<xref:System.Windows.Controls.InkCanvas> Aracılığıyla çeşitli giriş modları için destek sağlar, <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> özelliği.

### <a name="manipulate-ink"></a>Mürekkep işleme

<xref:System.Windows.Controls.InkCanvas> Birçok mürekkep düzenleme işlemleri için destek sağlar. Örneğin, <xref:System.Windows.Controls.InkCanvas> destekler arka-ın-kalem siler ve hiçbir ek kod öğesine işlevselliği eklemek için gereklidir.

#### <a name="selection"></a>Seçim

Seçim modunu ayarlama ayarı olarak basit <xref:System.Windows.Controls.InkCanvasEditingMode> özelliğini **seçin**.

Aşağıdaki kod düzenleme moduna değerine göre ayarlar bir <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Kullanım <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> mürekkep vuruşlarını görünümünü değiştirmek için özellik. Örneğin, <xref:System.Windows.Ink.DrawingAttributes.Color%2A> üyesi <xref:System.Windows.Ink.DrawingAttributes> işlenen rengini ayarlar <xref:System.Windows.Ink.Stroke>.

Aşağıdaki örnek, seçili vuruşların rengini kırmızı değiştirir:

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Özelliği, yükseklik, genişlik ve oluşturulması için vuruşlarının rengi gibi özelliklere erişim sağlar bir <xref:System.Windows.Controls.InkCanvas>. Siz değiştirdikten sonra <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, girilen tüm gelecek vuruşlar <xref:System.Windows.Controls.InkCanvas> yeni özellik değerleri ile işlenir.

Değiştirme yanı sıra <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> arka plan kod dosyasında belirtmek için XAML söz dizimi kullanabilirsiniz <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri.

Sonraki örnekte nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Ink.DrawingAttributes.Color%2A> özelliği. Bu kodu kullanmak için Visual Studio'da "HelloInkCanvas" adlı yeni bir WPF projesi oluşturun. Değiştirin *MainWindow.xaml* dosyasındaki kodu aşağıdaki kodla:

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Ardından, aşağıdaki düğmeyi olay işleyicileri arka plan kod dosyasında, MainWindow sınıfının içine ekleyin:

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Bu kodu kopyaladıktan sonra basın **F5** hata ayıklayıcıda programı çalıştırmak üzere Visual Studio'da.

Bildirim nasıl <xref:System.Windows.Controls.StackPanel> düğmeleri üstüne yerleştirir <xref:System.Windows.Controls.InkCanvas>. Mürekkep düğmelerinin üst çalışırsanız <xref:System.Windows.Controls.InkCanvas> düğmelerin arkasında mürekkebi işler ve toplar. Eşdüzey düğmelerdir olmasıdır <xref:System.Windows.Controls.InkCanvas> aksine alt öğeleri. Ayrıca, mürekkep arkasına işlenebilmesi düğmeleri z düzeninde daha yüksektir.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>