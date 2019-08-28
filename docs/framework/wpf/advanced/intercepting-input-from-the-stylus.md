---
title: Ekran Kaleminden Gelen Girişi Önleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046323"
---
# <a name="intercepting-input-from-the-stylus"></a>Ekran Kaleminden Gelen Girişi Önleme
Mimari <xref:System.Windows.Input.StylusPlugIns> , giriş ve dijital mürekkep <xref:System.Windows.Ink.Stroke> nesnelerinin oluşturulması üzerinde <xref:System.Windows.Input.Stylus> alt düzey denetimi uygulamaya yönelik bir mekanizma sağlar. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Sınıfı, özel davranış uygulamanız için bir mekanizma sağlar ve en iyi performans için ekran kalemi aygıtından gelen verilerin akışına uygulanır.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
- [Mimari](#Architecture)  
  
- [Ekran kalemi eklentilerini uygulama](#ImplementingStylusPlugins)  
  
- [InkCanvas 'a eklenti ekleme](#AddingYourPluginToAnInkCanvas)  
  
- [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Mimari  
 , Microsoft [Windows XP Tablet PC Edition yazılım geliştirme seti 1,7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)' de [kalem girişine erişme ve düzenleme](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)konularında açıklanan StylusInput API 'lerinin evmidir. [](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>  
  
 Her <xref:System.Windows.UIElement> birinin bir <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğinesahiptir<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Verileri oluşturulduğu gibi işlemek <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.StylusPoint> için bir <xref:System.Windows.UIElement.StylusPlugIns%2A> öğenin özelliğine ekleyebilirsiniz. <xref:System.Windows.Input.StylusPoint>veriler, sistem çizim tablası tarafından desteklenen <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> veri noktası <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> verilerinin yanı sıra veriler de dahil olmak üzere tüm özelliklerden oluşur.  
  
 Nesneleriniz <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> , <xref:System.Windows.Input.Stylus> özelliğineeklediğinizdecihazdan<xref:System.Windows.UIElement.StylusPlugIns%2A> gelen veri akışına doğrudan eklenir. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.UIElement.StylusPlugIns%2A> Koleksiyona eklenen eklentilerin, verileri alma <xref:System.Windows.Input.StylusPoint> sırasını belirlemesi için bu sırayı belirler. Örneğin, girişi belirli bir bölgeye kısıtlayan bir filtre eklentisi ekler ve sonra yazıldığı şekilde hareketleri tanıyan bir eklenti eklerseniz, hareketleri tanıyan eklenti filtrelenmiş <xref:System.Windows.Input.StylusPoint> verileri alır.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Ekran kalemi eklentilerini uygulama  
 Bir eklenti uygulamak için, öğesinden <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>bir sınıf türetebilirsiniz. Bu sınıf, <xref:System.Windows.Input.Stylus>' den geldiği haliyle veri akışına uygulanır. Bu sınıfta, <xref:System.Windows.Input.StylusPoint> verilerin değerlerini değiştirebilirsiniz.  
  
> [!CAUTION]
> Bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> özel durum oluşturursa veya neden olursa uygulama kapanır. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ' İ kullanan ve yalnızca bir özel durum oluşturmayacak şekilde <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir denetim kullanan denetimleri iyice test etmelisiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint> verileri <xref:System.Windows.Input.StylusPoint.Y%2A> cihazdan<xref:System.Windows.Input.Stylus> geldiği şekilde değiştirerek, ekran kalemi girişini kısıtlayan bir eklentiyi gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>InkCanvas 'a eklenti ekleme  
 Özel eklentiyi kullanmanın en kolay yolu, InkCanvas 'dan türeyen bir sınıfı uygulamak ve <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğe eklemektir.  
  
 Aşağıdaki örnek, mürekkebe filtre uygulayan <xref:System.Windows.Controls.InkCanvas> bir özel gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Uygulamanıza bir `FilterInkCanvas` ekler ve bunu çalıştırırsanız, Kullanıcı bir vuruş tamamlanana kadar mürekkebin bir bölgeyle sınırlı olmadığını fark edeceksiniz. Bunun nedeni, öğesinin <xref:System.Windows.Controls.InkCanvas> bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> olan <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> ve zaten <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonun üyesi olan bir özelliğine sahip olmasından kaynaklanır. Koleksiyona eklediğiniz <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.StylusPoint> özel, verileri aldıktan sonra <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> verileri alır. <xref:System.Windows.UIElement.StylusPlugIns%2A> Sonuç olarak, <xref:System.Windows.Input.StylusPoint> bir vuruş sona erdirmek için, Kullanıcı kalemi kaldırıncaya kadar veriler filtrelenmez. Kullanıcı çizerken mürekkebi filtrelemek için, öğesinden `FilterPlugin` <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>önce eklemeniz gerekir.  
  
 Aşağıdaki C# kod, mürekkebi çizmiş <xref:System.Windows.Controls.InkCanvas> gibi filtreleyen bir özel gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Kendi <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıflarınızı türeterek ve <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> bunları koleksiyonlara ekleyerek dijital mürekkebinizin davranışını önemli ölçüde artırabilirsiniz. <xref:System.Windows.Input.StylusPoint> Verilerin oluşturulduğu gibi verilere erişebilirsiniz ve bu sayede <xref:System.Windows.Input.Stylus> girişi özelleştirme olanağı elde edersiniz. <xref:System.Windows.Input.StylusPoint> Verilere düşük düzeyde erişim sahibi olduğunuz için, uygulamanız için en iyi performansla birlikte mürekkep toplamayı ve işlemeyi uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
- [Kalem girişine erişme ve Işleme](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
