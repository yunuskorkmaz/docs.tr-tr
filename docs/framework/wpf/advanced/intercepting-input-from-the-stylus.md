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
ms.openlocfilehash: 5384a49461886ba184a0a128467c864b37c0efc9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667046"
---
# <a name="intercepting-input-from-the-stylus"></a>Ekran Kaleminden Gelen Girişi Önleme
<xref:System.Windows.Input.StylusPlugIns> Mimari üzerinde alt düzey denetimi uygulamak için bir mekanizma sağlar <xref:System.Windows.Input.Stylus> giriş ve dijital mürekkep oluşturulmasını <xref:System.Windows.Ink.Stroke> nesneleri. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Sınıfı özel davranış uygulayan ve en iyi performans için ekran kalemi aygıttan gelen veri akışını uygulamak için bir mekanizma sağlar.  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
-   [Mimari](#Architecture)  
  
-   [Ekran kalemi eklentileri uygulama](#ImplementingStylusPlugins)  
  
-   [Eklentinizin InkCanvas'a ekleme](#AddingYourPluginToAnInkCanvas)  
  
-   [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Mimari  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Evrimidir [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) API'leri, açıklanan [erişme ve düzenleme kalem girişi](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), [Microsoft Windows XP Tablet PC Edition yazılımı Geliştirme Seti 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Her <xref:System.Windows.UIElement> sahip bir <xref:System.Windows.UIElement.StylusPlugIns%2A> olan özellik bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Ekleyebileceğiniz bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir öğenin <xref:System.Windows.UIElement.StylusPlugIns%2A> işlemek için özellik <xref:System.Windows.Input.StylusPoint> veriler oluşturulur. <xref:System.Windows.Input.StylusPoint> veriler dahil olmak üzere sistem çizim tablası tarafından desteklenen tüm özellikleri oluşur <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> veri noktası olarak <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> veri.  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Nesneleri doğrudan gelen veri akışının içine yerleştirildiğinde <xref:System.Windows.Input.Stylus> eklediğinizde, cihaz <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> için <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği. İçinde eklentiler eklenme sırası <xref:System.Windows.UIElement.StylusPlugIns%2A> derlemesindeki bunlar alma sırasını <xref:System.Windows.Input.StylusPoint> veri. Belirli bir bölgeye girişini kısıtlayan filtresi eklentisini ekleyin ve ardından bir eklenti yazıldıkları şekilde hareketleri tanıyan ekleyin, örneğin, hareketlerini tanıdığı eklenti filtrelenmiş alırsınız <xref:System.Windows.Input.StylusPoint> veri.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Ekran kalemi eklentileri uygulama  
 Bir eklenti uygulamak için öğesinden bir sınıf türetin <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Bu sınıf geldiğini uygulanan o veri akışını aynıdır <xref:System.Windows.Input.Stylus>. Bu sınıfta değerlerini değiştirebilir <xref:System.Windows.Input.StylusPoint> veri.  
  
> [!CAUTION]
>  Varsa bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> oluşturur veya bir özel durum, uygulama kapatılır neden olur. Tüketen denetimleri sınamanız bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve yalnızca belirli durumlarda bir denetimi kullanın <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir özel durum oluşturmaz.  
  
 Aşağıdaki örnek değiştirerek iğne girişi kısıtlayan bir eklenti gösterir <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> değerler <xref:System.Windows.Input.StylusPoint> verilerin geldiği <xref:System.Windows.Input.Stylus> cihaz.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Eklentinizin InkCanvas'a ekleme  
 InkCanvas türeyen bir sınıf uygulamak ve eklemek için kendi özel eklenti kullanmanın en kolay yolu olan <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği.  
  
 Aşağıdaki örnek bir özel gösterir <xref:System.Windows.Controls.InkCanvas> , mürekkep filtreler.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Eklerseniz bir `FilterInkCanvas` çalışma ve uygulama, kullanıcı bir fırça tamamlandıktan sonra mürekkep bir bölgeye kadar kısıtlı olmadığını görürsünüz. Bunun nedeni, <xref:System.Windows.Controls.InkCanvas> sahip bir <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> özelliğinin bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve zaten bir üye <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu. Özel <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> eklediğiniz <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu alır <xref:System.Windows.Input.StylusPoint> sonra verileri <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> verileri alır. Sonuç olarak, <xref:System.Windows.Input.StylusPoint> veri filtrelenmez kadar kullanıcı kalemi vuruşu sonlandırmak için kaldırıncaya sonra. Kullanıcı bunu çizer gibi mürekkep filtrelemek için eklemelisiniz `FilterPlugin` önce <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Aşağıdaki C# kodu özel bir gösterir <xref:System.Windows.Controls.InkCanvas> çizildiğinde mürekkep filtrelere.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Kendi türetme tarafından <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıfları ve ekleyerek <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> koleksiyonları, dijital mürekkep davranışını büyük ölçüde geliştirebilirsiniz. Erişiminiz <xref:System.Windows.Input.StylusPoint> veri olarak üretilir, özelleştirme fırsatı verir <xref:System.Windows.Input.Stylus> giriş. Alt düzey erişiminiz olduğundan <xref:System.Windows.Input.StylusPoint> veri, uygulamanız için mürekkep toplama ve işleme en iyi performans ile uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş Mürekkep İşleme](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
- [Erişim ve kalem girişi düzenleme](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
