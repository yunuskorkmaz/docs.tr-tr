---
title: 'Nasıl yapılır: Özel Denetimden Mürekkep Seçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 5c9b2f3d64e4cbb309772d6a1d9fa88f589df84c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173608"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Nasıl yapılır: Özel Denetimden Mürekkep Seçme
Ekleyerek bir <xref:System.Windows.Ink.IncrementalLassoHitTester> özel denetiminizi kullanıcı benzer şekilde, Serbest Şekil aracı ile mürekkep seçebilmeniz için Denetim etkinleştirebilirsiniz <xref:System.Windows.Controls.InkCanvas> mürekkebi seçer.  
  
 Bu örnekte, mürekkep özellikli bir özel denetim oluşturma konusunda bilgi sahibi olduğunuz varsayılır.  Mürekkep giriş kabul eden özel bir denetim oluşturmak için bkz: [mürekkep giriş denetimi oluşturma](creating-an-ink-input-control.md).  
  
## <a name="example"></a>Örnek  
 Kullanıcı bir Serbest Şekil çizdiğinde <xref:System.Windows.Ink.IncrementalLassoHitTester> kullanıcı Serbest Şekil tamamlandıktan sonra hangi strokes Serbest Şekil yolunun sınırları içinde olacak tahmin eder.  Serbest Şekil yolunun sınırları içinde olacak şekilde belirlenir strokes, seçili olarak düşünülebilir.  Seçili vuruşların seçilmemiş olabilir.  Örneğin, kullanıcı Serbest Şekil çizim sırasında yön tersine döner <xref:System.Windows.Ink.IncrementalLassoHitTester> bazı vuruşları seçimden.  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> Başlatır <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> özel denetiminizin kullanıcı, serbest şekil çizme sırasında yanıt vermesini sağlayan olay.  Örneğin, kullanıcının seçer ve bunları seçili olanları kaldırdığında vuruşlarının görünümünü değiştirebilirsiniz.  
  
## <a name="managing-the-ink-mode"></a>Mürekkep modunu yönetme  
 Serbest Şekil, denetim üzerinde mürekkep farklı görünürse kullanıcıya yararlıdır. Bunu gerçekleştirmek için özel denetiminizi kullanıcı yazma ya da mürekkep seçme izlemek gerekir. İki değer içeren bir numaralandırmayı bildirmek için bunu yapmanın en kolay yolu olan: bir kullanıcı mürekkep ve kullanıcı mürekkep seçtiğini gösteren yazma belirtmek için.  
  
 [!code-csharp[HowToSelectInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Ardından, iki ekleyin <xref:System.Windows.Ink.DrawingAttributes> sınıfa: bir kullanıcının kullanıcı mürekkep seçtiğinde kullanacağıma mürekkep yazarken kullanılacak.  Oluşturucuda başlatmak <xref:System.Windows.Ink.DrawingAttributes> ve her iki <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> aynı olay işleyicisi olayları. Ardından <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> özelliği <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> mürekkep <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Seçim modunu kullanıma sunduğu özellik ekleyin. Kullanıcı seçim modu değiştiğinde ayarlamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> özelliği <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> uygun <xref:System.Windows.Ink.DrawingAttributes> nesnesi ve ardından yeniden <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> özelliğini <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Kullanıma sunma <xref:System.Windows.Ink.DrawingAttributes> özellikleri, böylece uygulamalar mürekkep ve seçim vuruşlarını görünümünü belirleyebilir.  
  
 [!code-csharp[HowToSelectInk#6](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Özelliği bir <xref:System.Windows.Ink.DrawingAttributes> değişiklikleri, nesne <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> iliştirilmesi gerekir <xref:System.Windows.Controls.InkPresenter>.  İçin olay işleyicisinde <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> olay ekleyemediği <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> için <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>IncrementalLassoHitTester kullanma  
 Oluşturma ve başlatma bir <xref:System.Windows.Ink.StrokeCollection> , seçili vuruşların içerir.  
  
 [!code-csharp[HowToSelectInk#8](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Kullanıcı bir fırça çizmek başladığında mürekkep veya Serbest Şekil seçili vuruşların seçimini kaldırın. Ardından, kullanıcı, bir serbest şekil çizme, oluşturun bir <xref:System.Windows.Ink.IncrementalLassoHitTester> çağırarak <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, abone <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> olay ve arama <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Bu kodu ayrı bir yöntem olabilir ve çağrılır <xref:System.Windows.UIElement.OnStylusDown%2A> ve <xref:System.Windows.UIElement.OnMouseDown%2A> yöntemleri.  
  
 [!code-csharp[HowToSelectInk#9](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Ekran kalemi işaret ekleme <xref:System.Windows.Ink.IncrementalLassoHitTester> sırada kullanıcının Serbest Şekil çizer.  Aşağıdaki yöntemi çağırın <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, ve <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> yöntemleri.  
  
 [!code-csharp[HowToSelectInk#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Tanıtıcı <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> kullanıcı seçer ve vuruş seçili olanları kaldırdığında geldiğinde olay.  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Sınıfında <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> ve <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> vuruşları özellikleri seçili olan ve seçili, sırasıyla.  
  
 [!code-csharp[HowToSelectInk#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Kullanıcı serbest şekil çizme tamamlandığında, aboneliğinizi <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> olay ve arama <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Hepsini birleştirme.  
 Aşağıdaki örnek, kullanıcının mürekkebi seçmesini sağlayan özel bir denetimdir.  
  
 [!code-csharp[HowToSelectInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [Mürekkep Giriş Denetimi Oluşturma](creating-an-ink-input-control.md)
