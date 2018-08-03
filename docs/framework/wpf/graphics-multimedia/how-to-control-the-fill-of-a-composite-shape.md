---
title: 'Nasıl yapılır: Bileşik Şeklin Dolgusunu Denetleme'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: a9a17434f11f432f6446e09bd853ed0d2f23fbe8
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "33563049"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Nasıl yapılır: Bileşik Şeklin Dolgusunu Denetleme
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Özelliği bir <xref:System.Windows.Media.GeometryGroup> veya <xref:System.Windows.Media.PathGeometry>, "bileşik şeklin belirli bir noktaya parçası olup olmadığını belirlemek için kullandığı bir kuralı" belirtir. Olası iki değeri vardır <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> ve <xref:System.Windows.Media.FillRule.Nonzero>. Aşağıdaki bölümlerde, bu iki kuralın kullanmayı anlatmaktadır.  
  
 **EvenOdd:** bu kural, bir nokta ışın bu noktadan herhangi bir yönde sonsuza çizerek ve kestiği belirli bir şeklin içindeki yol bölümlerinin sayısını sayma dolgu bölgesi içinde olup olmadığını belirler. Bu sayı tek ise, noktanın içindedir; çift ise noktası dışında.  
  
 Örneğin, aşağıdaki XAML ile Eşmerkezli halkalarının (hedef) bir dizi oluşan bileşik şekil oluşturur bir <xref:System.Windows.Media.GeometryGroup.FillRule%2A> kümesine <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Önceki örnekte oluşturulan şekli aşağıda gösterilmiştir.  
  
 ![Ekran: FillRule EvenOdd özelliği](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Yukarıdaki çizimde, 3 ve merkezi olmayan doldurulur dikkat edin. Parçaların bir çift sayı ya da bu iki halkalarının içinde herhangi bir noktasından çizilmiş bir ray geçirir olmasıdır. Aşağıdaki resme bakın:  
  
 ![Diyagram: FillRule özellik değeri EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **NonZero:** bu kural, bir nokta ışın bu noktadan herhangi bir yönde sonsuza çizerek ve ardından nerede çizip şeklin kestiği kestiği yerleri inceleyerek yolun dolgu bölgesinde olup olmadığını belirler. Sıfır sayısı ile başlayarak, ekleme her biri bir Segment aştığında ray soldan sağa ve her biri çıkarmak için zaman zaman bir yol kesimi sağdan sola ray aştığında. Sonuç sıfırsa kesişimlerin sayım sonra ardından yolu dışına noktasıdır. Aksi takdirde, içindedir.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 Yukarıdaki örnekte, değerini kullanarak <xref:System.Windows.Media.FillRule.Nonzero> için <xref:System.Windows.Media.GeometryGroup.FillRule%2A> sonuç olarak, aşağıdaki çizimde sağlar:  
  
 ![Ekran: FillRule NonZero değeri](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Gördüğünüz gibi tüm halkaları doldurulur. Tüm parçaları aynı yönde çalıştığından ve herhangi bir noktasından çizilen bir ray bir çapraz ya da daha fazla kesim ve kesişmeleri toplamı sıfırdan eşit değildir budur. Örneğin, aşağıdaki çizimde, kırmızı ok çizilen kesimlerin yönünü temsil eder ve bir noktasından en içteki halka rasgele bir ışını beyaz ok temsil eder. Segment soldan sağa kestiği çünkü kestiği, her bir kesim için sıfır değeri ile başlayarak, bir değeri, eklenir.  
  
 ![Diyagram: FillRule özellik değeri için NonZero eşit](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Daha iyi davranışını göstermek için <xref:System.Windows.Media.FillRule.Nonzero> farklı yönlerde parçalarla daha karmaşık bir şekil kuralı gereklidir. İle oluşturulan hariç, aşağıdaki XAML kodu benzer bir şekil önceki örnek olarak oluşturur. bir <xref:System.Windows.Media.PathGeometry> yerine sonra bir <xref:System.Windows.Media.EllipseGeometry> oluşturan dört Eşmerkezli yaylar yerine tamamen eşmerkezli daireler kapalı.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Önceki örnekte oluşturulan şekli aşağıda gösterilmiştir.  
  
 ![Ekran: FillRule özellik değeri NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Üçüncü yay Merkezi'nden doldurulmadı dikkat edin. Aşağıdaki çizimde, bu neden olduğunu gösterir. Çizimde, kırmızı ok çizilen kesimlerin yönünü temsil eder. İki beyaz okları dışarı Taşı "dolu olmayan" bölgesinde bir noktasından iki rastgele ışınlarındaki temsil eder. Gösterimden görülebileceği gibi yolu, segmentleri geçmeden belirli bir ray değerleri sıfır toplamıdır. Yukarıda tanımlanan sıfır toplamı noktası geometri (dolgu parçası olmayan) bir parçası olan bir toplama sırasında olmadığı anlamına gelir *değil* sıfır negatif bir değer de dahil olmak üzere, geometri bir parçasıdır.  
  
 ![Diyagram: FillRule özellik değeri NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Not:** amacıyla <xref:System.Windows.Media.FillRule>, tüm şekiller kapalı olarak kabul edilir. Bir segmenti boşluk varsa, kapatmak için hayali bir çizgi çizin. Yukarıdaki örnekte, küçük boşlukları halkaları vardır. Bunu göz önünde bulundurulduğunda, bir farklı bir sonuç sağlamak için boşluk üzerinden çalışan bir ray sonra başka bir yönde bir ray bekleyebilirsiniz. Bu boşlukları ve "sanal segment" biri genişletilmiş bir gösterimi aşağıda verilmiştir (uygulamak amacıyla çizilmiş segment <xref:System.Windows.Media.FillRule>), kapatır.  
  
 ![Diyagram: FillRule için kesimler her zaman kapalıdır](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Örnek  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bileşik Şekil Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
