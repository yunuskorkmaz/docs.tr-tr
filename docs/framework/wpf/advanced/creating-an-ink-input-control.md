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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186289"
---
# <a name="creating-an-ink-input-control"></a>Mürekkep Giriş Denetimi Oluşturma
Mürekİğİ dinamik ve statik olarak işleyen özel bir denetim oluşturabilirsiniz. Diğer bir deyişle, kullanıcı bir kontur çizerken mürekkebin tablet kaleminden "akış" gibi görünmesine ve tablet kalemi üzerinden tablet kalemi üzerinden veya bir dosyadan yüklendikten sonra mürekkebin görüntülenmesine neden olan bir kontur çizer. Mürekİğİ dinamik olarak işlemek için, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>denetiminizin bir . Mürekviyi statik olarak işlemek için, veri toplamak,<xref:System.Windows.UIElement.OnStylusDown%2A> <xref:System.Windows.UIElement.OnStylusMove%2A> <xref:System.Windows.UIElement.OnStylusUp%2A> <xref:System.Windows.Input.StylusPoint> konturoluşturmak ve bunları bir <xref:System.Windows.Controls.InkPresenter> (denetimdeki mürekvitleri oluşturan) eklemek için kalem olay yöntemlerini (, ve ) geçersiz kılmanız gerekir.  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
- [Nasıl Kullanılır: Kalem Puan Verilerini Topla ve Mürekkep Darbeleri Oluştur](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Nasıl Oynanır: Fareden Giriş Kabul Etmek İçin Denetiminizi Etkinleştirin](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Bir araya getirmek](#PuttingItTogether)  
  
- [Ek Eklentiler ve DynamicRenderers kullanma](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Sonuç](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Nasıl Kullanılır: Kalem Puan Verilerini Topla ve Mürekkep Darbeleri Oluştur  
 Mürekkep konturlarını toplayan ve yöneten bir denetim oluşturmak için aşağıdakileri yapın:  
  
1. Bir sınıftife <xref:System.Windows.Controls.Control> veya türetilen <xref:System.Windows.Controls.Control>sınıflardan <xref:System.Windows.Controls.Label>biri gibi .  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Sınıfa <xref:System.Windows.Controls.InkPresenter> bir ekleme ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği yeniye <xref:System.Windows.Controls.InkPresenter>ayarlayın.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Controls.InkPresenter> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.UIElement.StylusPlugIns%2A> Yöntemi çağırarak the to the'yi ekleyin ve koleksiyona ekleyin. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> Bu, <xref:System.Windows.Controls.InkPresenter> kalem noktası verileri denetiminiz tarafından toplanırken mürekyenin görüntülenmesini sağlar.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. <xref:System.Windows.UIElement.OnStylusDown%2A> Yöntemi geçersiz kılın.  Bu yöntemde, bir çağrı ile kalemi <xref:System.Windows.Input.Stylus.Capture%2A>yakalamak. Kalemi yakalayarak, kalem ilerlüse bile, denetiminiz almaya <xref:System.Windows.UIElement.StylusMove> devam edecek ve <xref:System.Windows.UIElement.StylusUp> olaylar kontrol ün sınırlarını terk eder. Bu kesinlikle zorunlu değildir, ama hemen hemen her zaman iyi bir kullanıcı deneyimi için istenir. Veri toplamak <xref:System.Windows.Input.StylusPointCollection> <xref:System.Windows.Input.StylusPoint> için yeni bir oluştur. Son olarak, ilk <xref:System.Windows.Input.StylusPoint> veri <xref:System.Windows.Input.StylusPointCollection>kümesini .  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. <xref:System.Windows.UIElement.OnStylusMove%2A> Yöntemi geçersiz kılın ve <xref:System.Windows.Input.StylusPoint> verileri <xref:System.Windows.Input.StylusPointCollection> daha önce oluşturduğunuz nesneye ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. <xref:System.Windows.UIElement.OnStylusUp%2A> Yöntemi geçersiz kılın ve <xref:System.Windows.Ink.Stroke> verilerle <xref:System.Windows.Input.StylusPointCollection> yeni bir oluşturma. Oluşturduğunuz <xref:System.Windows.Ink.Stroke> yeni sürümü <xref:System.Windows.Controls.InkPresenter.Strokes%2A> ve sürüm <xref:System.Windows.Controls.InkPresenter> kalemi yakalama koleksiyonuna ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Nasıl Oynanır: Fareden Giriş Kabul Etmek İçin Denetiminizi Etkinleştirin  
 Uygulamanıza önceki denetimi eklerseniz, çalıştırın ve fareyi giriş aygıtı olarak kullanırsanız, konturların kalıcı olmadığını fark esiniz. Fare giriş aygıtı olarak kullanıldığında konturları devam etmek için aşağıdakileri yapın:  
  
1. Geçersiz kılın <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> ve olay <xref:System.Windows.Input.StylusPointCollection> meydana geldiğinde farenin konumunu alın ve <xref:System.Windows.Input.StylusPoint> nokta verilerini kullanarak bir <xref:System.Windows.Input.StylusPoint> oluşturun <xref:System.Windows.Input.StylusPointCollection>ve yeni bir .  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. <xref:System.Windows.UIElement.OnMouseMove%2A> Yöntemi geçersiz kılın. Olay meydana geldiğinde farenin konumunu alın ve <xref:System.Windows.Input.StylusPoint> nokta verilerini kullanarak bir oluşturma.  Daha <xref:System.Windows.Input.StylusPoint> önce <xref:System.Windows.Input.StylusPointCollection> oluşturduğunuz nesneye ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> Yöntemi geçersiz kılın.  <xref:System.Windows.Input.StylusPointCollection> Verilerle <xref:System.Windows.Ink.Stroke> yeni bir oluşturma ve <xref:System.Windows.Ink.Stroke> oluşturduğunuz yeni <xref:System.Windows.Controls.InkPresenter.Strokes%2A> yi <xref:System.Windows.Controls.InkPresenter>koleksiyonuna ekleyin.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>Bir araya getirmek  
 Aşağıdaki örnek, kullanıcı fareyi veya kalemi kullandığında mürekkemi toplayan özel bir denetimdir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Ek Eklentiler ve DynamicRenderers kullanma  
 InkCanvas gibi, özel denetiminizde <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> özel ve ek nesneler olabilir. Bunları koleksiyona <xref:System.Windows.UIElement.StylusPlugIns%2A> ekleyin. Nesnelerin <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sırası işlendiğinde <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> mürekyenin görünümünü etkiler. Tablet kaleminden mürekkebatı dengeleyen bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> `dynamicRenderer` <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> çağrınız ve özel bir `translatePlugin` örneğiniz olduğunu varsayalım. Birinci, ikinci `dynamicRenderer` ise, kullanıcı kalemi hareket ettikçe "akan" mürekkep dengelenir. `translatePlugin` <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> Birinci `dynamicRenderer` ve `translatePlugin` ikinci ise, kullanıcı kalemi kaldırana kadar mürekkep mahsup edilmez.  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>Sonuç  
 Kalem olay yöntemlerini geçersiz kılarak mürekçe toplayan ve işleyen bir denetim oluşturabilirsiniz. Kendi denetiminizi oluşturarak, kendi <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıflarınızı türeterek ve <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>bunları içine ekleyerek, dijital mürekkeple akla gelebilecek hemen hemen her davranışı uygulayabilirsiniz. Oluşturulan <xref:System.Windows.Input.StylusPoint> verilere erişebilirsiniz ve bu da size girişi özelleştirme <xref:System.Windows.Input.Stylus> ve uygulamanız için uygun şekilde ekranda işleme fırsatı verir. Verilere bu kadar düşük düzeyde <xref:System.Windows.Input.StylusPoint> erişiminiz olduğundan, mürekkep toplamayı uygulayabilir ve uygulamanız için en iyi performansla işleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
- [Kalem Girişine Erişim ve Manipülasyon](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
