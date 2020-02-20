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
ms.openlocfilehash: 983ae51fb74255b3331237825755449a00c9f95c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453149"
---
# <a name="3-d-transformations-overview"></a>3B Dönüşümlere Genel Bakış
Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik sisteminde 3B modellere nasıl dönüşüm uygulanacağını açıklar. Dönüşümler, geliştiricilerin bunları tanımlayan Taban değerleri değiştirmeden modelleri yeniden konumlandırmasına, yeniden boyutlandırmasına ve yeniden erişmesine izin verir.  

## <a name="3-d-coordinate-space"></a>3-b koordinat alanı  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içindeki 3-b grafik içeriği, iki boyutlu öğe yapısına katılabileceğiniz bir öğe olan <xref:System.Windows.Controls.Viewport3D>kapsüllenir. Grafik sistemi, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]diğer birçok farklı şekilde iki boyutlu bir görsel öğe olarak Viewport3D davranır. Viewport3D, üç boyutlu bir sahneye bir pencere görünümü (Görünüm penceresi) olarak çalışır. Daha doğrusu, 3-b sahnenin yansıtılmasına neden olan bir yüzeydir.  Viewport3D 'i aynı sahne grafiğinde diğer 2-b çizim nesneleriyle birlikte kullanabilseniz de, bir Viewport3D içinde 2-b ve 3-b nesnelerini birbirine karışamaz. Aşağıdaki tartışmada, açıklanan koordinat alanı Viewport3D öğesinin içindedir.  
  
 2-b grafik için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] koordinat sistemi, işleme yüzeyinin sol üst kısmındaki kaynağı bulur (genellikle ekran). 2-b sistemde, pozitif x ekseni değerleri sağa ve pozitif y ekseni değerleri aşağı devam ediyor. Ancak, 3-b koordinat sisteminde, kaynak ekranın ortasında bulunur, pozitif x ekseni değerleri sağa devam ediyor ancak pozitif y ekseni değerleri sıfırdan devam ediyor ve pozitif z ekseni değerleri kaynaktan dışarı doğru ilerliyor Görüntüleyici.  
  
 ![Koordinat sistemleri](./media/coordsystem-1.png "CoordSystem-1")  
Koordinat sistemi karşılaştırması  
  
 Bu eksenlerde tanımlanan alan, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3-b nesneler için başvuru sabit çerçevesidir. Bu alanda modeller oluştururken ve bunları görüntülemek için ışıklar ve kameralar oluşturdığınızda, buna dönüşümler uyguladığınızda, bu sabit başvuru çerçevesini veya "Dünya alanı" ' nı her bir model için oluşturduğunuz yerel başvuru çerçevelerinden ayırt etmek yararlı olur. Ayrıca, açık ve kamera ayarlarına bağlı olarak dünya alanındaki nesnelerin tamamen farklı görünebileceğini veya hiç görünmediğine de unutmayın, ancak kameranın konumu Dünya alanındaki nesnelerin konumunu değiştirmez.  
  
## <a name="transforming-models"></a>Modelleri dönüştürme  
 Modeller oluşturduğunuzda, sahnede belirli bir konum vardır. Bu modelleri sahne içinde hareket ettirmek, döndürmek veya boyutunu değiştirmek için modelleri tanımlayan köşeleri değiştirmek pratik değildir. Bunun yerine, 2-b ' de olduğu gibi, modellere dönüşümler de uygularsınız.  
  
 Her model nesnesi, modeli taşıyabileceğiniz, yeniden yönlendirebileceğiniz veya yeniden boyutlandırabileceğiniz bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliğine sahiptir. Bir dönüşüm uyguladığınızda, dönüşüm tarafından belirtilen vektör veya değere göre modelin tüm noktalarını etkin bir şekilde fark edersiniz. Diğer bir deyişle, modelin tanımlandığı koordinat alanını ("model alanı") dönüştürürsünüz, ancak tüm sahnenin koordinat sisteminde modelin geometrisini oluşturan değerleri ("Dünya alanı") değiştirmezsiniz.  
  
## <a name="translation-transformations"></a>Çeviri dönüştürmeleri  
 3-b dönüşümler soyut temel sınıftan devralınır <xref:System.Windows.Media.Media3D.Transform3D>; Bunlar <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>ve <xref:System.Windows.Media.Media3D.RotateTransform3D>Afine dönüştürme sınıflarını içerir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-b sistem Ayrıca, daha kısa matris işlemlerinde aynı dönüştürmeleri belirtmenize imkan tanıyan bir <xref:System.Windows.Media.Media3D.MatrixTransform3D> sınıfı sağlar.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>ve <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> özellikleriyle belirttiğiniz konum vektörü yönünde Model3D içindeki tüm noktaları taşıtırın. Örneğin, (2, 2, 2) konumundaki bir küpün bir köşesi söz konusu olduğunda (0, 1.6, 1), bu köşeyi (2, 2, 2) (2, 3.6, 3) öğesine taşıyabilecek. Küpün köşesi model alanında hala (2, 2, 2), ancak model alanının (2, 2, 2) dünya alanında (2, 3.6, 3) olması için bu model alanı dünya alanı ilişkisini değiştirdi.  
  
 ![Çeviri şekli](./media/transforms-translate.png "Dönüşümler-çevir")  
Uzaklığa sahip çeviri  
  
 Aşağıdaki kod örnekleri, bir çevirinin nasıl uygulanacağını gösterir.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Ölçek dönüşümleri  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>, modelin ölçeğini, bir orta noktaya başvuru ile belirtilen bir ölçek vektörüne dönüştürür. Modelin boyutunu orantılı olarak değiştirmek için modeli X, Y ve Z eksenlerinde aynı değere göre ölçeklendirerek bir Tekdüzen ölçeği belirtin. Örneğin, dönüşümün <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> özelliklerini 0,5 olarak ayarlamak, modelin boyutunu durdurur; aynı özellikleri 2 ' ye ayarlamak üç eksende ölçeğini iki katına çıkarır.  
  
 ![Tekdüzen ScaleTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
ScaleVector örneği  
  
 Tek biçimli olmayan bir ölçek dönüştürmesi belirterek — X, Y ve Z değerleri aynı olmayan bir ölçek dönüşümü — bir modelin, diğerlerini etkilemeden bir veya iki boyutta genişlemesine veya anlaşmasına neden olabilirsiniz. Örneğin, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, 2 ' ye <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ve 1 ' e <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>, dönüştürülmüş modelin yükseklik içinde çift olmasına neden olur, ancak X ve Z eksenleri boyunca değişmeden kalır.  
  
 ScaleTransform3D, varsayılan olarak köşelerin (0, 0, 0) kaynak hakkında genişlemesine veya anlaşmasına neden olur. Dönüştürmek istediğiniz model kaynaktan çizilmemişse, modelin kaynaktan ölçeklendirilmesi, modeli "yerinde" ölçeklendirmeyecektir. Bunun yerine, modelin köşeleri ölçek vektörü ile çarpıldığı zaman, ölçek işlemi modeli çevirme ve ölçeklendirmeyi de etkiler.  
  
 ![Üç küp belirtilen orta nokta ile ölçeklendirilir](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Ölçek merkezi örneği  
  
 "Yerinde" bir modeli ölçeklendirmek için, ScaleTransform3D's <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> özelliklerini ayarlayarak modelin merkezini belirtin. Bu, grafik sisteminin model alanını ölçeklendirmesini ve sonra belirtilen <xref:System.Windows.Media.Media3D.Point3D>ortasına çevirmesini sağlar. Buna karşılık, kaynak hakkında modeli derlediyseniz ve farklı bir orta nokta belirttiğinizde, modelin kaynaktan uzağa çevrildiğini görmeniz beklenir.  
  
## <a name="rotation-transformations"></a>Döndürme dönüştürmeleri  
 3-b bir modeli birkaç farklı şekilde döndürebilirsiniz. Tipik bir döndürme dönüştürmesi bir ekseni ve bu eksen etrafında döndürme açısını belirtir. <xref:System.Windows.Media.Media3D.RotateTransform3D> sınıfı, <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği ile bir <xref:System.Windows.Media.Media3D.Rotation3D> tanımlamanızı sağlar. Daha sonra, Rotation3D üzerinde <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> ve <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> özelliklerini, bu durumda dönüştürmeyi tanımlamak için bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>belirtin. Aşağıdaki örneklerde, Y ekseni etrafında bir model 60 derece döndürülür.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Note:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-D, doğru bir döndürme sistemidir, bu da bir dönüşle ilgili pozitif bir açı değerinin, eksen hakkında saat yönünde bir dönüşle sonuçlanmasıyla sonuçlanır.  
  
 Eksen-açı döndürmeler, RotateTransform3D üzerinde <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>ve <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> özellikleri için bir değer belirtilmemişse, kaynak hakkında döndürmeyi varsayar. Ölçeklendirmeyle birlikte, döndürmenin modelin tüm koordinat alanını dönüştürdüğünü hatırlamak yararlı olur. Model, kaynak hakkında oluşturulmadıysa veya daha önce çevrilmişse, döndürme yerine, kaynak hakkında "Özet" olabilir.  
  
 ![Yeni orta nokta ile döndürme](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Yeni Merkezi belirtilen döndürme  
  
 Modeli "yerinde" döndürmek için, modelin gerçek merkezini döndürme merkezi olarak belirtin. Geometri genellikle kaynak hakkında modellendiği için, önce modeli boyutlandırarak (ölçeklendirerek) bir dönüştürme kümesinin beklenen sonucunu alabilir, sonra da bunun yönünü ayarlayabilir ve son olarak istediğiniz konuma taşıyabilirsiniz ( çevirme).  
  
 ![X&#45; ve y&#45;eksenlerinde 60 derecenin dönüşü](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Döndürme örneği  
  
 Eksen-açı döndürmeler, statik dönüşümler ve bazı animasyonlar için iyi çalışır. Ancak, X ekseninin bir küp modeli 60 derece, sonra da Z ekseni etrafında 45 derece döndürmeyi düşünün. Bu dönüştürmeyi iki ayrı afin dönüştürmesi veya matris olarak tanımlayabilirsiniz. Ancak, bu şekilde tanımlanan bir dönüşü sorunsuzca hareketlendirmek zor olabilir. Her iki yaklaşım tarafından hesaplanan modelin başlangıç ve bitiş konumları aynı olsa da, model tarafından alınan ara konumlar hesaplama açısından kesin değildir. Dördegenler, bir döndürmenin başlangıcı ve bitişi arasındaki ilişkilendirmeyi hesaplamak için alternatif bir yol temsil eder.  
  
 Dörde, 3-b alanda bir ekseni ve bu eksenin etrafında bir döndürme temsil eder. Örneğin, dörde bir (1, 1, 2) ekseni ve 50 derece dönüşü temsil edebilir. Döndürmeler 'in tanımlanmasıyla ilgili olarak, bu işlemler üzerinde gerçekleştirebileceğiniz iki işlemden geliyor: bileşim ve ilişkilendirme. Bir geometriye uygulanan iki dörde 'nın bileşimi, "rotation2 by Axis2 etrafında geometriyi döndürme, sonra rotation1 ile axis1 ile döndürme" anlamına gelir. Kompozisyonu kullanarak, sonucu temsil eden tek bir dörde elde etmek için geometrideki iki ölçütü birleştirebilirsiniz. Dörde enterpolasyon, bir eksenden ve hizalamalardan sorunsuz ve makul bir yolu hesaplayabildiğinden, orijinalden diğerine kesintisiz bir geçiş elde etmek için, dönüştürme. Hareketlendirmek istediğiniz modeller için <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği için bir <xref:System.Windows.Media.Media3D.QuaternionRotation3D> kullanarak döndürme için bir hedef <xref:System.Windows.Media.Media3D.Quaternion> belirtebilirsiniz.  
  
## <a name="using-transformation-collections"></a>Dönüşüm koleksiyonları kullanma  
 Bir sahne oluştururken bir modele birden fazla dönüşüm uygulamak yaygındır. Dönüşümleri gruplamak için <xref:System.Windows.Media.Media3D.Transform3DGroup> sınıfının <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> koleksiyonuna dönüşümler ekleyerek sahnenin çeşitli modellere kolayca uygulanmasını sağlar. Her örneğe farklı bir dönüşüm kümesi uygulayarak bir modeli yeniden kullanabilmenin pek çok farklı grupta bir dönüştürmeyi yeniden kullanmak genellikle yararlıdır. Dönüştürmelerin koleksiyona eklendiği sıra önemli olduğunu unutmayın: koleksiyondaki dönüşümler birinciden en son ' a uygulanır.  
  
## <a name="animating-transformations"></a>Dönüşümleri Hareketlendirme  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-b uygulama, 2-b grafik ile aynı zamanlama ve animasyon sistemine katılır. Diğer bir deyişle 3B sahneye animasyon uygulamak için modellerinin özelliklerine animasyon ekleyin. Temel elemanların özelliklerine doğrudan animasyon eklemek mümkündür, ancak modellerin konumunu veya görünümünü değiştiren dönüştürmelerin animasyonunu genellikle daha kolay hale gelir. Dönüşümler <xref:System.Windows.Media.Media3D.Model3DGroup> nesnelere ve tek tek modellere uygulanabileceğinden, bir animasyon kümesini bir Model3Dgroup alt öğesine ve başka bir animasyon kümesinin bir nesne grubuna uygulamak mümkündür.  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zamanlama ve animasyon sistemiyle ilgili arka plan bilgileri için bkz. [animasyon genel bakış](animation-overview.md) ve görsel taslaklara [genel bakış](storyboards-overview.md).  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]bir nesneye animasyon uygulamak için, bir zaman çizelgesi oluşturun, bir animasyon tanımlayın (zaman içinde bazı özellik değerindeki bir değişiklik) ve animasyonun uygulanacağı özelliği belirtin. Bu özellik FrameworkElement 'in bir özelliği olmalıdır. 3-b sahnedeki tüm nesneler Viewport3D alt öğesi olduğundan, sahneye uygulamak istediğiniz herhangi bir animasyonun hedeflediği Özellikler Viewport3D özelliklerinin özellikleridir. Söz dizimi ayrıntılı olabileceğinden animasyon için özellik yolunun dikkatli bir şekilde çalışması önemlidir.  
  
 Bir nesneyi yerinde döndürmek istediğinizi varsayalım, ancak daha fazla nesne görüntülemek için bir uygulama hareketi uygulamak için de bir hareket uygulayın. Modele bir RotateTransform3D uygulamayı ve döndürme eksenini bir vektörden diğerine hareketlendirmek tercih edebilirsiniz. Aşağıdaki kod örneği, RotateTransform3D 'in bir <xref:System.Windows.Media.TransformGroup>model için uygulanan birkaç dönüşümden biri olduğunu varsayarak, dönüştürmenin Rotation3D Axis özelliğine bir <xref:System.Windows.Media.Animation.Vector3DAnimation> uygulama gösterir.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Nesneyi taşımak veya ölçeklendirmek için diğer dönüştürme özelliklerini hedeflemek üzere benzer bir sözdizimi kullanın.  Örneğin, bir modelin, şeklinin düzgün deforme etmesine yol açmak için ölçek dönüşümünden ScaleCenter özelliğine bir <xref:System.Windows.Media.Animation.Point3DAnimation> uygulayabilirsiniz.  
  
 Yukarıdaki örneklerde <xref:System.Windows.Media.Media3D.GeometryModel3D>özellikleri dönüştürübilse de, sahnedeki diğer modellerin özelliklerini dönüştürmek de mümkündür.  Örneğin, ışık nesnelerine uygulanan çevirileri canlandırarak, modellerinizin görünüşünü önemli ölçüde değiştirebilmesini sağlayan hareketli ışık ve gölge etkileri oluşturabilirsiniz.  
  
 Kameralar da modeller olduğundan, kamera özelliklerini de dönüştürmek mümkündür.  Kamera konumunu veya düzlem mesafelerini dönüştürerek sahnenin görünümünü büyük ölçüde değiştirebilirsiniz; yani sahne alanının tamamını dönüştürmek için, bu şekilde elde ettiğiniz etkilerin, görüntüleyiciye "görsel anlam" olarak sunulmadığını unutmayın. farklı olarak, sahnedeki modellerin konumuna veya konumuna uygulanan dönüşümler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [2-b dönüşümler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
