---
title: Mürekkep Giriş Denetimi Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 105a44f90c1c654a21fc8920a149ad63b2dabc99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323856"
---
# <a name="creating-an-ink-input-control"></a>Mürekkep Giriş Denetimi Oluşturma
Statik olarak mürekkebi işler ve özel bir denetim, dinamik olarak oluşturabilir. Mürekkep "tablet kaleminden flow" ve sonra mürekkep görüntülemek için eklenir, denetime tablet kalem yoluyla panodan yapıştırılan veya bir dosyasından yüklenen görünmesine neden olan bir kullanıcı bir fırça çizer gibi diğer bir deyişle, mürekkebi işler. Mürekkep dinamik olarak işlemek için Denetim kullanmalısınız bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Mürekkep statik olarak işlemek için ekran kalemi olay yöntemleri geçersiz kılmanız gerekir (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, ve <xref:System.Windows.UIElement.OnStylusUp%2A>) toplamak için <xref:System.Windows.Input.StylusPoint> veri vuruş oluşturmak ve bunları Ekle bir <xref:System.Windows.Controls.InkPresenter> (denetim üzerinde mürekkep işleyen).  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
-   [Nasıl yapılır: Ekran kalemi noktası verileri toplayıp mürekkep vuruşları oluşturma](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Nasıl yapılır: Denetiminiz fare girişi kabul etmek etkinleştirin](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Hepsini birleştirme](#PuttingItTogether)  
  
-   [Ek Eklentiler ve DynamicRenderers Kullanma](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Sonuç](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Nasıl yapılır: Ekran kalemi noktası verileri toplayıp mürekkep vuruşları oluşturma  
 Strokes toplar ve mürekkep yöneten bir denetim oluşturmak için aşağıdakileri yapın:  
  
1. Öğesinden bir sınıf türetin <xref:System.Windows.Controls.Control> veya sınıflardan birini türetilen <xref:System.Windows.Controls.Control>, gibi <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Ekleme bir <xref:System.Windows.Controls.InkPresenter> sınıfı ve kümesi <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini yeni <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Ekleme <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> , <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkPresenter> çağırarak <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> yöntemi ve ekleme <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu. Böylece <xref:System.Windows.Controls.InkPresenter> denetiminiz tarafından ekran kalemi noktası veriler toplanırken mürekkep görüntülenecek.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Geçersiz kılma <xref:System.Windows.UIElement.OnStylusDown%2A> yöntemi.  Bu yöntemde, ekran kalemi çağrısıyla yakalama <xref:System.Windows.Input.Stylus.Capture%2A>. Ekran kalemi yakalayarak denetiminiz almaya devam edecektir <xref:System.Windows.UIElement.StylusMove> ve <xref:System.Windows.UIElement.StylusUp> olayları ekran kalemi denetimin sınırları dışına olsa bile. Bu kesinlikle zorunlu ancak neredeyse her zaman iyi bir kullanıcı deneyimi için istenen değil. Yeni bir <xref:System.Windows.Input.StylusPointCollection> toplamak üzere <xref:System.Windows.Input.StylusPoint> veri. Son olarak, ilk ekleme <xref:System.Windows.Input.StylusPoint> veri <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Geçersiz kılma <xref:System.Windows.UIElement.OnStylusMove%2A> yöntemi ve ekleme <xref:System.Windows.Input.StylusPoint> veri <xref:System.Windows.Input.StylusPointCollection> daha önce oluşturduğunuz bir nesne.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Geçersiz kılma <xref:System.Windows.UIElement.OnStylusUp%2A> yöntemi ve yeni bir <xref:System.Windows.Ink.Stroke> ile <xref:System.Windows.Input.StylusPointCollection> veri. Yeni Ekle <xref:System.Windows.Ink.Stroke> için oluşturduğunuz <xref:System.Windows.Controls.InkPresenter.Strokes%2A> koleksiyonunu <xref:System.Windows.Controls.InkPresenter> kalemini bırakın.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Nasıl yapılır: Denetiminiz fare girişi kabul etmek etkinleştirin  
 Uygulamanıza önceki denetimi ekleyin, çalıştırın ve fare giriş aygıtı olarak kullanmak, vuruşları kalıcı olmadığını fark edeceksiniz. Kalıcı hale getirmek için vuruşları fare giriş cihazı olarak kullanıldığında, aşağıdakileri yapın:  
  
1. Geçersiz kılma <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> ve yeni bir <xref:System.Windows.Input.StylusPointCollection> olay gerçekleştiğinde farenin konumunun almak ve oluşturmak bir <xref:System.Windows.Input.StylusPoint> noktası verileri kullanarak ve ekleme <xref:System.Windows.Input.StylusPoint> için <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Geçersiz kılma <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi. Olay gerçekleştiğinde farenin konumunun almak ve oluşturmak bir <xref:System.Windows.Input.StylusPoint> noktası verileri kullanarak.  Ekleme <xref:System.Windows.Input.StylusPoint> için <xref:System.Windows.Input.StylusPointCollection> daha önce oluşturduğunuz bir nesne.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Geçersiz kılma <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> yöntemi.  Yeni bir <xref:System.Windows.Ink.Stroke> ile <xref:System.Windows.Input.StylusPointCollection> verileri ve yeni Ekle <xref:System.Windows.Ink.Stroke> için oluşturduğunuz <xref:System.Windows.Controls.InkPresenter.Strokes%2A> koleksiyonunu <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Hepsini birleştirme  
 Aşağıdaki örnek kullanıcı fare ya da bir kalem kullandığında, Mürekkep toplayan özel bir denetimdir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Ek Eklentiler ve DynamicRenderers Kullanma  
 InkCanvas gibi özel özel denetiminizi olabilir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve ek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> nesneleri. Bu ekleme <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu. Sırasını <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nesneler <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> işlendiğinde mürekkep görünümünü etkiler. Sahip olduğunuz varsayalım bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> adlı `dynamicRenderer` ve özel bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> adlı `translatePlugin` , tablet kalem mürekkebi kaydırır. Varsa `translatePlugin` ilk <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> içinde <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, ve `dynamicRenderer` ikinci kullanıcı kalemi hareket "akış" mürekkep uzaklığı. Varsa `dynamicRenderer` ilk, ve `translatePlugin` ikinci mürekkep değil uzak olabileceği kullanıcı kalemi kaldırıncaya kadar olan.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Ekran kalemi olay yöntemleri geçersiz kılarak mürekkebi işler ve toplar bir denetim oluşturabilirsiniz. Kendi denetiminizi oluşturarak kendi türetme <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıfları ve bunları içine <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, dijital mürekkep ile kodlamalardaki neredeyse herhangi bir davranış uygulayabilirsiniz. Erişiminiz <xref:System.Windows.Input.StylusPoint> veri olarak üretilir, özelleştirme fırsatı verir <xref:System.Windows.Input.Stylus> giriş ve ekranında uygulamanız için uygun şekilde işleyin. Alt düzey erişiminiz olduğundan <xref:System.Windows.Input.StylusPoint> veri mürekkep koleksiyonu ve uygulamanız için en iyi performans ile işleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
- [Erişim ve kalem girişi düzenleme](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
