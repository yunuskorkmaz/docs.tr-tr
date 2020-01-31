---
title: Dijital Mürekkep toplama
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
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747032"
---
# <a name="collect-ink"></a>Mürekkep toplama

[Windows Presentation Foundation](../index.md) platformu, işlevselliğinin temel bir parçası olarak dijital mürekkep toplar. Bu konuda Windows Presentation Foundation (WPF) içindeki mürekkep koleksiyonu için yöntemler ele alınmaktadır.

## <a name="prerequisites"></a>Prerequisites

Aşağıdaki örnekleri kullanmak için, önce Visual Studio 'Yu ve Windows SDK yüklemeniz gerekir. WPF için nasıl uygulama yazılacağını de anlamanız gerekir. WPF kullanmaya başlama hakkında daha fazla bilgi için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.

## <a name="use-the-inkcanvas-element"></a>InkCanvas öğesini kullanma

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> öğesi WPF 'de mürekkep toplamanın en kolay yolunu sağlar. Mürekkep girişi almak ve göstermek için bir <xref:System.Windows.Controls.InkCanvas> öğesi kullanın. Mürekkep vuruşları oluşturmak için bir çizim tablasına etkileşim kuran bir ekran kalemi kullanarak genellikle mürekkep girmeniz gerekir. Ayrıca fare, bir ekran kalemi yerine kullanılabilir. Oluşturulan konturlar <xref:System.Windows.Ink.Stroke> nesne olarak temsil edilir ve hem programlı olarak hem de Kullanıcı girişi tarafından yönetilebilir. <xref:System.Windows.Controls.InkCanvas>, kullanıcıların var olan bir <xref:System.Windows.Ink.Stroke>seçmesini, değiştirmesini veya silmesini sağlar.

XAML kullanarak, ağaca bir **InkCanvas** öğesi eklemek kadar mürekkep toplamayı kolayca ayarlayabilirsiniz. Aşağıdaki örnek, Visual Studio 'da oluşturulan varsayılan WPF projesine bir <xref:System.Windows.Controls.InkCanvas> ekler:

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas** öğesi Ayrıca, daha önce her türlü xaml öğesine mürekkep ek açıklama özellikleri eklemenizi olanaklı hale getiren alt öğeleri de içerebilir. Örneğin, bir metin öğesine mürekkep özellikleri eklemek için bunu bir <xref:System.Windows.Controls.InkCanvas>alt öğesi yapmanız yeterlidir:

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Bir görüntüyü mürekkeple işaretlemek için destek eklemek oldukça kolaydır:

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>InkCollection modları

<xref:System.Windows.Controls.InkCanvas>, <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> özelliği aracılığıyla çeşitli giriş modları için destek sağlar.

### <a name="manipulate-ink"></a>Mürekkep işleme

<xref:System.Windows.Controls.InkCanvas> birçok mürekkep düzenlemesi işlemi için destek sağlar. Örneğin, <xref:System.Windows.Controls.InkCanvas> kalem arka silmeyi destekler ve işlevselliği öğesine eklemek için ek kod gerekmez.

#### <a name="selection"></a>Seçim

Seçim modunu ayarlamak <xref:System.Windows.Controls.InkCanvasEditingMode> özelliğini **Seçilecek**kadar basittir.

Aşağıdaki kod, bir <xref:System.Windows.Forms.CheckBox>değerine göre, Düzen modunu ayarlar:

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Mürekkep vuruşlarının görünümünü değiştirmek için <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> özelliğini kullanın. Örneğin, <xref:System.Windows.Ink.DrawingAttributes> <xref:System.Windows.Ink.DrawingAttributes.Color%2A> üyesi, işlenen <xref:System.Windows.Ink.Stroke>rengini ayarlar.

Aşağıdaki örnek, seçili vuruşların rengini kırmızı olarak değiştirir:

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özelliği, bir <xref:System.Windows.Controls.InkCanvas>oluşturulacak vuruşların yüksekliği, genişliği ve rengi gibi özelliklere erişim sağlar. <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>değiştirdikten sonra, <xref:System.Windows.Controls.InkCanvas> girilen tüm gelecek konturlar yeni özellik değerleriyle işlenir.

Arka plan kod dosyasında <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> değiştirmeye ek olarak, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri belirtmek için XAML söz dizimini kullanabilirsiniz.

Sonraki örnekte <xref:System.Windows.Ink.DrawingAttributes.Color%2A> özelliğinin nasıl ayarlanacağı gösterilmektedir. Bu kodu kullanmak için, Visual Studio 'da "HelloInkCanvas" adlı yeni bir WPF projesi oluşturun. *MainWindow. xaml* dosyasındaki kodu aşağıdaki kodla değiştirin:

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Sonra, MainWindow sınıfının içindeki arka plan kod dosyasına aşağıdaki düğme olay işleyicilerini ekleyin:

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Bu kodu kopyaladıktan sonra Visual Studio 'da **F5** ' e basarak programı hata ayıklayıcıda çalıştırın.

<xref:System.Windows.Controls.StackPanel> düğmeleri <xref:System.Windows.Controls.InkCanvas>üstüne nasıl yerleştirdiğine dikkat edin. Düğmelerin üst kısmında mürekkebi denemeye çalışırsanız, <xref:System.Windows.Controls.InkCanvas> düğmelerin arkasındaki mürekkebi toplar ve işler. Bunun nedeni, alt öğelerin aksine düğmelerin eşdüzey <xref:System.Windows.Controls.InkCanvas>. Ayrıca, düğmeler z düzeninde daha yüksektir, bu nedenle mürekkep bunların arkasında işlenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
