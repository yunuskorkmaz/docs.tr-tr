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
ms.openlocfilehash: 0ceb831057a9a92aa7319d2004f04d7cf5ac820e
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111835"
---
# <a name="custom-rendering-ink"></a>Özel İşleme Mürekkebi
Konturözelliği, <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> bir konturun boyutunu, rengini ve şekli gibi bir konturgörünümünü belirtmenize olanak tanır, ancak görünümü <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> izin verenin ötesinde özelleştirmek istediğiniz zamanlar olabilir. Bir hava fırçası, yağlı boya ve diğer birçok efekt görünümünü görüntüleyerek mürekkep görünümünü özelleştirmek isteyebilirsiniz. Windows Sunu Temeli (WPF), özel <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve <xref:System.Windows.Ink.Stroke> nesne uygulayarak mürekçeoluşturmanızı sağlar.  
  
 Bu konu aşağıdaki alt bölümleri içerir:  
  
- [Mimari](#Architecture)  
  
- [Dinamik İşleme İşleme](#ImplementingADynamicRenderer)  
  
- [Özel Konturların Uygulanması](#ImplementingCustomStrokes)  
  
- [Özel Mürekkep Tuvali Uygulama](#ImplementingACustomInkCanvas)  
  
- [Sonuç](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Mimari  
 Mürekkep işleme iki kez oluşur; bir kullanıcı mürekkep yüzeyine mürekkep yazdığında ve konturdan sonra mürekkep etkin yüzeye tekrar eklenir. Kullanıcı <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> tablet kalemini sayısallaştırıcıya taşırken mürekkebin işlenir ve bir öğeye eklendikten sonra kendisini <xref:System.Windows.Ink.Stroke> işler.  
  
 Mürekİğİ dinamik olarak oluştururken uygulanacak üç sınıf vardır.  
  
1. **DynamicRenderer**: 'den <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>türeyen bir sınıf uygulayın. Bu sınıf, çekildiği gibi kontur işleyen özel <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> bir sınıftır. Ayrı <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> bir iş parçacığı üzerinde render yapar, böylece mürekkep yüzeyi uygulama kullanıcı arabirimi (UI) iş parçacığı engellendiğinde bile mürekkep toplamak için görünür. İş parçacığı modeli hakkında daha fazla bilgi için [Mürekkep İş parçacığı modeline](the-ink-threading-model.md)bakın. Kontur oluşturmayı dinamik olarak özelleştirmek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> için yöntemi geçersiz kılın.  
  
2. **Kontur**: <xref:System.Windows.Ink.Stroke>Türetilen bir sınıf uygulayın. Bu sınıf, <xref:System.Windows.Input.StylusPoint> bir <xref:System.Windows.Ink.Stroke> nesneye dönüştürüldükten sonra verilerin statik olarak işlenmesinden sorumludur. Konturun <xref:System.Windows.Ink.Stroke.DrawCore%2A> statik işlemesinin dinamik görüntülemeyle tutarlı olduğundan emin olmak için yöntemi geçersiz kılın.  
  
3. **Mürekkep Tuval:** 'den türeyen bir <xref:System.Windows.Controls.InkCanvas>sınıf uygulayın. Özelleştirilmiş <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> özelliği atayın. <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> Yöntemi geçersiz kılın ve <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özel bir kontur ekleyin. Bu, mürekçegörünümünün tutarlı olmasını sağlar.  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>Dinamik İşleme İşleme  
 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Sınıf [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]standart bir parçası olmasına rağmen , daha özel işleme gerçekleştirmek için, bu türlerden türetilmiş <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi geçersiz kılan özelleştirilmiş bir dinamik render oluşturmak gerekir.  
  
 Aşağıdaki örnek, doğrusal <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> degrade fırça efektiyle mürekçe çeken özelleştirilmiş bir örnek gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>Özel Konturların Uygulanması  
 'den türeyen bir <xref:System.Windows.Ink.Stroke>sınıf uygulayın. Bu sınıf, bir <xref:System.Windows.Input.StylusPoint> <xref:System.Windows.Ink.Stroke> nesneye dönüştürüldükten sonra verileri işlemekten sorumludur. Gerçek çizimi <xref:System.Windows.Ink.Stroke.DrawCore%2A> yapmak için sınıfı geçersiz kılın.  
  
 Kontur sınıfınız da <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> yöntemi kullanarak özel verileri depolayabilir. Bu veriler, kalıcı olduğunda kontur verileriyle birlikte depolanır.  
  
 Sınıf <xref:System.Windows.Ink.Stroke> isabet testi de gerçekleştirebilir. Ayrıca, geçerli sınıftayöntemi <xref:System.Windows.Ink.Stroke.HitTest%2A> geçersiz kılarak kendi isabet testi algoritmanızı da uygulayabilirsiniz.  
  
 Aşağıdaki C# kodu, <xref:System.Windows.Ink.Stroke> <xref:System.Windows.Input.StylusPoint> verileri 3B kontur olarak işleyen özel bir sınıf gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>Özel Mürekkep Tuvali Uygulama  
 Özelleştirilmiş <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve konturunuzu kullanmanın en kolay yolu, bu <xref:System.Windows.Controls.InkCanvas> sınıflardan türetilen ve kullanan bir sınıf uygulamaktır. Kullanıcı <xref:System.Windows.Controls.InkCanvas> çizim <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> yaparken konturun nasıl işlenirse nasıl işlenir belirten bir özelliği vardır.  
  
 Özel işleme konturlarını <xref:System.Windows.Controls.InkCanvas> yapmak için aşağıdakileri yapın:  
  
- <xref:System.Windows.Controls.InkCanvas>'den türeyen bir sınıf oluşturun.  
  
- Özelleştirilmiş <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> özelliğinizi <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> atayın.  
  
- <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> Yöntemi geçersiz kılın. Bu yöntemde, InkCanvas'a eklenen orijinal kontur kaldırın. Ardından özel bir kontur oluşturun, özel kontur <xref:System.Windows.Controls.InkCanvas.Strokes%2A> ekleyin ve <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> taban sınıfı özel kontur içeren yeni bir çağrı yla arayın.  
  
 Aşağıdaki C# kodu, özelleştirilmiş <xref:System.Windows.Controls.InkCanvas> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> bir sınıf kullanan ve özel konturlar toplayan özel bir sınıfı gösterir.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Bir <xref:System.Windows.Controls.InkCanvas> birden <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>fazla olabilir. Özelliğe ekleyerek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> birden çok <xref:System.Windows.Controls.InkCanvas> nesne ekleyebilirsiniz. <xref:System.Windows.UIElement.StylusPlugIns%2A>  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Sonuç  
 Kendi <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>ve <xref:System.Windows.Controls.InkCanvas> sınıflar türeterek mürekkep görünümünü özelleştirebilirsiniz. Bu sınıflar birlikte, kullanıcı kontur çizdiğinde ve toplandıktan sonra kontur görünümünün tutarlı olmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş Mürekkep İşleme](advanced-ink-handling.md)
