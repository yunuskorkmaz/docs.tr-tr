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
ms.openlocfilehash: 98b2abf813a232e36b80683254174b12b97659bb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095222"
---
# <a name="creating-an-ink-input-control"></a>Mürekkep Giriş Denetimi Oluşturma
Mürekkebi dinamik ve statik olarak işleyen özel bir denetim oluşturabilirsiniz. Diğer bir deyişle, mürekkebi bir kullanıcı olarak işle, mürekkebin tablet kalemden "Flow" gibi görünmesine neden olur ve tablet kalemi aracılığıyla, panodan yapıştırılmış veya bir dosyadan yüklendikten sonra mürekkebi görüntüler. Mürekkebi dinamik olarak işlemek için denetiminizin bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>kullanması gerekir. Mürekkebi statik olarak işlemek için, ekran kalemi olay yöntemlerini (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>ve <xref:System.Windows.UIElement.OnStylusUp%2A>) geçersiz kılmanız gerekir, bu sayede <xref:System.Windows.Input.StylusPoint> verileri toplayıp, konturlar oluşturabilir ve bunları bir <xref:System.Windows.Controls.InkPresenter> (denetimde mürekkebi oluşturur) ekleyebilirsiniz.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
- [Nasıl yapılır: ekran kalemi noktası verilerini toplama ve mürekkep vuruşları oluşturma](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Nasıl yapılır: fareden girişi kabul etmek için denetiminizi etkinleştirme](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Birlikte yerleştirme](#PuttingItTogether)  
  
- [Ek eklentiler ve DynamicRenderers kullanma](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Sonuç](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Nasıl yapılır: ekran kalemi noktası verilerini toplama ve mürekkep vuruşları oluşturma  
 Mürekkep vuruşlarını toplayıp yöneten bir denetim oluşturmak için aşağıdakileri yapın:  
  
1. <xref:System.Windows.Controls.Control> bir sınıf veya <xref:System.Windows.Controls.Label>gibi <xref:System.Windows.Controls.Control>türetilmiş sınıflardan birini türetebilirsiniz.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Sınıfa bir <xref:System.Windows.Controls.InkPresenter> ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini yeni <xref:System.Windows.Controls.InkPresenter>olarak ayarlayın.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> yöntemini çağırarak <xref:System.Windows.Controls.InkPresenter> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> ekleyin ve <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> koleksiyonuna <xref:System.Windows.UIElement.StylusPlugIns%2A> ekleyin. Bu, ekran kalemi noktası verileri denetiminiz tarafından toplandığından <xref:System.Windows.Controls.InkPresenter> mürekkebin görüntülenmesini sağlar.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. <xref:System.Windows.UIElement.OnStylusDown%2A> yöntemini geçersiz kılın.  Bu yöntemde, <xref:System.Windows.Input.Stylus.Capture%2A>bir çağrısıyla ekran kalemini yakalayın. Ekran kalemi yakalanarak, ekran kalemi denetimin sınırlarının dışına çıktığında bile denetim <xref:System.Windows.UIElement.StylusMove> ve <xref:System.Windows.UIElement.StylusUp> olaylarını almaya devam edecektir. Bu kesinlikle zorunlu değildir, ancak neredeyse her zaman iyi bir kullanıcı deneyimi için istenir. <xref:System.Windows.Input.StylusPoint> verileri toplamak için yeni bir <xref:System.Windows.Input.StylusPointCollection> oluşturun. Son olarak, <xref:System.Windows.Input.StylusPoint> verilerinin başlangıç kümesini <xref:System.Windows.Input.StylusPointCollection>ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. <xref:System.Windows.UIElement.OnStylusMove%2A> yöntemini geçersiz kılın ve daha önce oluşturduğunuz <xref:System.Windows.Input.StylusPointCollection> nesnesine <xref:System.Windows.Input.StylusPoint> verileri ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. <xref:System.Windows.UIElement.OnStylusUp%2A> yöntemini geçersiz kılın ve <xref:System.Windows.Input.StylusPointCollection> verileriyle yeni bir <xref:System.Windows.Ink.Stroke> oluşturun. Oluşturduğunuz yeni <xref:System.Windows.Ink.Stroke>, <xref:System.Windows.Controls.InkPresenter> <xref:System.Windows.Controls.InkPresenter.Strokes%2A> koleksiyonuna ekleyin ve Stilus Capture sürümünü yayınlayın.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Nasıl yapılır: fareden girişi kabul etmek için denetiminizi etkinleştirme  
 Uygulamanıza önceki denetimi eklerseniz, çalıştırın ve fareyi bir giriş cihazı olarak kullanırsanız, vuruşların kalıcı olmadığını fark edersiniz. Fare giriş cihazı olarak kullanıldığında konturları kalıcı hale getirmek için şunları yapın:  
  
1. <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> geçersiz kılın ve yeni bir <xref:System.Windows.Input.StylusPointCollection> oluşturun ve olay oluştuğunda fare konumunu alın ve nokta verilerini kullanarak bir <xref:System.Windows.Input.StylusPoint> oluşturun ve <xref:System.Windows.Input.StylusPoint> <xref:System.Windows.Input.StylusPointCollection>ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemini geçersiz kılın. Olay oluştuğunda fare konumunu alın ve nokta verilerini kullanarak bir <xref:System.Windows.Input.StylusPoint> oluşturun.  Daha önce oluşturduğunuz <xref:System.Windows.Input.StylusPointCollection> nesnesine <xref:System.Windows.Input.StylusPoint> ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> yöntemini geçersiz kılın.  <xref:System.Windows.Input.StylusPointCollection> verilerle yeni bir <xref:System.Windows.Ink.Stroke> oluşturun ve oluşturduğunuz yeni <xref:System.Windows.Ink.Stroke>, <xref:System.Windows.Controls.InkPresenter><xref:System.Windows.Controls.InkPresenter.Strokes%2A> koleksiyonuna ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Birlikte yerleştirme  
 Aşağıdaki örnek, Kullanıcı fare veya kalemi kullandığında mürekkep toplayan özel bir denetimdir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Ek eklentiler ve DynamicRenderers kullanma  
 InkCanvas gibi özel denetiminizin özel <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve ek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> nesneleri olabilir. Bunları <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonuna ekleyin. <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nesnelerinin sırası, her işlendiğinde mürekkebin görünümünü etkiler. `dynamicRenderer` adlı bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> olduğunu ve mürekkebi tablet kalemden kaydırın `translatePlugin` adlı özel bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> olduğunu varsayalım. `translatePlugin` <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>ilk <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve `dynamicRenderer` ikinci ise, Kullanıcı kalemi taşıdıkça "akışlar" olan mürekkep de kaydırılır. `dynamicRenderer` ilk ve `translatePlugin` ikinci ise, Kullanıcı kalemi kaldırıncaya kadar mürekkep de kaydırılır.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Ekran kalemi olay yöntemlerini geçersiz kılarak, mürekkebi toplayıp işleyen bir denetim oluşturabilirsiniz. Kendi denetiminizi oluşturarak, kendi <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıflarınızı türeterek ve <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>içine ekleyerek, dijital mürekkeple neredeyse tüm davranışları kodlamalardaki uygulayabilirsiniz. <xref:System.Windows.Input.StylusPoint> verilerine erişim elde edersiniz. böylece, <xref:System.Windows.Input.Stylus> girişi özelleştirme ve bu uygulamayı uygulamanız için uygun şekilde ekranda işleme fırsatı vermiş olursunuz. <xref:System.Windows.Input.StylusPoint> verilerine alt düzey erişiminiz olduğundan, mürekkep toplamayı uygulayabilir ve uygulamanız için en iyi performansı elde edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
- [Kalem girişine erişme ve Işleme](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
