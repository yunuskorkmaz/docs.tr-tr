---
title: "3B Dönüşümlere Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 431f4abd55da3b8c4e348d3abbd107e2f6344d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="3-d-transformations-overview"></a>3B Dönüşümlere Genel Bakış
Bu konu, 3-b modellerinde dönüştürmeleri uygulamak açıklar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik sistemi. Dönüşümleri geliştiricinin yeniden konumlandırmak, yeniden boyutlandırma ve bunları tanımlayan temel değerleri değiştirmeden modelleri yeniden yönlendirmesine izin verin.  
  

  
## <a name="3-d-coordinate-space"></a>3-b koordinat  
 3B grafik içeriği [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bir öğedeki kapsüllenmiş <xref:System.Windows.Controls.Viewport3D>, iki boyutlu öğe yapısında katılmak. Grafik sistemi diğer birçok gibi iki boyutlu bir görsel öğe olarak Viewport3D değerlendirir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D işlevleri bir pencere olarak — bir görünüm penceresinin — üç boyutlu Sahne içine. Daha doğru bir şekilde 3B Sahne yansıtıldığı yüzey değil.  Aynı Sahne grafiği diğer 2-D çizim nesneleri ile Viewport3D kullanabilseniz de, Viewport3D içindeki 2 ve 3 boyutlu nesnelerinin işleyemezsiniz. Aşağıdaki tartışmada Viewport3D öğesi tarafından tanımlanan koordinat yer alır.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Koordinat sistemi 2B grafik için sol üst işleme yüzeyinin (genellikle ekran) kaynak bulur. 2-D sistemindeki pozitif x ekseni değerleri sağa doğru devam eder ve pozitif y ekseni değerleri aşağı doğru devam eder. 3-b koordinat sistemi, ancak, başlangıç ekranı Merkezi'nde pozitif x ekseni değerleri sağa ancak bunun yerine yukarı doğru devam ederek pozitif y ekseni değerleri ve dışa kaynaktan doğru pozitif z ekseni değerleri ile bulunur Görüntüleyici.  
  
 ![Koordinat sistemleri](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Koordinat sistemi karşılaştırma  
  
 Bu eksenler tarafından tanımlanan başvuru çerçevesidir 3-b nesneler için alandır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Bu alanda modelleri oluşturabilir ve ışık oluşturup bunları görüntülemek için kameralar gibi bu başvuru çerçevesidir ya da "world alanı," yerel dönüşümleri uyguladığınızda, her model için oluşturduğunuz başvuru çerçevesini ayırmak yararlıdır. Ayrıca, dünya uzayındaki nesnelerin tamamen farklı arayın veya hiç görünmez, açık ve Kamera bağlı olarak ayarlar, ancak kamera konumunu değiştirmez dünya uzayındaki nesnelerin konumunu olduğunu unutmayın.  
  
## <a name="transforming-models"></a>Dönüşüm modelleri  
 Modelleri oluşturduğunuzda Sahne belirli bir konumda sahiptirler. Sahne döndürmek ya da kendi boyutunu değiştirmek için bu modelleri hareket etmek için bu modelleri tanımlayan köşeleri değiştirmek mümkün değil. Bunun yerine, yalnızca 2-D olduğu gibi dönüşümleri modellere uygulayın.  
  
 Her model nesnesi olan bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> ile taşıyabilir, yeniden yönlendirmek veya model yeniden boyutlandırma özelliği. Dönüşüm uyguladığınızda, etkili bir şekilde modelinin tüm noktalarını dönüşüm tarafından belirtilen tüm vektör veya değer tarafından uzaklık. Diğer bir deyişle, koordinat alanında dönüştürdükten model olan ("model uzayı") tanımlı, ancak tüm Sahne ("world alanı") koordinat sistemi içinde modelin geometri oluşturan değerleri değiştirmezsiniz.  
  
## <a name="translation-transformations"></a>Çeviri Dönüşümleri  
 3B dönüşümler soyut taban sınıfından devralan <xref:System.Windows.Media.Media3D.Transform3D>; bunlar afin dönüşüm sınıflarını içerir <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, ve <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-b sistemi de sağlayan bir <xref:System.Windows.Media.Media3D.MatrixTransform3D> olanak sağlayan sınıf daha kısa matris işlemlerinde aynı dönüşümleri belirtin.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>Model3D ile belirttiğiniz uzaklık vektör yönünü içinde olan tüm noktaları taşır <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, ve <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> özellikleri. Örneğin, bir küp bir köşesinin (2,2,2) göz önüne alındığında, (0,1.6,1) bir uzaklık vektörü bu (2,2,2) köşesini (2,3.6,3) taşıyabilir. Küpün köşe hala (2,2,2) içinde model alanı olmakla birlikte, böylece (2,2,2) içinde model alanı (köşesini 2,3.6,3) artık bu modeli alanı world alanı ilişkisini world alanı değiştirilmiştir.  
  
 ![Çeviri şekil](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "dönüşümler Çevir")  
Uzaklık ile  
  
 Aşağıdaki kod örnekleri, bir çeviri uygulamak gösterilmektedir.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Ölçeklendirme dönüşümleri  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>Merkez nokta başvuru içeren bir belirtilen ölçek vektörü tarafından modelin ölçeğini değiştirir. Modelin boyutunu orantılı olarak değiştirmek için X, Y ve Z eksenleri, aynı değeri model ölçeklendirir Tekdüzen bir ölçek belirtin. Örneğin, dönüşümün ayarlama <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 0,5 özelliklerine halves model boyutunu; 2'ye aynı özelliklerini ayarlama, tüm üç eksen kendi ölçek iki katına çıkar.  
  
 ![Tekdüzen ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
ScaleVector Örneği  
  
 Bir Tekdüzen olmayan ölçeklendirme dönüşümü belirterek — X, Y ve Z değerleri tümü aynı olmayan bir ölçeklendirme dönüşümü — uzatmak veya diğer etkilemeden bir veya iki boyutlarında sözleşme bir model neden olabilir. Örneğin, ayarlama <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 2 ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 1 yüksekliği çift ancak X ve Z eksenleri değişmeden dönüştürülmüş modelin neden olur.  
  
 Varsayılan olarak, ScaleTransform3D Genişlet veya daralt kaynak (0,0,0) neden olur. Dönüştürmek istediğiniz modeli kaynaktan çizilmiş değil, ancak kaynak modelden ölçeklendirme modeli "yerinde." ölçekleme sağlamaz Bunun yerine, modelin köşeleri ölçek vektörü ile çarpıldığı zaman ölçeklendirme işlemi, model çevirme yanı ölçeklendirme etkisi olmaz.  
  
 ![Üç küpleri orta noktası belirtilen ölçeklendirilmiş](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Ölçek Merkezi örnek  
  
 Bir modeli "yerinde" ölçeklendirmek için ScaleTransform3D ayarlayarak modelin merkezine belirtin <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> özellikleri. Bu grafik sistem modeli alanı ölçeklendirir ve onu belirtilen Orta çevirir sağlar <xref:System.Windows.Media.Media3D.Point3D>. Kaynak modeli oluşturduğunuza ve farklı bir orta nokta belirtirseniz, buna karşılık, kaynağını çıktığınızda çevrilen modeli bekliyoruz.  
  
## <a name="rotation-transformations"></a>Döndürme Dönüşümleri  
 3-b modelde birkaç farklı şekilde döndürebilirsiniz. Tipik döndürme dönüşümü eksende ve o ekseni etrafında döndürme açısı belirtir. <xref:System.Windows.Media.Media3D.RotateTransform3D> Sınıfı tanımlamanıza olanak sağlayan bir <xref:System.Windows.Media.Media3D.Rotation3D> ile kendi <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği. Ardından belirttiğiniz <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> ve <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> özellikler bu durumda Rotation3D üzerinde bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, dönüşüm tanımlamak için. Aşağıdaki örnekler bir modeli Y ekseni etrafında 60 derece döndürün.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Not:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-b olan bir dönüş için bir pozitif açı değer ekseni etrafında yönünün saat yönünde bir döndürme sonuçlanır anlamına gelir bir sağ sistemi.  
  
 Eksen-açı döndürmeleri varsayın etrafında döndürme için bir değer belirtilmezse <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, ve <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> RotateTransform3D özellikleri. Ölçeklendirme gibi döndürme modelinin tüm koordinat dönüştüren anımsaması yararlıdır. Modeli kaynak oluşturulmadı veya önceden taşınmışsa, döndürme "yerinde döndürme yerine kaynak hakkında Özet".  
  
 ![Yeni Merkezi noktasıyla döndürme](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Belirtilen yeni Merkezi ile döndürme  
  
 Modeli "yerinde" döndürmek için modelin fiili orta döndürme merkezi olarak belirtin. Geometri genellikle kaynak modellenir olduğundan, en sık dönüşümleri kümesi beklenen sonucu (ölçeklendirme) modeli, ilk boyutlandırma sonra yönünü (döndürme) ayarlayarak ve taşımak için istenen konumu (son alabilirsiniz Bu çevirme).  
  
 ![X 60 derece &#45;döndürme; y &#45; ve eksenleri](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Döndürme örneği  
  
 Eksen-açı döndürmeleri statik dönüşümler ve bazı animasyonları için iyi çalışır. Ancak, bir küp modelini 60 derece sonra 45 dereceyi Z ekseni etrafında X ekseni etrafında döndürme göz önünde bulundurun. Bu dönüşüm iki ayrı afin dönüşümler veya bir matris olarak tanımlayabilirsiniz. Ancak, bu şekilde tanımlanan bir döndürmeyi sorunsuz hale getirmeyi zor olabilir. Başlangıç ve bitiş her iki yaklaşım tarafından hesaplanmış modeli konumlarını aynı olsa da, model tarafından gerçekleştirilen ara konumlar kesin değildir. Dördey başlangıç ve bitiş bir döndürme arasında ilişkilendirme hesaplamak için alternatif bir yol gösterir.  
  
 Bir dördey eksende 3B ve o ekseni etrafında döndürme temsil eder. Örneğin, bir dördey (1,1,2) ekseni ve 50 derece dönüşünü temsil edebilir. Bunlar üzerinde gerçekleştirebileceğiniz iki işlem döndürme tanımlamadaki güç gelir: oluşturma ve ilişkilendirme. Bir geometriye uygulanan iki dördey oluşumunu "tarafından rotation2 geometri axis2 etrafında döndürün ve ardından tarafından rotation1 ile axis1 etrafında döndürün." anlamına gelir. Birleşim kullanarak iki döndürmeleri sonucunu temsil eder tek bir dördey almak için geometri üzerinde birleştirebilirsiniz. Dördey ilişkilendirme bir kesintisiz ve makul bir yol bir eksen ve yönüne öğesinden diğerine hesaplayabilirsiniz olduğundan, özgün hesaplayabildiği birinden diğerine, sorunsuz bir geçiş gerçekleştirmek için için animasyon olanak kesinti Dönüşüm. Animasyon eklemek istediğiniz modelleri için bir hedef belirtin <xref:System.Windows.Media.Media3D.Quaternion> kullanarak döndürme için bir <xref:System.Windows.Media.Media3D.QuaternionRotation3D> için <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği.  
  
## <a name="using-transformation-collections"></a>Dönüşüm koleksiyonları kullanma  
 Bir görünüm oluştururken bir modele birden fazla dönüşüm uygulamak yaygındır. Dönüşümler ekleyin <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> koleksiyonu <xref:System.Windows.Media.Media3D.Transform3DGroup> gruplandırmak için sınıf dönüştüren rahat çeşitli modellere uygulamak için. Genellikle, bir dönüşüm kadar her bir örneğine farklı dönüşümler kümesi uygulayarak bir modeli yeniden kullanabilirsiniz şekilde birkaç farklı gruplar halinde yeniden kullanmak uygundur. Dönüşümleri koleksiyona eklenir sipariş önemli olduğunu unutmayın: koleksiyondaki dönüşümler uygulanır birinciden için son.  
  
## <a name="animating-transformations"></a>Dönüşümleri animasyon ekleme  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-b uygulaması katılan 2B grafik olarak aynı zamanlama ve animasyon sistemi. Diğer bir deyişle, 3B Sahne animasyon için kendi modellerinin özelliklerini animasyon. Elemanlar özelliklerine doğrudan animasyon mümkündür, ancak konum veya modelleri görünümünü değiştirme dönüşümleri animasyon genellikle daha kolay. Dönüşümleri uygulanabilir çünkü <xref:System.Windows.Media.Media3D.Model3DGroup> nesneleri tek tek modellerin yanı sıra tek bir Model3Dgroup alt kümesini ve diğer nesnelerin bir grubuna uygulamak mümkündür.  Arka plan bilgileri için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zamanlama ve animasyon sistemi bkz [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Bir nesnenin animasyon için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], bir zaman çizelgesi oluşturun, (gerçekten bazı özellik değerinde bir değişiklik zaman içinde) bir animasyon tanımlayın ve animasyonun uygulanacağı özelliği belirtin. Bu özellik FrameworkElement özelliği olmalıdır. 3B Sahne içinde tüm nesneler Viewport3D alt olduğundan Sahne uygulamak istediğiniz animasyon tarafından hedeflenen özellikler Viewport3D özelliklerinin özellikleridir. Sözdizimi ayrıntılı olabileceğinden animasyonun özellik yolunda dikkatlice çalışmak önemlidir.  
  
 Bir nesneyi yerinde döndürmek için aynı zamanda daha fazla bilgi görüntülemek için nesnesinin kullanıma sunmak için swinging hareketinin uygulamak istediğinizi varsayalım. Modele bir RotateTransform3D uygulamak ve bir vektör döndürme başka bir eksen hale getirmeyi tercih edebilirsiniz. Aşağıdaki kod örneğinde, uygulama gösterilmektedir bir <xref:System.Windows.Media.Animation.Vector3DAnimation> dönüşümün Rotation3D eksen özelliğine sahip olan model uygulanan birkaç Dönüşümlerin biri için RotateTransform3D varsayarak bir <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Benzer bir sözdizimi taşımak veya nesneyi ölçeklemek için diğer dönüşüm özelliklerini hedeflemek için kullanın.  Örneğin, geçerli olabilecek bir <xref:System.Windows.Media.Animation.Point3DAnimation> ölçeklendirme dönüşümü bir modelin düzgün şekilde neden ScaleCenter özelliğine.  
  
 Önceki örneklerde özelliklerini dönüştürme rağmen <xref:System.Windows.Media.Media3D.GeometryModel3D>, diğer modellere özelliklerini dönüştürmek mümkündür.  Işık nesnelerine uygulanan çevirileri animasyon tarafından Örneğin, taşıma açık ve önemli ölçüde Modellerinizi görünümünü değiştirebilirsiniz gölge efektleri oluşturabilirsiniz.  
  
 Kameralar da modeller olduğundan, kamera özelliklerini dönüştürmek mümkündür.  Kamera konumu veya düzlem uzaklıklarını dönüştürerek kesinlikle Sahne görünümünü değiştirebilirsiniz ancak — yürürlükte, tüm Sahne projeksiyon dönüştürme — çoğu bu şekilde elde etkileri kadar "visual" Görüntüleyicisi anlamı olmayabilir olduğunu unutmayın Konum veya Sahne modellerin konumda uygulanan dönüşümleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Dönüşümler genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252)
