---
title: "Mürekkep Giriş Denetimi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cfc6553fe9dd176d2aa557df906141c13a5f425
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-an-ink-input-control"></a>Mürekkep Giriş Denetimi Oluşturma
Statik olarak mürekkep işler ve özel bir denetim, dinamik olarak oluşturabilir. Diğer bir deyişle, "tablet kalem akışı" ve sonra mürekkep görüntülemek için eklenir denetimine tablet kalem aracılığıyla ya da panodan yapıştırılan veya bir dosyasından yüklenen görünmesi mürekkep neden olan bir kullanıcı bir vuruş çizer gibi mürekkep işler. Dinamik olarak mürekkep işlemek için denetiminizin kullanmalısınız bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Statik olarak mürekkep işlemek için Kalem olay yöntemleri geçersiz kılmanız gerekir (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, ve <xref:System.Windows.UIElement.OnStylusUp%2A>) toplamak için <xref:System.Windows.Input.StylusPoint> verileri, vuruş oluşturmak ve bunları Ekle bir <xref:System.Windows.Controls.InkPresenter> (denetimindeki mürekkep işleyen).  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
-   [Nasıl yapılır: kalem noktası verileri toplama ve mürekkep vuruşları oluşturma](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Nasıl yapılır: fare girişi kabul etmek, denetimini etkinleştir](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Araya getirme](#PuttingItTogether)  
  
-   [Ek Eklentiler ve DynamicRenderers Kullanma](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Sonuç](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Nasıl yapılır: kalem noktası verileri toplama ve mürekkep vuruşları oluşturma  
 Vuruşları toplar ve mürekkep yöneten bir denetim oluşturmak için aşağıdakileri yapın:  
  
1.  Öğesinden bir sınıf türetin <xref:System.Windows.Controls.Control> veya sınıflarından türetilen <xref:System.Windows.Controls.Control>, gibi <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Ekleme bir <xref:System.Windows.Controls.InkPresenter> sınıfı ve kümesi <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini yeni <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Attach <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> , <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkPresenter> çağırarak <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> yöntemi ekleyin <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu. Böylece <xref:System.Windows.Controls.InkPresenter> kalem noktası verilerini denetiminiz tarafından toplanan mürekkep görüntülemek için.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Geçersiz kılma <xref:System.Windows.UIElement.OnStylusDown%2A> yöntemi.  Bu yöntemde çağrısıyla ekran yakalama <xref:System.Windows.Input.Stylus.Capture%2A>. Kalem yakalayarak denetiminizi almaya devam edecektir <xref:System.Windows.UIElement.StylusMove> ve <xref:System.Windows.UIElement.StylusUp> olayları kalem denetimin sınırlarını ayrılsa bile. Bu kesinlikle zorunlu ancak iyi bir kullanıcı deneyimi için neredeyse her zaman istenen değil. Yeni bir <xref:System.Windows.Input.StylusPointCollection> toplamak için <xref:System.Windows.Input.StylusPoint> veri. Son olarak, ilk kümesi eklemek <xref:System.Windows.Input.StylusPoint> veri <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Geçersiz kılma <xref:System.Windows.UIElement.OnStylusMove%2A> yöntemi ekleyin <xref:System.Windows.Input.StylusPoint> veri <xref:System.Windows.Input.StylusPointCollection> daha önce oluşturduğunuz nesne.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Geçersiz kılma <xref:System.Windows.UIElement.OnStylusUp%2A> yöntemi ve yeni bir <xref:System.Windows.Ink.Stroke> ile <xref:System.Windows.Input.StylusPointCollection> veri. Yeni Ekle <xref:System.Windows.Ink.Stroke> için oluşturduğunuz <xref:System.Windows.Controls.InkPresenter.Strokes%2A> koleksiyonunu <xref:System.Windows.Controls.InkPresenter> ve Kalem yakalama bırakın.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Nasıl yapılır: fare girişi kabul etmek, denetimini etkinleştir  
 Önceki denetimi uygulamanıza eklemek, çalıştırmak ve fare giriş aygıtı olarak kullanma, vuruşları sürdürülmez fark edeceksiniz. Kalıcı hale getirmek için vuruşları fare giriş aygıtı olarak kullanıldığında, aşağıdakileri yapın:  
  
1.  Geçersiz kılma <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> ve yeni bir <xref:System.Windows.Input.StylusPointCollection> olay oluştuğunda farenin konumunu alın ve oluşturma bir <xref:System.Windows.Input.StylusPoint> noktası verilerini kullanarak ve ekleyin <xref:System.Windows.Input.StylusPoint> için <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Geçersiz kılma <xref:System.Windows.UIElement.OnMouseMove%2A> yöntemi. Olay oluştuğunda farenin konumunu alın ve oluşturma bir <xref:System.Windows.Input.StylusPoint> noktası verileri kullanarak.  Ekleme <xref:System.Windows.Input.StylusPoint> için <xref:System.Windows.Input.StylusPointCollection> daha önce oluşturduğunuz nesne.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Geçersiz kılma <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> yöntemi.  Yeni bir <xref:System.Windows.Ink.Stroke> ile <xref:System.Windows.Input.StylusPointCollection> veri ve yeni Ekle <xref:System.Windows.Ink.Stroke> için oluşturduğunuz <xref:System.Windows.Controls.InkPresenter.Strokes%2A> koleksiyonu <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Araya getirme  
 Aşağıdaki örnekte kullanıcı fare veya kalem kullandığında Mürekkep toplayan bir özel denetim ' dir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Ek Eklentiler ve DynamicRenderers Kullanma  
 InkCanvas gibi özel denetim özel olabilir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve ek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> nesneleri. Bu ekleme <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu. Sırasını <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nesnelerini <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> işlendiğinde mürekkep görünümünü etkiler. Sahip olduğunuz varsayalım bir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> adlı `dynamicRenderer` ve özel bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> adlı `translatePlugin` tablet kalem kaynaklı mürekkep kaydırır. Varsa `translatePlugin` ilk <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> içinde <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, ve `dynamicRenderer` saniyedir kullanıcı kalem taşınırken "akışlar" mürekkep kaydırılacağı miktar. Varsa `dynamicRenderer` ilk, ve `translatePlugin` ikinci olarak, mürekkep değil uzaklığı kullanıcı kalem kaldırır kadar değil.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Toplar ve Kalem olay yöntemleri geçersiz kılarak mürekkep işleyen bir denetim oluşturabilirsiniz. Kendi denetim oluşturarak, kendi türetme <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sınıfları ve bunları ekleme içine <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, neredeyse tüm dijital mürekkep ile hayal davranışları uygulayabilirsiniz. Erişiminiz <xref:System.Windows.Input.StylusPoint> veri olarak oluşturulur, özelleştirme fırsatı verir <xref:System.Windows.Input.Stylus> giriş ve uygulamanız için uygun şekilde ekranda işleme. Alt düzey erişiminiz olduğundan <xref:System.Windows.Input.StylusPoint> veri mürekkep koleksiyonu uygulamak ve uygulamanız için en uygun performans ile işlenemiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş mürekkep işleme](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Verilere erişme ve kalem giriş düzenleme](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
