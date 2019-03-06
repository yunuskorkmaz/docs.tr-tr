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
ms.openlocfilehash: ce4c2bd48e819541d942c795307df36629ec05b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362636"
---
# <a name="custom-rendering-ink"></a>Özel İşleme Mürekkebi
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Bir fırça özelliği, boyutunu, rengini ve şekil gibi bir vuruş görünümünü belirtmenize olanak sağlar ancak ne ötesinde görünümünü özelleştirmek istediğiniz zamanlar olabilir <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> izin verin. Mürekkep tarafından işlenirken bir püskürtme kabı, Petrol boyama ve birçok başka etkileri görünüşünü özelleştirme isteyebilirsiniz. Windows Presentation Foundation (WPF), özel işleme mürekkebi özel bir uygulama tarafından sağlayan <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve <xref:System.Windows.Ink.Stroke> nesne.  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
-   [Mimari](#Architecture)  
  
-   [Dinamik bir işleyici uygulama](#ImplementingADynamicRenderer)  
  
-   [Özel vuruşları uygulama](#ImplementingCustomStrokes)  
  
-   [Özel bir InkCanvas Uygulama](#ImplementingACustomInkCanvas)  
  
-   [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Mimari  
 Mürekkep işleme, iki kez gerçekleşir; bir kullanıcı mürekkep yüzeyine ve vuruş sonra yeniden yazdığında mürekkep özellikli yüzeyine eklenir. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Kullanıcı tablet kalemi çizim tablasının üzerinde hareket ettiğinde mürekkebi işler ve <xref:System.Windows.Ink.Stroke> öğe eklendikten sonra kendisini işler.  
  
 Mürekkep dinamik olarak işlenirken uygulamak için üç sınıfı vardır.  
  
1.  **DynamicRenderer**: Türetilen bir sınıf uygulamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Bu sınıf özelleştirilmiş, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> çizildiğinde vuruş işleyen. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Mürekkep surface bile uygulama kullanıcı arabirimi (UI) iş parçacığı engellendiğinde mürekkep toplama görünmesi için ayrı bir iş parçacığı üzerinde işleme yok. İş parçacığı modeli hakkında daha fazla bilgi için bkz: [mürekkep iş parçacığı modeli](the-ink-threading-model.md). Bir vuruş dinamik olarak işleme özelleştirmek için geçersiz kılma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi.  
  
2.  **Fırça darbesi**: Türetilen bir sınıf uygulamak <xref:System.Windows.Ink.Stroke>. Bu sınıfın statik işlemesinden sorumludur <xref:System.Windows.Input.StylusPoint> içine dönüştürüldükten sonra verileri bir <xref:System.Windows.Ink.Stroke> nesne. Geçersiz kılma <xref:System.Windows.Ink.Stroke.DrawCore%2A> yöntemi statik vuruş işlemesinin emin olmak için dinamik işleme ile tutarlıdır.  
  
3.  **InkCanvas:** Türetilen bir sınıf uygulamak <xref:System.Windows.Controls.InkCanvas>. Özelleştirilmiş atama <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> özelliği. Geçersiz kılma <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> yöntemi ve özel bir vuruş ekleme <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği. Bu, mürekkep görünümünü tutarlı olmasını sağlar.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Dinamik bir işleyici uygulama  
 Rağmen <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> sınıftır, standart bir parçası [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]özelleştirilmiş işlemeyi daha fazlasını gerçekleştirmek için türetilen özelleştirilmiş bir dinamik Oluşturucu oluşturmalısınız <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve geçersiz kılma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi.  
  
 Aşağıdaki örnek, özelleştirilmiş gösterir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> , doğrusal gradyan fırça efekti ile mürekkep çizer.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Özel vuruşları uygulama  
 Türetilen bir sınıf uygulamak <xref:System.Windows.Ink.Stroke>. Bu sınıf işlenmesinden sorumludur <xref:System.Windows.Input.StylusPoint> içine dönüştürüldükten sonra verileri bir <xref:System.Windows.Ink.Stroke> nesne. Geçersiz kılma <xref:System.Windows.Ink.Stroke.DrawCore%2A> gerçek çizim yapmak için sınıf.  
  
 Stroke sınıfınız de özel veri kullanarak depolayabilirsiniz <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> yöntemi. Bu veriler kalıcı olduğunda vuruş verilerle depolanır.  
  
 <xref:System.Windows.Ink.Stroke> Sınıfı, isabet sınaması da gerçekleştirebilirsiniz. Ayrıca kendi isabet algoritması geçersiz kılarak sınama uygulayabilirsiniz <xref:System.Windows.Ink.Stroke.HitTest%2A> geçerli sınıfında yöntemi.  
  
 Aşağıdaki C# kod, özel bir gösterir <xref:System.Windows.Ink.Stroke> işleyen sınıfı <xref:System.Windows.Input.StylusPoint> 3B vuruş olarak veri.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Özel bir InkCanvas Uygulama  
 Özelleştirilmiş kullanmak için en kolay yolu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve vuruşu türetildiği bir sınıf uygulamak için <xref:System.Windows.Controls.InkCanvas> ve bu sınıflar kullanır. <xref:System.Windows.Controls.InkCanvas> Sahip bir <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> kullanıcının bunu yeniden çizilirken vuruş nasıl oluşturulacağını belirten özelliği.  
  
 Üzerinde strokes özel işleme bir <xref:System.Windows.Controls.InkCanvas> aşağıdakileri yapın:  
  
-   Türetilen bir sınıf oluşturmanız <xref:System.Windows.Controls.InkCanvas>.  
  
-   Özelleştirilmiş atama <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> özelliği.  
  
-   Geçersiz kılma <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> yöntemi. Bu yöntemde InkCanvas'a eklenen özgün vuruş kaldırın. Özel bir vuruş'ı oluşturun, ekleyin <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği ve yeni bir temel sınıfı çağırın <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> kontur içeren.  
  
 Aşağıdaki C# kod, özel bir gösterir <xref:System.Windows.Controls.InkCanvas> özelleştirilmiş kullanan sınıf <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve özel vuruşları toplar.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Bir <xref:System.Windows.Controls.InkCanvas> birden fazla aboneliğiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Birden çok ekleyebilirsiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> nesneleri için <xref:System.Windows.Controls.InkCanvas> ekleyerek <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Kendi türetilerek mürekkep görünümünü özelleştirebilirsiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, ve <xref:System.Windows.Controls.InkCanvas> sınıfları. Birlikte, bu sınıflar stroke'un Görünümü Kullanıcı vuruşu çizer ve toplandıktan sonra tutarlı olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
