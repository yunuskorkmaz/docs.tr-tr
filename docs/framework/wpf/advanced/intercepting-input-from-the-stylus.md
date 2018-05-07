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
ms.openlocfilehash: 813c5f6060b3a59358b286c93a9077debd41a746
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="intercepting-input-from-the-stylus"></a>Ekran Kaleminden Gelen Girişi Önleme
<xref:System.Windows.Input.StylusPlugIns> Mimarisi üzerinde alt düzey denetim uygulamak için bir mekanizma sağlar <xref:System.Windows.Input.Stylus> giriş ve dijital mürekkep oluşturulmasını <xref:System.Windows.Ink.Stroke> nesneleri. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Sınıfı özel davranışı uygulamak ve en iyi performans için Kalem aygıtından gelen veri akışı için bir mekanizma sağlar.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
-   [Mimari](#Architecture)  
  
-   [Kalem eklentileri uygulama](#ImplementingStylusPlugins)  
  
-   [Eklentinizin InkCanvas'a ekleme](#AddingYourPluginToAnInkCanvas)  
  
-   [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Mimari  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Evrimi olan [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) API'leri, açıklanan [erişme ve düzenleme kalem giriş](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), [Microsoft Windows XP Tablet PC Edition yazılımı Geliştirme Seti 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Her <xref:System.Windows.UIElement> sahip bir <xref:System.Windows.UIElement.StylusPlugIns%2A> olan özellik bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Ekleyebileceğiniz bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir öğenin <xref:System.Windows.UIElement.StylusPlugIns%2A> işlemek için özellik <xref:System.Windows.Input.StylusPoint> veri olarak oluşturulur. <xref:System.Windows.Input.StylusPoint> Veri oluşur dahil olmak üzere sistem dijital dönüştürücü tarafından desteklenen tüm özelliklerin <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> nokta verilerini yanı <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> veri.  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Nesneleri doğrudan gelen veri akışının içine yerleştirildiğinde <xref:System.Windows.Input.Stylus> eklediğinizde, aygıt <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> için <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği. İçinde eklentileri eklenir sipariş <xref:System.Windows.UIElement.StylusPlugIns%2A> derlemesindeki bunlar alma sırasını <xref:System.Windows.Input.StylusPoint> veri. Belirli bir bölgeye girişini kısıtlayan filtresi eklentisini ekleyin ve sonra bir eklenti yazıldığı gibi hareketleri tanıyan ekleyin, örneğin, hareketleri tanıyan eklenti filtrelenmiş karşılaşırsınız <xref:System.Windows.Input.StylusPoint> veri.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Kalem eklentileri uygulama  
 Bir eklentiyi uygulamak için öğesinden bir sınıf türetin <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Bu sınıf alanından gelir uygulanan o veri akışı aynıdır <xref:System.Windows.Input.Stylus>. Bu sınıf değerlerini değiştirebilirsiniz <xref:System.Windows.Input.StylusPoint> veri.  
  
> [!CAUTION]
>  Varsa bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> oluşturur veya bir özel durum, Uygulama kapanacak neden olur. Tüketen denetimleri kapsamlı olarak sınamalısınız bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve belirli yalnızca bir denetim kullanırsanız <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir özel durum oluşturmayacaksa.  
  
 Aşağıdaki örnek değiştirerek kalem girişini kısıtlayan bir eklentiyi gösterir <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> değerler <xref:System.Windows.Input.StylusPoint> veriler geldiğinde <xref:System.Windows.Input.Stylus> aygıt.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Eklentinizin InkCanvas'a ekleme  
 Kendi özel eklentinizi kullanmanın en kolay yolu, InkCanvas'dan türetilen bir sınıf uygulama ve kendisine eklemektir <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği.  
  
 Aşağıdaki örnek, bir özel gösterir <xref:System.Windows.Controls.InkCanvas> mürekkep filtreler.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Eklerseniz bir `FilterInkCanvas` çalışma ve uygulama, kullanıcı bir vuruş tamamlandıktan sonra mürekkep bir bölge içinde kısıtlanmış olmadığını görürsünüz. Bunun nedeni, <xref:System.Windows.Controls.InkCanvas> sahip bir <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> olan özellik bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve bir üye zaten <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu. Özel <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> eklediğiniz <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu alır <xref:System.Windows.Input.StylusPoint> sonra verileri <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> verileri alır. Sonuç olarak, <xref:System.Windows.Input.StylusPoint> veri filtrelenmez kadar sonra Kullanıcı vuruşu sonlandırmak için Kalem kaldırır. Kullanıcı onu çizer gibi mürekkep filtrelemek için eklemelisiniz `FilterPlugin` önce <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Aşağıdaki C# kodu özel gösterir <xref:System.Windows.Controls.InkCanvas> mürekkep filtre uygulayan çizilirken.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Kendi türetme tarafından <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıfları ve bunların içine ekleme <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> koleksiyonlar, dijital mürekkep davranışını önemli ölçüde artırabilir. Erişiminiz <xref:System.Windows.Input.StylusPoint> veri olarak oluşturulur, özelleştirme fırsatı verir <xref:System.Windows.Input.Stylus> giriş. Alt düzey erişiminiz olduğundan <xref:System.Windows.Input.StylusPoint> verileri, uygulamanız için mürekkep koleksiyonu ve en iyi performans işlemeyle uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş Mürekkep İşleme](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Verilere erişme ve kalem giriş düzenleme](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
