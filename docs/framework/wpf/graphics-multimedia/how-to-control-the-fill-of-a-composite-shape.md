---
title: 'Nasıl yapılır: Bileşik Şeklin Dolgusunu Denetleme'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855903"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Nasıl yapılır: Bileşik Şeklin Dolgusunu Denetleme

Bir <xref:System.Windows.Media.GeometryGroup.FillRule%2A> veya'<xref:System.Windows.Media.PathGeometry>nin özelliği, bileşik şeklin, belirli bir noktanın geometrinin parçası olup olmadığını belirlemekte kullanacağı bir "kural" belirtir. <xref:System.Windows.Media.GeometryGroup> İçin <xref:System.Windows.Media.FillRule>iki olası değer vardır: <xref:System.Windows.Media.FillRule.EvenOdd> ve <xref:System.Windows.Media.FillRule.Nonzero>. Aşağıdaki bölümlerde bu iki kuralın nasıl kullanılacağı açıklanır.

**EvenOdd** Bu kural, bir noktanın, bu noktadan herhangi bir yönde sonsuza kadar bir ışın çizerek ve belirtilen şeklin içindeki yol segmentlerinin sayısını, ışın kesiştiği şekilde sayarak, bir noktanın Fill bölgesinde olup olmadığını belirler. Bu sayı tek ise, nokta içindedir; bile, nokta dışarıda olur.

Örneğin, aşağıdaki xaml, olarak <xref:System.Windows.Media.GeometryGroup.FillRule%2A> <xref:System.Windows.Media.FillRule.EvenOdd>ayarlanmış bir dizi eşmerkezli halkadan (hedef) oluşan bileşik bir şekil oluşturur.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

Aşağıdaki çizimde, önceki örnekte oluşturulan Şekil gösterilmektedir.

![Değişen renklerle, bir dizi eşmerkezli halkalardan oluşan bir daire.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

Önceki çizimde, Merkez ve üçüncü halkanın doldurulduğuna dikkat edin. Bunun nedeni, bu iki halkadan herhangi birinin içindeki herhangi bir noktadan çizilen bir ışın, hatta çok sayıda kesimden geçer. Aşağıdaki çizime bakın:

![Daire içinde çizilen EvenOdd ışınları gösteren diyagram.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**Sıfır olmayan** Bu kural, bu noktadan herhangi bir yönde sonsuza kadar bir ışın çizerek ve sonra şeklin bir segmentinin ışını kesen yerleri inceleyerek yolun Fill bölgesinde olup olmadığını belirler. Sıfır sayımla başlayarak, bir kesim her bir ışın bir ışını soldan sağa kesiştiği her seferinde bir kez ekleyin ve bir yol segmenti, bir yol segmentini sağdan sola kesişterek bir kez çıkarın. Çapraz çizgiler saydıktan sonra, sonuç sıfır ise, nokta yolun dışındadır. Aksi halde, içindedir.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

Önceki örneği kullanarak, <xref:System.Windows.Media.FillRule.Nonzero> için <xref:System.Windows.Media.GeometryGroup.FillRule%2A> değeri aşağıdaki çizimi sonuç olarak verir:

![Bir seri eş merkezli halkalardan oluşan bir daire, hepsi aynı renkle doldurulmuştur.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

Gördüğünüz gibi, tüm halkalar doldurulur. Bunun nedeni, tüm segmentlerin aynı yönde çalıştığı ve bu nedenle herhangi bir noktadan çizilen bir ışın bir veya daha fazla segment ve çapraz yönlerin toplamı sıfıra eşit olmayacaktır. Örneğin, aşağıdaki çizimde, kırmızı oklar parçaların çizildiği yönü temsil eder ve beyaz ok, en içteki halkadaki bir noktadan çalışan rastgele bir ışını temsil eder. Bir değeri sıfır ile başlayarak, bir ışın, bir değeri bir değer ile soldan sağa kesiştiğinden, bir değeri eklenir.

![FillRule Özellik değerini sıfırdan büyük değere eşit gösteren diyagram.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

<xref:System.Windows.Media.FillRule.Nonzero> Kural davranışlarını daha iyi göstermek için farklı yönlerde çalışan kesimlerle daha karmaşık bir şekil gereklidir. Aşağıdaki XAML kodu, bir <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.EllipseGeometry> önceki örnek olarak benzer bir şekil oluşturur; Bu, daha sonra tam olarak kapalı eşmerkezli daireler oluşturan dört adet eşmerkezli yay oluşturur.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

Aşağıdaki çizimde, önceki örnekte oluşturulan Şekil gösterilmektedir.

![Üçüncü yaya doldurulmamış renklerle, bir serinin eşmerkezli halkalardan oluşan bir daire.](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

Merkezden üçüncü yay doldurulduğuna dikkat edin. Aşağıdaki çizimde bunun neden olduğu gösterilmektedir. Çizimde, kırmızı oklar segmentlerin çizildiği yönü temsil eder. İki beyaz ok, "doldurulmamış" bölgedeki bir noktadan aşağı açılan iki rastgele ışını temsil eder. Çizimden görünebilirler, ancak yolundaki kesimleri geçen belirli bir ışın değerlerinin toplamı sıfırdır. Yukarıda tanımlandığı gibi, sıfır toplamı, bir negatif değer de dahil olmak üzere sıfır *olmayan* bir toplam değer geometrisinin bir parçası olsa da noktanın geometrinin (dolgunun parçası değil) bir parçası olmadığı anlamına gelir.

![Kesimleri kesişen rastgele ışınları gösteren diyagram.](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> Amaçları doğrultusunda <xref:System.Windows.Media.FillRule>tüm şekiller kapalı olarak kabul edilir. Kesimde bir boşluk varsa kapatmak için bir sanal çizgi çizin. Yukarıdaki örnekte halkalar üzerinde küçük boşluklar vardır. Bu, bir, başka bir yönde çalışan bir ışın daha sonra farklı bir sonuç vermek için boşluk boyunca çalışan bir ışın bekleyebilir. Aşağıda, bu boşluklardan birinin büyütülmüş bir gösterimi ve "sanal kesim" (uygulamanın uygulanması <xref:System.Windows.Media.FillRule>amacıyla çizilen segmenti).

![Her zaman kapatılan FillRule segmentlerini gösteren diyagram.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>Örnek

## <a name="see-also"></a>Ayrıca bkz.

- [Bileşik Şekil Oluşturma](how-to-create-a-composite-shape.md)
- [Geometriye Genel Bakış](geometry-overview.md)
