---
title: "Nasıl yapılır: Bileşik Şeklin Dolgusunu Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5730b930a4f863ad01fcb6153d9bfd8f700fdb92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Nasıl yapılır: Bileşik Şeklin Dolgusunu Denetleme
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Özelliği bir <xref:System.Windows.Media.GeometryGroup> veya <xref:System.Windows.Media.PathGeometry>, "bileşik şeklin verilen bir noktaya geometrinin parçası olup olmadığını belirlemek için kullandığı bir kuralı" belirtir. İki olası değerler için <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> ve <xref:System.Windows.Media.FillRule.Nonzero>. Aşağıdaki bölümlerde bu iki kuralın nasıl kullanılacağı açıklanmıştır.  
  
 **EvenOdd:** bu kural, bir nokta Tuvaldeki bir noktadan herhangi bir yönde sonsuza çizip içinde verilen şeklin yayın kestiği yol bölümlerinin sayısını inceleyerek dolgu bölgesi içinde olup olmadığını belirler. Bu sayı tek ise, noktanın içindedir; çift ise dışında noktasıdır.  
  
 Örneğin, aşağıdaki XAML Eşmerkezli çalma (hedef) bir dizi oluşan bileşik bir şekil oluşturur bir <xref:System.Windows.Media.GeometryGroup.FillRule%2A> kümesine <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Aşağıdaki çizimde önceki örnekte oluşturulan şekli gösterir.  
  
 ![Ekran görüntüsü: FillRule EvenOdd özelliği](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Yukarıdaki çizimde, merkez ve 3 değil doldurulur dikkat edin. Bu iki çalma birini içinde herhangi bir noktasından çizilmiş ray çift sayıda kesimleri geçirir olmasıdır. Aşağıdaki çizime bakın:  
  
 ![Diyagram: FillRule özelliği EvenOdd değeri](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **NonZero:** bu kural, bir nokta herhangi bir yönde sonsuza o noktadan itibaren Tuvaldeki bir çizim ve çizip şeklin bir bölümünün Yayı kestiği yerleri inceleyerek yolun dolgu bölgesi içinde olup olmadığını belirler. Sıfır sayısı ile başlayarak, ekleme her biri bir Segment kestiği ışını soldan sağa ve her biri çıkarmak için zaman zaman bir yol kesimi sağdan sola Yayı kestiği. Sonuç sıfır ise kesişimlerin sayım sonra sonra noktası dışında yoludur. Aksi halde, içindedir.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 Değerini Yukarıdaki örneği kullanarak <xref:System.Windows.Media.FillRule.Nonzero> için <xref:System.Windows.Media.GeometryGroup.FillRule%2A> aşağıdaki çizimde sonucunda sağlar:  
  
 ![Ekran görüntüsü: FillRule NonZero değeri](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Gördüğünüz gibi tüm çalma doldurulur. Tüm segmentler aynı yönde çalıştığından ve herhangi bir noktadan çizilmiş ray bir çapraz ya da daha fazla segment ve kesişimlerin toplamı sıfıra eşit değil budur. Örneğin, aşağıdaki çizimde, Kırmızı oklar çizilen kesimlerin yönünü temsil eder ve beyaz ok en içteki halka içindeki bir noktadan rasgele bir ışını temsil eder. Bölümünün Yayı soldan sağa kestiği çünkü yayın kestiği, her segment için sıfır değeri ile başlayan bir değeri, eklenir.  
  
 ![Diyagram: FillRule özelliği değeri NonZero'ya eşit](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Daha iyi davranışını göstermek için <xref:System.Windows.Media.FillRule.Nonzero> kural farklı yönlerde kesimine sahip daha karmaşık bir şekil gereklidir. Aşağıdaki XAML kodu ile oluşturulan dışında benzer bir şekil önceki örnek olarak oluşturur. bir <xref:System.Windows.Media.PathGeometry> yerine sonra bir <xref:System.Windows.Media.EllipseGeometry> dört Eşmerkezli yaylar oluşturan yerine tam olarak eşmerkezli daireler kapalı.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Aşağıdaki çizimde önceki örnekte oluşturulan şekli gösterir.  
  
 ![Ekran görüntüsü: FillRule NonZero özellik değeri](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Üçüncü Yayı Merkezi'nden doldurulmadı dikkat edin. Aşağıdaki çizimde bunun nedenini gösterir. Çizimde, Kırmızı oklar çizilen kesimlerin yönünü temsil eder. İki beyaz OK "dolu olmayan" bölge içindeki bir noktadan taşıdığınız gönderilen iki rasgele ışını temsil eder. Gösterimden görüldüğü gibi yolundaki kesimleri geçmesinden verilen ray değerleri sıfır toplamıdır. Yukarıda tanımlanan sıfır toplamını noktası geometri (dolgu parçası değil) bir parçası olan toplam sırasında olmadığı anlamına gelir *değil* sıfır negatif bir değer de dahil olmak üzere, geometri bir parçasıdır.  
  
 ![Diyagram: FillRule NonZero özellik değeri](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Not:** amacıyla <xref:System.Windows.Media.FillRule>, tüm şekiller kapalı olarak kabul edilir. Bir segmenti boşluk varsa, kapatmak için sanal bir çizgi çizin. Yukarıdaki örnekte halka içinde küçük boşluklar vardır. Bu verildiğinde, biri farklı bir sonuç vermek için boşluk üzerinden çalışan bir ray sonra başka bir yönde çalıştıran ray bekleyebilirsiniz. Büyütülmüş çizim biri bu boşluklar ve "sanal kesim" aşağıdadır (uygulama amacıyla çizilmiş kesim <xref:System.Windows.Media.FillRule>), kapatır.  
  
 ![Diyagram: FillRule için kesimler her zaman kapalıdır](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Örnek  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bileşik şekil oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Geometri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
