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
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095144"
---
# <a name="intercepting-input-from-the-stylus"></a>Ekran Kaleminden Gelen Girişi Önleme
<xref:System.Windows.Input.StylusPlugIns> mimarisi, <xref:System.Windows.Input.Stylus> giriş ve dijital mürekkep <xref:System.Windows.Ink.Stroke> nesnelerinin oluşturulması üzerinde alt düzey denetimi uygulamaya yönelik bir mekanizma sağlar. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıfı, özel davranışı uygulamanız ve en iyi performans için ekran kalemi aygıtından gelen veri akışına uygulamanız için bir mekanizma sağlar.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
- [Mimari](#Architecture)  
  
- [Ekran kalemi eklentilerini uygulama](#ImplementingStylusPlugins)  
  
- [InkCanvas 'a eklenti ekleme](#AddingYourPluginToAnInkCanvas)  
  
- [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Mimari  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>, [kalem girişine erişme ve düzenleme](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))konularında açıklanan [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) API 'lerinin gelişmidir.  
  
 Her <xref:System.Windows.UIElement>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>bir <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğine sahiptir. Oluşturulan <xref:System.Windows.Input.StylusPoint> verileri işlemek için bir öğenin <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğine <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ekleyebilirsiniz. <xref:System.Windows.Input.StylusPoint> veriler, sistem çizim tablası tarafından desteklenen <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> Point <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> verileri de dahil olmak üzere tüm özelliklerden oluşur.  
  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nesneleriniz, <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğine <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> eklediğinizde <xref:System.Windows.Input.Stylus> cihazdan gelen veri akışına doğrudan eklenir. <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonuna eklenen eklentilerin sırası, <xref:System.Windows.Input.StylusPoint> verileri alma sırasını belirler. Örneğin, girişi belirli bir bölgeye kısıtlayan bir filtre eklentisi ekler ve sonra yazıldığı şekilde hareketleri tanıyan bir eklenti eklerseniz, hareketleri tanıyan eklenti, filtrelenmiş <xref:System.Windows.Input.StylusPoint> verileri alır.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Ekran kalemi eklentilerini uygulama  
 Bir eklenti uygulamak için <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>bir sınıf türetebilirsiniz. Bu sınıf, <xref:System.Windows.Input.Stylus>veri akışını, ' dan geldiği şekilde uygulanır. Bu sınıfta <xref:System.Windows.Input.StylusPoint> verilerinin değerlerini değiştirebilirsiniz.  
  
> [!CAUTION]
> Bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir özel durum oluşturursa veya neden olursa uygulama kapanır. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> kullanan denetimleri kapsamlı test etmelisiniz ve yalnızca <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> özel durum oluşturmayacağından emin olmanız durumunda bir denetim kullanabilirsiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Input.Stylus> cihazdan geldiği gibi <xref:System.Windows.Input.StylusPoint> verilerdeki <xref:System.Windows.Input.StylusPoint.X%2A> ve <xref:System.Windows.Input.StylusPoint.Y%2A> değerlerini değiştirerek ekran kalemi girişini kısıtlayan bir eklentiyi gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>InkCanvas 'a eklenti ekleme  
 Özel eklentiyi kullanmanın en kolay yolu, InkCanvas 'dan türeyen bir sınıfı uygulamak ve <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliğine eklemektir.  
  
 Aşağıdaki örnek, mürekkebe filtre uygulayan özel bir <xref:System.Windows.Controls.InkCanvas> gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Uygulamanıza bir `FilterInkCanvas` ekler ve bunu çalıştırırsanız, Kullanıcı bir vuruş tamamlanana kadar mürekkebin bir bölgeyle sınırlı olmadığını fark edeceksiniz. Bunun nedeni, <xref:System.Windows.Controls.InkCanvas> bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> olan ve zaten <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonunun bir üyesi olan bir <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> özelliğine sahip olmasından kaynaklanır. <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonuna eklediğiniz özel <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> veri aldıktan sonra <xref:System.Windows.Input.StylusPoint> verileri alır. Sonuç olarak, <xref:System.Windows.Input.StylusPoint> veriler, Kullanıcı vuruşu sona erdirmek için kalemi kaldırıncaya kadar filtrelenmez. Kullanıcı çizerken mürekkebi filtrelemek için, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>önce `FilterPlugin` eklemeniz gerekir.  
  
 Aşağıdaki C# kod, mürekkebi çizmiş gibi filtreleyerek özel bir <xref:System.Windows.Controls.InkCanvas> gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Kendi <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıflarınızı türeterek ve <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> koleksiyonlara yerleştirerek dijital mürekkebinizin davranışını büyük ölçüde geliştirebilirsiniz. <xref:System.Windows.Input.StylusPoint> verilerine erişim elde edersiniz ve size <xref:System.Windows.Input.Stylus> girişi özelleştirme fırsatı vermiş olursunuz. <xref:System.Windows.Input.StylusPoint> verilerine düşük düzeyde erişim sahibi olduğunuzdan, uygulamanız için en iyi performansla birlikte mürekkep toplamayı ve işlemeyi uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
- [Kalem girişine erişme ve Işleme](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
