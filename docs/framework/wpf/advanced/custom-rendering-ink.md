---
title: Özel İşleme Mürekkebi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 2c627f757c1eccc37f57aea6880ffc8a362e5ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-rendering-ink"></a>Özel İşleme Mürekkebi
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Vuruş özelliğinin boyutunu, rengini ve şekil gibi bir vuruş görünümünü belirtmenize olanak verir, ancak ne ötesinde görünümünü özelleştirmek istediğiniz zamanlar olabilir <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> izin verin. Hava fırça, Petrol boyama ve diğer birçok efekt görünümünü işlemede tarafından mürekkep görünümünü özelleştirmek isteyebilirsiniz. Windows Presentation Foundation (WPF), özel işleme mürekkep özel bir uygulama tarafından verir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve <xref:System.Windows.Ink.Stroke> nesne.  
  
 Bu konu, aşağıdaki alt bölümleri içerir:  
  
-   [Mimari](#Architecture)  
  
-   [Dinamik işleyici uygulama](#ImplementingADynamicRenderer)  
  
-   [Özel vuruşları uygulama](#ImplementingCustomStrokes)  
  
-   [Özel InkCanvas Uygulama](#ImplementingACustomInkCanvas)  
  
-   [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Mimari  
 Mürekkep işleme iki kez oluşan; bir kullanıcı mürekkep yüzeyine ve vuruşun sonra yeniden yazdığında mürekkep etkin yüzeye eklenir. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Kullanıcı dijital dönüştürücü üzerinde tablet kalem taşıdığında mürekkep işler ve <xref:System.Windows.Ink.Stroke> bir öğe olarak eklendikten sonra kendisini işler.  
  
 Mürekkep dinamik olarak işlenirken uygulamak için üç sınıfları vardır.  
  
1.  **DynamicRenderer**: türeyen bir sınıf uygulama <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Bu sınıf özelleştirilmiş, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> çizilirken vuruşun işleyen. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> İçindekine yüzeyini uygulama kullanıcı arabirimi (UI) iş parçacığı engellendiğinde bile mürekkep toplamak görünmesi için ayrı bir iş parçacığı üzerinde işlemeyi yapar. İş parçacığı modeli hakkında daha fazla bilgi için bkz: [mürekkep iş parçacığı modeli](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md). Dinamik olarak vuruş işleme özelleştirmek için geçersiz kılma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi.  
  
2.  **Vuruş**: türeyen bir sınıf uygulama <xref:System.Windows.Ink.Stroke>. Bu sınıf, statik işlenmesinden sorumludur <xref:System.Windows.Input.StylusPoint> içine dönüştürüldükten sonra verileri bir <xref:System.Windows.Ink.Stroke> nesnesi. Geçersiz kılma <xref:System.Windows.Ink.Stroke.DrawCore%2A> Vuruşun statik işlemesinin emin olmak için yöntem dinamik işlemesi ile tutarlıdır.  
  
3.  **InkCanvas:** türeyen bir sınıf uygulama <xref:System.Windows.Controls.InkCanvas>. Özelleştirilmiş atamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> özelliği. Geçersiz kılma <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> yöntemi ve özel bir vuruş ekleyin <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği. Bu mürekkep görünümünü tutarlı olmasını sağlar.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Dinamik işleyici uygulama  
 Rağmen <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> sınıfı, standart bir parçası [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özelleştirilmiş işlemeyi daha gerçekleştirmek için türetilen özelleştirilmiş dinamik işleyicisini oluşturmalısınız <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve geçersiz kılma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi.  
  
 Aşağıdaki örnek özelleştirilmiş gösterir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> mürekkep doğrusal gradyan fırçası etkisi olmadan çizer.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Özel vuruşları uygulama  
 Türeyen bir sınıf uygulama <xref:System.Windows.Ink.Stroke>. Bu sınıf işlenmesinden sorumludur <xref:System.Windows.Input.StylusPoint> içine dönüştürüldükten sonra verileri bir <xref:System.Windows.Ink.Stroke> nesnesi. Geçersiz kılma <xref:System.Windows.Ink.Stroke.DrawCore%2A> Fiili çizimi yapmak için sınıf.  
  
 Stroke sınıfınız ayrıca özel verileri kullanarak depolayabilir <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> yöntemi. Bu veriler kalıcı olduğunda vuruş verisi ile depolanır.  
  
 <xref:System.Windows.Ink.Stroke> Sınıfı, isabet testi de gerçekleştirebilirsiniz. Algoritma kılarak kendi isabet sınama de uygulayabilir <xref:System.Windows.Ink.Stroke.HitTest%2A> geçerli sınıf içinde yöntemi.  
  
 Aşağıdaki C# kodu özel gösterir <xref:System.Windows.Ink.Stroke> işler sınıfı <xref:System.Windows.Input.StylusPoint> verisini 3-b vuruş olarak.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Özel InkCanvas Uygulama  
 Özelleştirilmiş kullanmak için en kolay yolu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve vuruşu türeyen bir sınıf uygulama için <xref:System.Windows.Controls.InkCanvas> ve bu sınıfları kullanır. <xref:System.Windows.Controls.InkCanvas> Sahip bir <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vuruşun kullanıcı onu çizerken nasıl işleneceğini belirten özellik.  
  
 Özel olarak üzerinde vuruşları işlemek bir <xref:System.Windows.Controls.InkCanvas> aşağıdakileri yapın:  
  
-   Türeyen bir sınıf oluşturun <xref:System.Windows.Controls.InkCanvas>.  
  
-   Özelleştirilmiş atamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> özelliği.  
  
-   Geçersiz kılma <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> yöntemi. Bu yöntemde, InkCanvas'a eklenen özgün vuruşu kaldırın. Özel bir vuruş oluşturun, ekleyin <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği ve çağrısı ile yeni bir temel sınıfı <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> özel vuruş içerir.  
  
 Aşağıdaki C# kodu özel gösterir <xref:System.Windows.Controls.InkCanvas> özelleştirilmiş kullanan sınıfı <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve özel vuruşları toplar.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Bir <xref:System.Windows.Controls.InkCanvas> birden fazla olabilir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Birden çok ekleyebilirsiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> nesneleri <xref:System.Windows.Controls.InkCanvas> ekleyerek <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Kendi türetme mürekkep görünümünü özelleştirebilirsiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, ve <xref:System.Windows.Controls.InkCanvas> sınıfları. Birlikte, bu sınıfları vuruşun görünümünü vuruşun kullanıcı çizer ve toplandıktan sonra tutarlı olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş Mürekkep İşleme](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
