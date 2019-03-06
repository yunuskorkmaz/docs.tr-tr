---
title: 3B Dönüşümlere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 578c8061271e08e4eac1ec5f11c84e63a3fa37bd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361895"
---
# <a name="3-d-transformations-overview"></a>3B Dönüşümlere Genel Bakış
Bu konu, 3B modeller dönüştürmeleri uygulamak açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik sistemi. Dönüştürmeleri geliştiricinin yeniden konumlandırma, yeniden boyutlandırma ve bunları tanımlayan temel değerleri değiştirmeden modelleri yeniden yönlendirme sağlar.  
  

  
## <a name="3-d-coordinate-space"></a>3B koordinat  
 3B grafik içeriği [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bir öğedeki kapsüllenir <xref:System.Windows.Controls.Viewport3D>, iki boyutlu öğesi yapısında katılmak. Grafik sistemi Viewport3D diğer birçok gibi iki boyutlu bir görsel öğe olarak değerlendirir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D bir pencere olarak çalışır; bir Görünüm penceresi — üç boyutlu bir Sahne olarak. Daha doğru bir şekilde 3B Görünümü yansıtıldığı bir yüzeydir.  Diğer 2B çizim nesneleri aynı Sahne grafiği ile Viewport3D kullanabilseniz de, 2B ve 3B nesneleri Viewport3D içinde işleyemezsiniz. Aşağıdaki tartışmada Viewport3D öğesi tarafından tanımlanan koordinat yer alır.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Koordinat sistemi 2B grafikler için kaynak işleme yüzeyi (genellikle ekranın) sol üst köşesindeki içinde bulur. 2B sistemindeki pozitif x eksenindeki değerler sağa devam etmek ve pozitif y ekseni değer aşağı doğru devam eder. 3B koordinat sisteminde ancak kaynağı ekranın ortasında sağa pozitif x eksenindeki değerler ancak bunun yerine yukarı doğru devam ederek pozitif y değerleri ve dışa doğru kaynaktan alınan etmeden pozitif z ekseni değerleri bulunur Görüntüleyici.  
  
 ![Koordinat sistemleri](./media/coordsystem-1.png "CoordSystem-1")  
Koordinat sistemi karşılaştırma  
  
 Bu eksen tarafından tanımlanan alan başvuru çerçevesidir 3B nesneler için olan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Bu alandaki modelleri oluşturabilir ve ışıklar oluşturup bunları görüntülemek için kameralar gibi bu başvuru çerçevesidir ya da "dünya alanındaki," yerel dönüşümleri uyguladığınızda, oluşturduğunuz her model için referans çerçevesi ayırmak yararlıdır. Ayrıca, dünya alanındaki nesneleri tamamen farklı arayın veya hiç görünür olmaması, bağlı olarak, açık ve kamera ayarları, ancak kameranın konumu değiştirmez, dünya alanındaki nesnelerin konumunu unutmayın.  
  
## <a name="transforming-models"></a>Modelleri dönüştürme  
 Modeli oluşturduğunuzda, belirli bir konuma sahnedeki sahiptirler. Sahne döndürmek veya bunların boyutunu değiştirmek için bu modelleri hareket etmek için bu modelleri tanımlayan köşelerini değiştirmek pratik değildir. Bunun yerine, yalnızca 2B olduğu gibi, dönüştürmeleri modelleri için geçerlidir.  
  
 Her model nesnesi olan bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> ile taşıyabilir, yeniden yönlendirmek veya model yeniden boyutlandırma özelliği. Dönüşüm uyguladığınızda, etkili bir şekilde modelin tüm noktaları dönüştürme işlemi tarafından belirtilen seçtiğiniz vektör veya değer tarafından uzaklığı. Diğer bir deyişle, koordinat içinde denetleyebildiğimiz modeli olan ("alanı model") tanımlanmış ancak modelin geometri koordinat sisteminde ("dünya alanı") tüm sahnenin oluşturan değerlerini değiştirmezsiniz.  
  
## <a name="translation-transformations"></a>Çeviri Dönüşümleri  
 3B dönüşümlere soyut taban sınıfından devralan <xref:System.Windows.Media.Media3D.Transform3D>; bunlar afin dönüşüm sınıfları <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, ve <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B sistemi de sağlar bir <xref:System.Windows.Media.Media3D.MatrixTransform3D> sağlar sınıfını daha kısa bir matris işlemlerinde aynı dönüşümleri belirtin.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> tüm noktaları ile belirttiğiniz uzaklık vektör yönünde Model3D taşır <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, ve <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> özellikleri. Örneğin, bir köşe küpün (2,2,2) göz önünde bulundurulduğunda, bir uzaklık vektörü (0,1.6,1) bu (2,2,2) köşesini (2,3.6,3) taşıyabilir. Küpün köşe hala (2,2,2) içinde model alanı olmakla birlikte, böylece (2,2,2) içinde model alanı (köşesini 2,3.6,3) artık bu model alan dünya alanındaki ilişkisini dünya alanında değişti.  
  
 ![Çeviri şekil](./media/transforms-translate.png "dönüşümler Çevir")  
Uzaklık ile  
  
 Aşağıdaki kod örnekleri, bir çeviri uygulamak gösterilmektedir.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Ölçek dönüşümleri  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> Merkez noktasını başvuru içeren bir belirtilen ölçek vektör tarafından modelinin ölçeğini değiştirir. Model orantılı olarak modelin boyutunu değiştirmek için X, Y ve Z ekseni, aynı değeri olarak ölçeklenen bir Tekdüzen ölçek belirtin. Örneğin, dönüşümün ayarlamak <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 0,5 özelliklerine halves modelin boyutundan; aynı özellikleri 2 olarak ayarlamak, ölçeği, tüm üç eksen iki katına çıkar.  
  
 ![Tekdüzen ScaleTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
ScaleVector Örneği  
  
 Tekdüzen olmayan ölçek dönüştürme belirterek — X, Y ve Z değerleri tümü aynı olmayan bir ölçek dönüştürme — esnetme ya da bir veya iki boyutta diğerleri etkilenmeden bir modeli neden olabilir. Örneğin, ayarlamak <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 2 ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 1 dönüştürülmüş modelin yükseklik çift ancak X ve Z ekseni değişmeden kalmasına neden olur.  
  
 Varsayılan olarak, ScaleTransform3D Genişlet veya daralt kaynak (0,0,0) neden olur. Dönüştürmek istediğiniz model kaynaktan alınan değil, ancak kaynağını modelden ölçeklendirme modeli "yerinde." ölçeği Bunun yerine, modelin köşeler ölçeklendirme vektörü ile çarpıldığında ölçeklendirme işlemi model çevirme olarak ölçeklendirme etkisi olmaz.  
  
 ![Üç küpler ölçeği orta noktası belirtilen](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Ölçek merkezi örneği  
  
 "Yerinde" modeli ölçeklendirmek için merkezi modelinin ScaleTransform3D ayarlayarak belirtin <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> özellikleri. Bu grafik sistemi model alanı ölçeklendirir ve onu belirtilen Orta çevirir sağlar <xref:System.Windows.Media.Media3D.Point3D>. Kaynak modeli derlediyseniz ve farklı bir orta nokta belirtin, buna karşılık, ayrılmak kaynağa çevrilmiş modelini görmek bekler.  
  
## <a name="rotation-transformations"></a>Döndürme Dönüşümleri  
 3-b bir modelde birkaç farklı şekilde döndürebilirsiniz. Tipik döndürme dönüşümü bir eksen ve bir o ekseni etrafında döndürme açısını belirtir. <xref:System.Windows.Media.Media3D.RotateTransform3D> Sınıfı tanımlamanıza olanak sağlayan bir <xref:System.Windows.Media.Media3D.Rotation3D> ile kendi <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği. Ardından belirttiğiniz <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> ve <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> bu durumda Rotation3D özellikleri bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>dönüşüm tanımlamak için. Aşağıdaki örnekler bir model tarafından 60 derecenin Y ekseni etrafında döndürün.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Not:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B bir döndürme açısı pozitif değerini bir saat yönünün döndürme eksen hakkında sonuçlanır anlamına gelir sağ taraf yönelimli bir sistemdir.  
  
 Eksen açı döndürmeleri varsayar kaynağa döndürme için bir değer belirtilmezse <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, ve <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> RotateTransform3D özellikleri. Ölçeklendirme gibi döndürme modelin bütün koordinat dönüştüren unutmayın yardımcı olur. Modeli kaynak oluşturulmamış ya da önceden çevrilmiş döndürme "yerinde döndürmek yerine kaynağa pivot".  
  
 ![Yeni merkez noktası ile döndürme](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Belirtilen yeni Merkezi ile döndürme  
  
 "Yerinde" modeli döndürmek için modelin gerçek merkezi döndürme merkezini belirtin. Geometri genellikle kaynak modellendiği için genellikle bir dizi dönüştürme beklenen sonucu (ölçeklendirme) modeli, ilk boyutlandırma sonra yönünü (döndürme) ayarlayıp taşımak için istenen konumu (son alabilirsiniz Bunu çevirme).  
  
 ![X 60 derece döndürme&#45; ve y&#45;eksenleri](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Döndürme örneği  
  
 Eksen açı döndürmeleri statik dönüşümleri ve bazı animasyonların için iyi çalışır. Ancak, bir küp modelini 60 derecenin ardından 45 derece Z ekseni etrafında X ekseni etrafında döndürme göz önünde bulundurun. Bu dönüştürme, iki ayrı afin dönüşümler veya bir matris olarak tanımlayabilirsiniz. Ancak, bu şekilde tanımlanan bir döndürme sorunsuzca animasyon uygulamak zor olabilir. Başlangıç ve bitiş konumları tarafından her iki yöntemle hesaplanan modelin aynı olsa da, model tarafından gerçekleştirilen Ara konumları kesin değildir. Dördeyler işlem başlangıcı ve sonu bir döndürme arasında enterpolasyon için alternatif bir yolu temsil eder.  
  
 Bir dördey eksen 3B ve bu ekseni etrafında döndürme işlemini temsil eder. Örneğin, bir dördey (1,1,2) bir eksenini ve 50 derece temsil edebilir. Dördeyler power'döndürme, üzerlerinde gerçekleştirebileceğiniz iki işlem geldiği: oluşturma ve ilişkilendirme. Geometri için uygulanan iki Dördeyler oluşumunu "tarafından rotation2 geometri axis2 etrafında döndürme ve sonra rotation1 tarafından ile axis1 etrafında döndürün." anlamına gelir. Birleşim kullanarak iki döndürmenin sonucunu temsil eden tek bir dördey almak için geometri üzerinde birleştirebilirsiniz. Bir kesintisiz ve makul yolu bir eksen ve yönlendirmesini diğerine dördey ilişkilendirme hesaplayabilirsiniz olduğundan, özgün hesaplayabildiği birinden diğerine, sorunsuz bir geçiş sağlamak için animasyon olanak sağlayan enterpolasyon dönüştürme. Animasyon uygulamak istediğiniz modelleri için bir hedef belirtin <xref:System.Windows.Media.Media3D.Quaternion> kullanarak döndürme için bir <xref:System.Windows.Media.Media3D.QuaternionRotation3D> için <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği.  
  
## <a name="using-transformation-collections"></a>Dönüşüm koleksiyonları kullanma  
 Sahne oluştururken birden fazla dönüştürme bir modele uygulamak yaygındır. Dönüşümler ekleyin <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> koleksiyonunu <xref:System.Windows.Media.Media3D.Transform3DGroup> grubuna sınıfı dönüştüren rahatça çeşitli modellere uygulamak için. Genellikle, bir dönüştürme kadar her örneğe dönüşümler farklı bir dizi uygulayarak bir model kullanabilirsiniz şekilde birkaç farklı gruplardaki yeniden kullanmak uygundur. Dönüştürmeleri koleksiyona eklendiğinde sipariş önemli olduğunu unutmayın: koleksiyondaki dönüşümler uygulanmadan birinciden için son.  
  
## <a name="animating-transformations"></a>Dönüşümler animasyon ekleme  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 2B grafikler aynı zamanlama ve animasyon sisteme katılan 3-b uygulaması. Diğer bir deyişle, 3B Görünümü animasyon eklemek gibi modellerinin özelliklerine animasyon ekleme. Temel özellikleri doğrudan oynatmak mümkün olduğu halde konumunu veya modelleri görünümünü değiştirme dönüşümleri animasyon uygulamak genellikle daha kolay olur. Dönüştürmeler uygulanabilir olduğundan <xref:System.Windows.Media.Media3D.Model3DGroup> nesneleri ayrı ayrı modeller yanı sıra, tek bir Model3Dgroup alt kümesini ve diğer nesnelerin bir grubuna uygulamak olabilir.  Üzerinde arka plan bilgileri için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zamanlama ve animasyon sistemi bkz [animasyona genel bakış](animation-overview.md) ve [görsel taslaklara genel bakış](storyboards-overview.md).  
  
 İçinde bir nesneye animasyon ekleme için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bir zaman çizelgesi oluşturma, (gerçekten bazı özellik değerinde bir değişiklik zaman içinde) bir animasyon tanımlayın ve animasyon uygulamak istediğiniz özelliğini belirtin. Bu özellik, bir özelliği FrameworkElement olmalıdır. 3B görünümde tüm nesneler Viewport3D alt olduğundan, sahneye uygulamak istediğiniz herhangi bir animasyon tarafından hedeflenen Viewport3D özelliklerinin özelliklerdir. Söz dizimi ayrıntılı olabileceği için dikkatli bir şekilde, animasyonun özellik yolunda çalışmak önemlidir.  
  
 Yerinde bir nesneyi döndürmek için ancak daha fazla nesneyi görüntülemek için kullanıma sunmak için swinging hareketinin uygulamak istediğinizi varsayalım. Bir RotateTransform3D modeli için geçerlidir ve bir vektör döndürme başka bir eksen animasyon uygulamak isteyebilirsiniz. Aşağıdaki kod örneği, uygulama gösterir bir <xref:System.Windows.Media.Animation.Vector3DAnimation> dönüşümün Rotation3D eksen özelliğine modeliyle uygulanan dönüşümlerden birini olmasını RotateTransform3D varsayılarak bir <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Benzer bir sözdizimi taşımak veya nesneyi ölçeklemek için diğer dönüşüm özellikleri hedeflemek için kullanın.  Örneğin, geçerli olabilecek bir <xref:System.Windows.Media.Animation.Point3DAnimation> düzgün şekilde bir modeli neden bir ölçekleme dönüşümü ScaleCenter özelliğine.  
  
 Önceki örneklerde özelliklerini dönüştürme rağmen <xref:System.Windows.Media.Media3D.GeometryModel3D>, diğer modellere özelliklerini dönüştürmek mümkündür.  Işık nesnelerine uygulanan çevirileri animasyon ekleme gibi taşıma açık ve önemli ölçüde Modellerinizi görünümünü değiştirebilirsiniz gölge efektleri oluşturabilirsiniz.  
  
 Kamera modelleri de olduğundan, kamera özellikleri de dönüştürmek mümkündür.  Görünümü sahnenin kamera konumu veya düzlem uzaklıklarını dönüştürerek kesinlikle değiştirebilirsiniz ancak — aslında tüm Sahne projeksiyon dönüştürme — bu şekilde elde etkileri birçoğu kadar "visual" Görüntüleyicisi çoğaltılmasının anlamı olmayabilir olduğunu unutmayın Konum veya modelleri konumunu sahnedeki uygulanmış olarak dönüşümler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [2B dönüşümleri örneği](https://go.microsoft.com/fwlink/?LinkID=158252)
