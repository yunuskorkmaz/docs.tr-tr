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
ms.openlocfilehash: 6c85855cda4f74d557539ed7aea3f725550512e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Nasıl yapılır: Özel Denetimden Mürekkep Seçme
Ekleyerek bir <xref:System.Windows.Ink.IncrementalLassoHitTester> özel denetim için bir kullanıcı mürekkep benzer şekilde, Serbest Şekil aracı ile seçebilmeniz için denetiminizi etkinleştirebilirsiniz <xref:System.Windows.Controls.InkCanvas> mürekkep bir Serbest Şekil ile seçer.  
  
 Bu örnekte, mürekkep etkin bir özel denetim oluşturma konusunda bilgi sahibi olduğunuz varsayılır.  Mürekkep girişi kabul özel bir denetim oluşturmak için bkz: [mürekkep giriş denetim oluşturma](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
## <a name="example"></a>Örnek  
 Kullanıcı bir Serbest Şekil çizer zaman <xref:System.Windows.Ink.IncrementalLassoHitTester> Serbest Şekil kullanıcı tamamlandıktan sonra hangi vuruşları Serbest Şekil yolunun sınırları içinde olacağını tahmin eder.  Serbest Şekil yolunun sınırları içinde olduğu belirlenen vuruşları, seçili olarak düşünülebilir.  Seçili vuruşları seçilmemiş olabilir.  Örneğin, kullanıcı Serbest Şekil çizim sırasında yönünü tersine çevirir <xref:System.Windows.Ink.IncrementalLassoHitTester> bazı vuruşları seçimini kaldırabilirsiniz.  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester> Başlatır <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> özel denetiminizin kullanıcı serbest şekil çizme sırasında yanıt vermesini sağlayan olay.  Örneğin, kullanıcı seçer ve bunları seçili olanları kaldırdığında gibi vuruşları görünümünü değiştirebilirsiniz.  
  
## <a name="managing-the-ink-mode"></a>Mürekkep modunu yönetme  
 Serbest Şekil denetiminizde mürekkep'den farklı görünüyorsa, kullanıcıya yardımcı olur. Bunu gerçekleştirmek için özel denetim kullanıcı yazma ya da mürekkep seçme izlemek gerekir. Bunu yapmanın en kolay yolu, iki değeri olan bir numaralandırma bildirmektir: bir kullanıcı mürekkep ve bir kullanıcı mürekkep seçtiğini göstermek için yazma belirtmek için.  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Sonra iki ekleyin <xref:System.Windows.Ink.DrawingAttributes> sınıfına: bir kullanıcı kullanıcı mürekkep seçtiğinde kullanmak üzere mürekkep yazdığında kullanın.  Oluşturucuda başlatma <xref:System.Windows.Ink.DrawingAttributes> ve her iki <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> aynı olay işleyicisi olayları. Ardından <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> özelliği <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> mürekkep <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Seçim modu kullanıma sunan bir özellik ekleyin. Kullanıcı seçim modunu değiştirdiğinde ayarlamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> özelliği <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> uygun <xref:System.Windows.Ink.DrawingAttributes> nesnesi ve ardından yeniden ekleyin <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> özelliğine <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Kullanıma <xref:System.Windows.Ink.DrawingAttributes> böylece uygulamaları mürekkep ve seçim vuruşlarını görünümünü belirleyebilir özellikleri olarak.  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Özelliği bir <xref:System.Windows.Ink.DrawingAttributes> nesnesi değişiklikleri <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> için yeniden gerekir <xref:System.Windows.Controls.InkPresenter>.  Olay işleyicisi içinde <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> olay, yeniden iliştirmeye <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> için <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>IncrementalLassoHitTester kullanma  
 Oluşturma ve başlatma bir <xref:System.Windows.Ink.StrokeCollection> seçili vuruşları içerir.  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Kullanıcı bir vuruş çizmeye başladığında, mürekkep veya Serbest Şekil tüm seçili vuruşları seçimini kaldırın. Ardından, kullanıcı bir serbest şekil çizme varsa, oluşturun bir <xref:System.Windows.Ink.IncrementalLassoHitTester> çağırarak <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, abone <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> olay ve arama <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Bu kod ayrı bir yöntem olabilir ve çağrılır <xref:System.Windows.UIElement.OnStylusDown%2A> ve <xref:System.Windows.UIElement.OnMouseDown%2A> yöntemleri.  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Kalem noktalarını eklemek <xref:System.Windows.Ink.IncrementalLassoHitTester> kullanıcı serbest şekil çizerken.  Aşağıdaki yöntemi çağırın <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, ve <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> yöntemleri.  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Tanıtıcı <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> kullanıcı seçer ve vuruşları seçili olanları kaldırdığında yanıt olay.  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Sınıfına sahip <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> ve <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> vuruşları özellikleri seçili olan ve sırasıyla seçilmemiş.  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Kullanıcı serbest şekil çizme tamamlandığında, aboneliğinizi <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> olay ve arama <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Hepsini birleştirme.  
 Aşağıdaki örnek, bir kullanıcının bir Serbest Şekil ile mürekkep seçmesini sağlayan özel bir denetimdir.  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [Mürekkep Giriş Denetimi Oluşturma](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
