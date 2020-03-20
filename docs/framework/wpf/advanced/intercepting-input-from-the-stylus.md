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
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181927"
---
# <a name="intercepting-input-from-the-stylus"></a>Ekran Kaleminden Gelen Girişi Önleme
Mimari, <xref:System.Windows.Input.StylusPlugIns> giriş ve dijital mürekkep <xref:System.Windows.Input.Stylus> <xref:System.Windows.Ink.Stroke> nesnelerinoluşturulması üzerinde düşük düzeyli denetimi uygulamak için bir mekanizma sağlar. Sınıf, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> özel davranışı uygulamanız ve en iyi performans için kalem aygıtından gelen veri akışına uygulamanız için bir mekanizma sağlar.  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
- [Mimari](#Architecture)  
  
- [Stylus Eklentilerinin Uygulanması](#ImplementingStylusPlugins)  
  
- [Eklentinizi Mürekkep Tuvaline Ekleme](#AddingYourPluginToAnInkCanvas)  
  
- [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Mimari  
 Kalem <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> [Girişine Erişim ve Manipüle](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))etmede açıklanan [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) API'lerinin evrimidir.  
  
 Her <xref:System.Windows.UIElement> biri <xref:System.Windows.UIElement.StylusPlugIns%2A> bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Verileri oluşturuldukça <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> işlemek <xref:System.Windows.Input.StylusPoint> için <xref:System.Windows.UIElement.StylusPlugIns%2A> bir öğenin özelliğine a ekleyebilirsiniz. <xref:System.Windows.Input.StylusPoint>veriler, sistem sayısallaştırıcısı tarafından desteklenen tüm özelliklerden, <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.Y%2A> nokta verileri ve <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> veriler de dahil olmak üzere oluşur.  
  
 Nesneyi <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğe eklediğinizde nesneleriniz doğrudan <xref:System.Windows.Input.Stylus> aygıttan gelen veri <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> akışına eklenir. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Eklentilerin <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyona eklenme sırası, veri alma <xref:System.Windows.Input.StylusPoint> sırasını belirler. Örneğin, girişi belirli bir bölgeye kısıtlayan bir filtre eklentisi eklerseniz ve sonra hareketleri yazılı olarak tanıyan bir eklenti eklerseniz, hareketleri tanıyan eklenti <xref:System.Windows.Input.StylusPoint> filtrelenmiş veri alır.  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>Stylus Eklentilerinin Uygulanması  
 Bir eklenti uygulamak için, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>bir sınıf türetmek. Bu sınıf o veri akışı ndan gelir olarak <xref:System.Windows.Input.Stylus>uygulanır. Bu sınıfta <xref:System.Windows.Input.StylusPoint> verilerin değerlerini değiştirebilirsiniz.  
  
> [!CAUTION]
> Bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> özel durum atar veya neden olursa, uygulama kapanır. Bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> tüketen denetimleri iyice test etmeli ve yalnızca <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir özel durum atmayacağından eminseniz bir denetim kullanmalısınız.  
  
 Aşağıdaki örnekte, cihazdan <xref:System.Windows.Input.StylusPoint.X%2A> gelirken <xref:System.Windows.Input.StylusPoint.Y%2A> <xref:System.Windows.Input.StylusPoint> verilerdeki ve değerleri değiştirerek kalem girişinin kısıtlanmasına <xref:System.Windows.Input.Stylus> neden olan bir eklenti gösterilmiş olur.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Eklentinizi Mürekkep Tuvaline Ekleme  
 Özel eklentinizi kullanmanın en kolay yolu, InkCanvas'tan türetilen bir sınıf uygulamak <xref:System.Windows.UIElement.StylusPlugIns%2A> ve özelliğine eklemektir.  
  
 Aşağıdaki örnek, mürekçe filtreleyen bir özel <xref:System.Windows.Controls.InkCanvas> gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Uygulamanıza bir `FilterInkCanvas` a ekler ve çalıştırArsanız, kullanıcı konturunuzu tamamlayana kadar mürekbin bir bölgeyle sınırlı olmadığını fark esiniz. Bunun nedeni, <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve zaten <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonun bir üyesi olan bir özelliğe sahip olmasıdır. Koleksiyona <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> eklediğiniz özel, <xref:System.Windows.Input.StylusPoint> verileri <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> aldıktan sonra alır. <xref:System.Windows.UIElement.StylusPlugIns%2A> Sonuç olarak, <xref:System.Windows.Input.StylusPoint> kullanıcı konturun sona erdirilmesi için kalemi kaldırana kadar veriler filtrelenmez. Kullanıcı çizerken mürekçe filtrelemek için, `FilterPlugin` <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>'den önce.  
  
 Aşağıdaki C# kodu, çizildikçe mürekçe filtreleyen bir özel <xref:System.Windows.Controls.InkCanvas> gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Sonuç  
 Kendi <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıflarınızı türeterek ve bunları <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> koleksiyonlara ekleyerek, dijital mürekİğİnizin davranışını büyük ölçüde geliştirebilirsiniz. Oluşturulan <xref:System.Windows.Input.StylusPoint> verilere erişebilirsiniz ve bu da size girişi özelleştirme <xref:System.Windows.Input.Stylus> fırsatı verir. <xref:System.Windows.Input.StylusPoint> Verilere bu kadar düşük düzeyde erişiminiz olduğundan, uygulamanız için en iyi performansla mürekkep toplama ve işleme uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
- [Kalem Girişine Erişim ve Manipülasyon](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
