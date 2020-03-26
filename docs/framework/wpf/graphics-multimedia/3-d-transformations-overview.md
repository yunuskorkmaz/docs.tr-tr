---
title: 3D Dönüşümlere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D transformations
- transformations [WPF], 3D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 0efd6d247f23760c878c82cc92e99f1b83c1b9d2
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112355"
---
# <a name="3d-transformations-overview"></a>3D Dönüşümlere Genel Bakış
Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik sistemindeki 3B modellere dönüşümlerin nasıl uygulanacağı açıklanmaktadır. Dönüşümler, geliştiricinin modelleri tanımlayan temel değerleri değiştirmeden yeniden konumlandırmasına, yeniden boyutlandırmasına ve yeniden yönlendirmesine olanak sağlar.  

## <a name="3d-coordinate-space"></a>3B Koordinat Alanı  
 3D grafik [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içeriği, iki boyutlu öğe <xref:System.Windows.Controls.Viewport3D>yapısına katılabilen bir öğeiçinde kapsüllenir. Grafik sistemi Viewport3D'yi diğer birçok 'daki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]gibi iki boyutlu görsel bir öğe olarak ele almaktadır. Viewport3D, üç boyutlu bir sahneye açılan bir pencere-görüntüleme portu olarak işlev görür. Daha doğrusu, bir 3B sahnenin yansıtıldığı bir yüzeydir.  Viewport3D'yi aynı sahne grafiğindeki diğer 2B çizim nesneleriyle birlikte kullanabiliyor olsanız da, Viewport3D içindeki 2B ve 3B nesnelere giremezsiniz. Aşağıdaki tartışmada, açıklanan koordinat alanı Viewport3D öğesi tarafından bulunur.  
  
 2B grafikleriçin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] koordinat sistemi, görüntü yüzeyinin sol üst kısmındaki kaynağı (genellikle ekran) bulur. 2B sistemde pozitif x ekseni değerleri sağa, pozitif y ekseni değerleri aşağı doğru ilerler. Ancak 3B koordinat sisteminde, menşe ekranın merkezinde yer alır, pozitif x ekseni değerleri sağa doğru ilerler ancak pozitif y ekseni değerleri yukarı doğru ilerler ve pozitif z ekseni değerleri kaynaktan dışa doğru izleyiciye.  
  
 ![Koordinat sistemleri](./media/coordsystem-1.png "CoordSystem-1")  
Koordinat Sistemi Karşılaştırması  
  
 Bu eksenler tarafından tanımlanan alan, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3B nesneler için ''de bulunan sabit başvuru çerçevesidir. Bu alanda modeller oluştururken ve bunları görüntülemek için ışıklar ve kameralar oluştururken, dönüşümleri uyguladığınızda her model için oluşturduğunuz yerel referans çerçevesinden bu sabit referans çerçevesini veya "dünya alanı"nı ayırt etmek yararlıdır. Ayrıca, dünya uzayında nesnelerin ışık ve kamera ayarlarına bağlı olarak tamamen farklı görünebileceğini veya hiç görünmeyebileceğini, ancak kameranın konumunun nesnelerin dünya uzasındaki konumunu değiştirmediğini unutmayın.  
  
## <a name="transforming-models"></a>Modelleri Dönüştürme  
 Modelleri oluşturduğunuzda, sahnede belirli bir konuma sahiptirler. Bu modelleri sahnede hareket ettirebilmek, döndürmek veya boyutlarını değiştirmek için modelleri tanımlayan tepe bilgilerini değiştirmek pratik değildir. Bunun yerine, tıpkı 2B'de olduğu gibi, dönüşümleri modellere uygularsınız.  
  
 Her model nesnesinin, modeli taşıyabileceğiniz, yeniden yönlendirebileceğiniz veya yeniden boyutlandırabileceğiniz bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği vardır. Bir dönüştürme uyguladığınız zaman, dönüşümün belirlediği vektör veya değere göre modelin tüm noktalarını etkili bir şekilde dengelersiniz. Başka bir deyişle, modelin tanımlandığı koordinat alanını ("model uzayı") dönüştürdüniz, ancak modelin geometrisini oluşturan değerleri tüm sahnenin koordinat sisteminde ("dünya uzayı") değiştirmedin.  
  
## <a name="translation-transformations"></a>Çeviri Dönüşümleri  
 3B dönüşümler soyut taban <xref:System.Windows.Media.Media3D.Transform3D>sınıfından miras; bu affine transform <xref:System.Windows.Media.Media3D.TranslateTransform3D>sınıfları içerir , <xref:System.Windows.Media.Media3D.ScaleTransform3D>ve <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3B sistem ayrıca, <xref:System.Windows.Media.Media3D.MatrixTransform3D> daha kısa matris işlemlerinde aynı dönüşümleri belirtmenizi sağlayan bir sınıf da sağlar.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>, ve <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A> <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> özellikleri ile belirttiğiniz ofset vektörü yönünde Model3D'deki tüm noktaları hareket ettirir. Örneğin, (2,2,2) bir küp ünbir vertex verilen, bir ofset vektör (0,1,6,1) bu vertex (2,2,2) için (2,3,6,3) hareket eder. Küpün tepe noktası hala (2,2,2) model uzayda, ama şimdi model alanı dünya uzayı ile ilişkisini değiştirdi, böylece (2,2,2) model uzayda (2,3.6,3) dünya uzayında.  
  
 ![Çeviri rakamı](./media/transforms-translate.png "Dönüşümler-Çeviri")  
Ofset ile Çeviri  
  
 Aşağıdaki kod örnekleri, bir çevirinin nasıl uygulanacağı gösterilmektedir.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Ölçek Dönüşümleri  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>bir merkez noktasına atıfta bulunarak modelin ölçeğini belirli bir ölçek vektörü yle değiştirir. Modelin boyutunu orantılı olarak değiştirmek için modeli X, Y ve Z eksenlerinde aynı değerle ölçeklendiren tek düze bir ölçek belirtin. Örneğin, dönüşümün <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> özelliklerinin 0,5'e ayarlanması modelin boyutunu yarıya indirir; aynı özellikleri 2'ye ayarlamak, her üç eksende de ölçeğini ikiye katlar.  
  
 ![Tek tip scaleTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
ScaleVector Örneği  
  
 X, Y ve Z değerlerinin tümü aynı olmayan bir ölçek dönüşümü olan tek düze olmayan bir ölçek dönüşümü belirterek, bir modelin diğerlerini etkilemeden bir veya iki boyutta esnemesine veya daraltlanmasına neden olabilirsiniz. Örneğin, 1, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 2 ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 1'e ayar yapmak, dönüştürülmüş modelin yüksekliğinin iki katına gelmesine, ancak X ve Z eksenleri boyunca değişmeden kalmasına neden olur.  
  
 Varsayılan olarak, ScaleTransform3D vertices genişletmek veya kökeni (0,0,0) hakkında sözleşme neden olur. Dönüştürmek istediğiniz model kaynaktan çizilmezse, ancak modelin kaynağından ölçeklendirme modeli "yerinde" ölçeklendirmez. Bunun yerine, modelin vertices ölçek vektörü ile çarpıldığında, ölçekişlemi modeli çevirme nin yanı sıra ölçekleme etkisine sahip olacaktır.  
  
 ![Merkez noktası belirtilen ölçeklendirilir üç küp](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Ölçek Merkezi Örneği  
  
 Bir modeli "yerinde" ölçeklendirmek için, ScaleTransform3D'lerin <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> özellikleri ayarlayarak modelin merkezini belirtin. Bu, grafik sisteminin model alanını ölçeklendirmesini ve daha sonra belirtilen <xref:System.Windows.Media.Media3D.Point3D>merkeze çevirmesini sağlar. Tersine, modelin kökeni hakkında bir model oluşturup farklı bir merkez noktası belirttiyseniz, modelin kaynaktan uzağa çevrildiğini görmeyi bekleyin.  
  
## <a name="rotation-transformations"></a>Rotasyon Dönüşümleri  
 Bir modeli birkaç farklı şekilde 3B olarak döndürebilirsiniz. Tipik bir döndürme dönüşümü, bir eksen ve bu eksen etrafında bir dönüş açısı belirtir. Sınıf, <xref:System.Windows.Media.Media3D.RotateTransform3D> <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği olan <xref:System.Windows.Media.Media3D.Rotation3D> bir'i tanımlamanızı sağlar. Daha sonra, <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> dönüşümü tanımlamak için, bu durumda <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>Bir , Döndürme 3D özellikleri belirtin. <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> Aşağıdaki örnekler bir modeli Y ekseni etrafında 60 derece döndürür.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Not:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D sağ elini kullanan bir sistemdir, bu da bir dönüş için pozitif açı değerinin eksen hakkında saat yönünün tersine dönmesiyle sonuçlandığı anlamına gelir.  
  
 Eksen açısı <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>döndürmeleri, RotateTransform3D'deki , ve <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A> <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> özellikler için bir değer belirtilmemişse, menşei hakkında döndürme yi varsayar. Ölçeklemede olduğu gibi, döndürmenin modelin tüm koordinat alanını dönüştürdüğünü hatırlamak yararlıdır. Model kökeni hakkında oluşturulmamadıysa veya daha önce çevrilmişse, döndürme yerinde döndürmek yerine kaynak hakkında "pivot" olabilir.  
  
 ![Yeni merkez noktası ile döndürme](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Belirtilen yeni merkezle döndürme  
  
 Modeli "yerinde" döndürmek için, döndürme merkezi olarak modelin gerçek merkezini belirtin. Geometri genellikle başlangıç hakkında modellenmiştir, genellikle önce modeli boyutlandırarak (ölçeklendirerek), sonra yönünü ayarlayarak (döndürerek) ve son olarak istenilen konuma taşıyarak bir dizi dönüşümün beklenen sonucunu elde edebilirsiniz ( çevirerek).  
  
 ![X&#45; ve y&#45;eksenlerinde 60 derece dönüş](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Döndürme Örneği  
  
 Eksen açısı döndürmeleri statik dönüşümler ve bazı animasyonlar için iyi çalışır. Ancak, bir küp modelini X ekseni etrafında 60 derece, ardından Z ekseni etrafında 45 derece döndürmeyi düşünün. Bu dönüşümü iki ayrı bağdönüşüm veya matris olarak tanımlayabilirsiniz. Ancak, bu şekilde tanımlanan bir döndürmeyi sorunsuz bir şekilde canlandırmak zor olabilir. Her iki yaklaşımla da hesaplanan modelin başlangıç ve bitiş konumları aynı olsa da, model tarafından alınan ara konumlar hesaplama açısından belirsizdir. Quaternions bir rotasyon un başlangıcı ve sonu arasındaki enterpolasyonu hesaplamak için alternatif bir yol temsil eder.  
  
 Bir kuation 3B boşlukta bir ekseni ve bu eksen etrafında bir dönüşü temsil eder. Örneğin, bir kuatnion (1,1,2) ekseni ve 50 derecelik bir dönüşü temsil edebilir. Kuverslerin döndürmeleri tanımlamadaki gücü, üzerlerinde gerçekleştirebileceğiniz iki işlemden gelir: kompozisyon ve enterpolasyon. Bir geometriye uygulanan iki kuatronun bileşimi "geometriyi eksen2 etrafında döndürme2' yi döndürme, sonra da 1. Kompozisyonu kullanarak, sonucu temsil eden tek bir quaternion almak için geometri üzerindeki iki döndürmeyi birleştirebilirsiniz. Kuternion enterpolasyonu bir eksenden diğerine düzgün ve makul bir yol hesaplayabildiği için, birinden diğerine yumuşak bir geçiş elde etmek için orijinalden oluşan quaternion'a enterpolasyon yapabilirsiniz. Dönüştürme. Animasyon yapmak istediğiniz modeller için, <xref:System.Windows.Media.Media3D.Quaternion> <xref:System.Windows.Media.Media3D.QuaternionRotation3D> <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özellik için bir kullanarak döndürme için bir hedef belirtebilirsiniz.  
  
## <a name="using-transformation-collections"></a>Dönüşüm Koleksiyonlarını Kullanma  
 Bir sahne inşa ederken, bir modele birden fazla dönüşüm uygulamak yaygındır. Sahnedeki <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> <xref:System.Windows.Media.Media3D.Transform3DGroup> çeşitli modellere uygulamak için uygun dönüşümleri gruplandırmak için sınıfın koleksiyonuna dönüşümler ekleyin. Bir dönüşümü, her örne farklı bir dönüşüm kümesi uygulayarak bir modeli yeniden kullanabileceğiniz şekilde, birkaç farklı grupta yeniden kullanmak genellikle uygundur. Dönüşümlerin koleksiyona eklenme sırasının önemli olduğunu unutmayın: koleksiyondaki dönüşümler birinciden sona doğru uygulanır.  
  
## <a name="animating-transformations"></a>Dönüşümleri Animating  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D uygulama 2D grafik olarak aynı zamanlama ve animasyon sistemi katılır. Başka bir deyişle, bir 3B sahneyi canlandırmak için, modellerinin özelliklerini animasyona. İlkel lerin özelliklerini doğrudan canlandırmak mümkündür, ancak modellerin konumunu veya görünümünü değiştiren dönüşümleri canlandırmak genellikle daha kolaydır. Dönüşümler nesnelerin yanı <xref:System.Windows.Media.Media3D.Model3DGroup> sıra tek tek modellere de uygulanabildiği için, bir Model3Dgroup'un çocuklarına bir animasyon kümesi ve bir nesne grubuna başka bir animasyon kümesi uygulamak mümkündür.  Zamanlama ve animasyon sistemi hakkında arka plan bilgileri için [Animasyona Genel Bakış](animation-overview.md) ve [Storyboards Genel Bakış'a](storyboards-overview.md)bakın. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]  
  
 Bir nesneyi canlandırmak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]için, zaman çizelgesi oluşturmak, bir animasyon tanımlayın (zaman içinde bazı özellik değerinde gerçekten bir değişikliktir) ve animasyonun uygulanacağı özelliği belirtin. Bu özellik bir FrameworkElement'in malıdır. 3B sahnedeki tüm nesneler Viewport3D'nin çocukları olduğundan, sahneye uygulamak istediğiniz animasyonun hedeflediği özellikler Viewport3D özellikleridir. Sözdizimi ayrıntılı olabileceğinden, animasyonun özellik yolunu dikkatle çalışmak önemlidir.  
  
 Bir nesneyi yerinde döndürmek istediğinizi, ancak görüntülenene daha fazla nesneyi ortaya çıkarmak için sallanan bir hareket uygulamak istediğinizi varsayalım. Modele bir RotateTransform3D uygulamayı ve döndürme eksenini bir vektörden diğerine animasyona dönüştürmeyi seçebilirsiniz. Aşağıdaki kod örneği, transformasyonun Rotation3D'sinin Eksen özelliğine bir <xref:System.Windows.Media.Animation.Vector3DAnimation> uygulama nın, RotateTransform3D'nin modele uygulanan <xref:System.Windows.Media.TransformGroup>birkaç dönüşümden biri olduğunu varsayarak bir .  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Nesneyi taşımak veya ölçeklendirmek için diğer dönüştürme özelliklerini hedeflemek için benzer bir sözdizimini kullanın.  Örneğin, bir modelin <xref:System.Windows.Media.Animation.Point3DAnimation> şeklini düzgün bir şekilde bozacak şekilde bir ölçek dönüşümünde ScaleCenter özelliğine bir uygulama nız olabilir.  
  
 Önceki örnekler özelliklerini dönüştürse <xref:System.Windows.Media.Media3D.GeometryModel3D>de, sahnedeki diğer modellerin özelliklerini de dönüştürmek mümkündür.  Örneğin, Işık nesnelerine uygulanan çevirileri canlandırarak, modellerinizin görünümünü önemli ölçüde değiştirebilecek hareketli ışık ve gölge efektleri oluşturabilirsiniz.  
  
 Kameralar da model olduğundan, kamera özelliklerini de dönüştürmek mümkündür.  Kamera konumunu veya düzlem mesafelerini dönüştürerek sahnenin görünümünü kesinlikle değiştirebilirsiniz-aslında, tüm sahne projeksiyonunu dönüştürerek—bu şekilde elde ettiğiniz etkilerin çoğunun izleyiciye bu kadar "görsel anlamda" anlam ifade etmeyebilir. dönüşümler sahnedeki modellerin konumuna veya konumuna uygulanırken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [2B Örnek Dönüştürür](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
