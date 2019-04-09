---
title: 3B Grafiklere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 79dc7a3578c395ae8cdf5933e1249441f97071a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087995"
---
# <a name="3-d-graphics-overview"></a>3B Grafiklere Genel Bakış
<a name="introduction"></a> [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] İşlevselliği [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çizme, dönüştürme ve biçimlendirme hem işlemsel koddaki 3B grafikler animasyon geliştiricilerin sağlar. Geliştiriciler birleştirebilirsiniz [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] ve [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] zengin denetimler oluşturmak, karmaşık veri çizimleri sağlayın veya kullanıcı geliştirmek için grafik deneyimi bir uygulamanın arabirimi. [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] desteği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tam özellikli bir oyun geliştirme platformu sağlamak üzere tasarlanmamıştır. Bu konu, genel bir bakış sağlar. [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] işlevselliği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik sistemi.  

<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>Bir 2B kapsayıcı 3-b  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafik içeriği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir öğedeki kapsüllenir <xref:System.Windows.Controls.Viewport3D>, iki boyutlu öğesi yapısında katılmak. Grafik sistemi işler <xref:System.Windows.Controls.Viewport3D> diğer birçok gibi iki boyutlu bir görsel öğe olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D> bir pencere olarak çalışır; bir Görünüm penceresi — üç boyutlu bir Sahne olarak. Bir yüzeyinde daha doğru bir şekilde olduğu bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne öngörülen.  
  
 Geleneksel olarak [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] uygulama, kullanım <xref:System.Windows.Controls.Viewport3D> kılavuz veya tuval gibi başka bir kapsayıcı öğe gibi.  Hizmetini kullanıyor olsanız da <xref:System.Windows.Controls.Viewport3D> diğer [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aynı Sahne grafiğin çizim nesneleri, size işleyemezsiniz [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] ve [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içindeki nesneleri bir <xref:System.Windows.Controls.Viewport3D>.  Bu konu nasıl çizileceğini odaklanacaktır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafik içinde <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3B koordinat  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Koordinat sistemi için [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafik işleme alan (genellikle ekranın) sol üst köşesindeki içinde kaynak bulur. İçinde [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sistem x eksenindeki değerler devam sağa ve aşağı doğru pozitif y değerleri devam pozitif.  İçinde [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sağa pozitif x eksenindeki değerler ancak bunun yerine yukarı doğru devam ederek pozitif y ekseni değerler ve dışa doğru pozitif z değerleri ile koordinat sistemi, ancak kaynak işleme alan ortasında bulunur merkezinden Görüntüleyicisi doğru.  
  
 ![Koordinat sistemleri](./media/coordsystem-1.png "CoordSystem-1")  
Geleneksel 2B ve 3B koordinat sistemini gösterimleri  
  
 Bu eksen tarafından tanımlanan başvuru çerçevesidir için alandır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesneler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu alandaki modelleri oluşturabilir ve ışıklar oluşturup bunları görüntülemek için kameralar gibi bu başvuru çerçevesidir ya da "dünya alanındaki," yerel dönüşümleri uyguladığınızda, oluşturduğunuz her model için referans çerçevesi ayırmak yararlıdır. Ayrıca, dünya alanındaki nesneleri tamamen farklı arayın veya hiç görünür olmaması, bağlı olarak, açık ve kamera ayarları, ancak kameranın konumu değiştirmez, dünya alanındaki nesnelerin konumunu unutmayın.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Kamaralar ve tahminler  
 Geliştiriciler, iş [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] çizim temelleri iki boyutlu bir ekranda konumlandırma alışkındır. Oluştururken bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sahnenin önemlidir, gerçekten oluşturma hatırlamak bir [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] gösterimini [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesneleri. Çünkü bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sahne izleyicisinin açısından bağlı olarak farklı görünüyor, o açısından belirtmeniz gerekir. <xref:System.Windows.Media.Media3D.Camera> Sınıfı için bu bakış açısı belirtmenizi sağlar bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne.  
  
 Başka bir şekilde anlamak için nasıl bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne temsil bir [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] yüzeydir görüntüleme yüzeyine bir projeksiyon olarak Sahne açıklayarak. <xref:System.Windows.Media.Media3D.ProjectionCamera> Farklı projeksiyonlar ve izleyicisinin nasıl göreceğini değiştirmek için kendi özelliklerini belirtmenize olanak tanır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelleri. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> Sahne foreshortens bir projeksiyon belirtir.  Diğer bir deyişle, <xref:System.Windows.Media.Media3D.PerspectiveCamera> kaybolmasını noktası perspektif sağlar.  Sahne, idare ve görünüm alanı kamera ve sahnede "yukarı" yönü tanımlayan vektör öğesinin koordinat kameranın konumu belirtebilirsiniz. Aşağıdaki diyagramda gösterilmektedir <xref:System.Windows.Media.Media3D.PerspectiveCamera>'s projeksiyon.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Ve <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> özelliklerini <xref:System.Windows.Media.Media3D.ProjectionCamera> kameranın projeksiyon aralığını sınırlayan. Kamera sahnenin herhangi bir yerde bulunan olabileceğinden, aslında bir model içinde veya nesnelerin düzgün bir şekilde ayırt etmek zor hale çok bir model yakın konumlandırılan kamera için mümkündür.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> dışında olmayan nesneler çizileceğini kameradan en düşük bir uzaklık belirtmenizi sağlar.  Buna karşılık, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> tanınabilir olmasını çok uzakta nesneleri Sahne içinde eklenmeyecek sağlar nesneleri değil çizilen, kamera mesafe belirtmenize olanak tanır.  
  
 ![Kamera Kurulum](./media/coordsystem-6.png "CoordSystem-6")  
Kamera konumu  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> bir orthogonal izdüşümü belirtir bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] model için bir [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] visual yüzeyi. Diğer kameralar gibi yönünü ve "yukarı" yönü görüntüleme, bir konumu belirtir. Farklı <xref:System.Windows.Media.Media3D.PerspectiveCamera>, ancak <xref:System.Windows.Media.Media3D.OrthographicCamera> perspektif foreshortening içermeyen bir projeksiyon açıklar. Diğer bir deyişle, <xref:System.Windows.Media.Media3D.OrthographicCamera> kenarlarının kenarlarının uyan bir noktada bir kamera olarak yerine paralel bir görüntüleme kutusunun açıklar. Aşağıdaki görüntüde kullanarak göründüğü haliyle aynı modelin gösterilmektedir <xref:System.Windows.Media.Media3D.PerspectiveCamera> ve <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Ortografik ve perspektif projeksiyon](./media/camera-projections4.png "Camera_projections4")  
Perspektif ve Ortografik projeksiyonlar  
  
 Aşağıdaki kod, bazı tipik kamera ayarları gösterir.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Model ve kafes temelleri  
  
 <xref:System.Windows.Media.Media3D.Model3D> Genel temsil eden soyut temel sınıf [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesne. Oluşturulacak bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sahnenin görüntülemek için bazı nesneler gerekir ve Sahne grafiğin nesnelerini türetilmesi <xref:System.Windows.Media.Media3D.Model3D>. Şu anda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geometriler ile modelleme destekler <xref:System.Windows.Media.Media3D.GeometryModel3D>. <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> Özelliği bu modelin kafes temel alır.  
  
 Bir model oluşturmak üzere basit bir tür oluşturarak başlayın veya kafes. A [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tek bir form köşeler koleksiyonunu ilkel [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] varlık. Çoğu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sistemleri üzerinde basit kapalı şekle modellenmiş temelleri sağlar: üç köşeler tarafından tanımlanan bir üçgen.  Üç nokta bir üçgen coplanar olduğundan, daha fazla model için üçgenler eklemeye devam edebilirsiniz karmaşık şekiller, kafesleri çağrılır.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sistemi şu anda sağlar <xref:System.Windows.Media.Media3D.MeshGeometry3D> sınıfı, tüm geometri belirtmenize olanak tanıyan; şu anda desteklemediği önceden tanımlanmış [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] temelleri Küreler ve üçüncü dereceden forms gibi. Oluşturmaya başlamak bir <xref:System.Windows.Media.Media3D.MeshGeometry3D> listesini üçgen köşelerin belirterek, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> özelliği. Her köşe olarak belirtilen bir <xref:System.Windows.Media.Media3D.Point3D>.  (İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bu özellik her köşe koordinatlarını temsil eden threes gruplandırılmış sayıdan oluşan bir liste olarak belirtin.) Geometrisini bağlı olarak, kafes birçok üçgenler, bazıları aynı köşelerini (köşe) paylaşmak oluşan. Kafes doğru bir şekilde çizmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hakkında köşeler hangi bu üçgen tarafından paylaşılır bilgilere gerek duyar. Üçgen dizin ile bir listesini belirterek bu bilgiyi sağlamak <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> özelliği. Bu liste, noktaları belirtilen sırada belirtir <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi bir üçgen belirler.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Önceki örnekte <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> küp şeklinde kafes tanımlamak için sekiz köşe listesi belirtir. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Özelliği, üç dizin on iki gruplarının bir listesini belirtir.  Listedeki her bir sayının bir uzaklık başvurduğu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi.  Örneğin, tarafından belirtilen ilk üç köşeler <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi olan (1,1,0) (0,1,0) ve (0,0,0). İlk üç tarafından belirtilen dizinleri <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> listesi: 0, 2 ve 1, ilk, üçüncü karşılık gelir ve ikinci noktaları <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi. Sonuç olarak, küp modelini yaptığı ilk üçgen (1,1,0) (0,1,0) için (0,0,0) için oluşan ve kalan on üçgenler benzer şekilde belirlenir.  
  
 Model için değerleri belirtilerek tanımlama devam <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> ve <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> özellikleri.  Modelin yüzeyine işlemek için belirli bir üçgen karşılıklı yüzey yönü hakkında bilgiler grafik sistemi gerekir. Modelin aydınlatma hesaplamaları yapmak için bu bilgileri kullanır: doğrudan ışık kaynağına yüzey ışık uzağa açılı olanlardan daha parlak görünür. Ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] normal vektörleri varsayılan belirleyebilirsiniz konumu koordinatları kullanarak eğri yüzeyleri görünümünü yaklaşık olarak belirlemenizi sağlayan farklı normal vektörleri de belirtebilirsiniz.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Özellik koleksiyonunu belirtir <xref:System.Windows.Point>grafik sistemi doku ağı köşelerini nasıl çizilmeden belirlemek koordinatları eşlemek bildiririz s. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> sıfır ile kapsamlı 1 arasında bir değer olarak belirtilir.  Olduğu gibi <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> özelliği grafik sistemi hesaplamak varsayılan doku koordinatları, ancak örneğin yinelenen bir desen ağının parçasını içeren bir dokuyu eşleşmesini kontrol etmek için farklı bir doku koordinatları ayarlamak isteyebilirsiniz. Sonraki konularda veya yönetilen Direct3D SDK doku koordinatları hakkında daha fazla bilgi bulunabilir.  
  
 Aşağıdaki örnek, yordam kodunda bir yüz küp modeli oluşturma işlemi gösterilmektedir. Tek bir GeometryModel3D'olarak tüm küp çizebilirsiniz dikkat edin. Bu örnek, küpün yüzeyi ayrı dokular her yüz için daha sonra uygulamak için farklı bir model olarak çizer.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Modele malzeme uygulama  
  
 Kafes üç boyutlu bir nesne gibi aramak bir bu üçgen ve köşeler aydınlatma ve Öngörülen bir kamera tarafından tanımlanan surface karşılamak için uygulanan bir doku olması gerekir. İçinde [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], kullandığınız <xref:System.Windows.Media.Brush> renkler, desenleri, gradyanlar veya diğer görsel içerik ekranın alanlara uygulamak için sınıfı.  Görünümünü [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesneleri, ancak bir işlev aydınlatma modeli, yalnızca rengini veya desenini uygulanmış durumdadır. Gerçek nesneleri ışık kendi yüzeyleri kalitesini bağlı olarak farklı şekilde yansıtma: parlak ve shiny yüzeyleri yoksa bakın aynı kaba veya Mat yüzeyleri ve diğer Parlayan sırada ışık etkisini azaltmak amacıyla bazı nesneler gibi görünüyor. Aynı fırçaları uygulayabilirsiniz [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] uygulayabileceğiniz nesneleri [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] nesneleri, ancak uygulayamaz bunları doğrudan.  
  
 Bir modelin yüzeyine özelliklerini tanımlamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan <xref:System.Windows.Media.Media3D.Material> soyut sınıf. Malzeme somut alt sınıflarını bazı modelin yüzeyine görünüm özelliklerini belirlemek ve her bir SolidColorBrush, TileBrush veya VisualBrush geçirebilirsiniz bir fırça özelliğini de sağlar.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> Bu modeli aydınlatma artırmadığı farklılaştırır fırça modele uygulanacağını belirler. DiffuseMaterial en kullanarak benzer doğrudan üzerinde fırçalarını kullanma [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] modelleri; ancak shiny olarak ışık yansıtmıyor modeli yüzeyleri yapın.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> modele modelin yüzeyine gibi davranarak sabit veya parlak, önemli yansıtan yeteneğine fırça uygulanacağını belirtir. İçin bir değer belirterek, doku önerisinde bulunacak bu yansıtıcı kalite veya "nokta" derecesini ayarlayabilirsiniz <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> özelliği.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> Fırça rengini açık eşit olan model yayma artırmadığı doku uygulanacak belirtmenizi sağlar. Bu model bir ışık yapmaz; Ancak, bunu DiffuseMaterial veya SpecularMaterial dokulu durumunda olduğu kadar temkinli gölgeleme içinde farklı katılacak.  
  
 Daha iyi performans için biri arka yüzlerini bir <xref:System.Windows.Media.Media3D.GeometryModel3D> (görünümden kamera modelden karşı tarafındaki oldukları için olan bu yüzeyleri) sahnenin başlangıç noktasına tam culled.  Belirtmek için bir <xref:System.Windows.Media.Media3D.Material> düzlem gibi bir modelin arkayüz uygulamak için modelin ayarlamak <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği.  
  
 Etkileri, Parlayan veya yansıtma gibi bazı yüzey kalitelerini elde etmek için birkaç farklı fırçalar bir Modeli'ne art arda uygulamak isteyebilirsiniz. Uygula ve birden çok malzemeleri kullanarak tekrar <xref:System.Windows.Media.Media3D.MaterialGroup> sınıfı. MaterialGroup alt önce son birden çok işleme geçişleri de uygulanır.  
  
 Aşağıdaki kod örnekleri renkten ve bir Çizim fırçaları olarak nasıl uygulanacağı Göster [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelleri.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Sahne illuminating  
 İçinde ışık [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafik yapmak gerçek dünyada ışıkları neler: yüzeyleri görünür yapmak. Sahne hangi kısmının projeksiyonda dahil edilecek daha noktasına ışıkları belirleyin. Açık nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli açık ve gölge efektleri oluşturun ve sonra çeşitli gerçek dünya ışık davranışını modellenir. Bir model görülebilir veya en az bir ışık, sahnede içermelidir.  
  
 Aşağıdaki ışıkları temel sınıfından türetilir <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Birörnek konumlarına veya yönlendirme bakılmaksızın tüm nesneleri aydınlatma ortam aydınlatması sağlar.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Uzak bir ışık kaynağına gibi gösterir.  Yönlü ışık sahip bir <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> bir Vector3D, ancak belirtilen konum belirtildi.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Yakındaki bir ışık kaynağına gibi gösterir. PointLights bir konuma sahiptir ve söz konusu konumdan açık tür dönüştürme. Sahnedeki nesneler, konumlarını ve ışık göre daha fazla mesafe bağlı olarak ışıklı. <xref:System.Windows.Media.Media3D.PointLightBase> kullanıma sunan bir <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> özelliği dışında modelleri değil ışıklı ışık tarafından bir uzaklığı belirler. PointLight nasıl mesafeli ışığın yoğunluğu azalır belirleyen zayıflama özellikleri de sunar. Işığın zayıflama için sabit, doğrusal veya ikinci dereceden ilişkilendirme belirtebilirsiniz.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: Devralınan <xref:System.Windows.Media.Media3D.PointLight>. Projektör gibi PointLight karanl ve hem konumuna ve yönüne sahip. Bunlar belirlediği bir Koni şeklinde alanında açık proje <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> ve <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> derece cinsinden belirtilen özellikleri.  
  
 Işıklar, <xref:System.Windows.Media.Media3D.Model3D> nesnelerine dönüştürmek ve konumu, renk, yönü ve aralığı dahil olmak üzere açık özelliklerine animasyon uygulamak için.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Modelleri dönüştürme  
 Modeli oluşturduğunuzda, belirli bir konuma sahnedeki sahiptirler. Sahne döndürmek veya bunların boyutunu değiştirmek için bu modelleri hareket etmek için bu modelleri tanımlayan köşelerini değiştirmek pratik değildir.  Bunun yerine, tam olarak [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], dönüştürmeleri modelleri için geçerlidir.  
  
 Her model nesnesi olan bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> ile taşıyabilir, yeniden yönlendirmek veya model yeniden boyutlandırma özelliği.  Dönüşüm uyguladığınızda, etkili bir şekilde modelin tüm noktaları seçtiğiniz vektör veya dönüştürme işlemi tarafından belirtilen değeri tarafından uzaklığı. Diğer bir deyişle, koordinat içinde denetleyebildiğimiz modeli olan ("alanı model") tanımlanmış ancak modelin geometri koordinat sisteminde ("dünya alanı") tüm sahnenin oluşturan değerlerini değiştirmezsiniz.  
  
 Dönüşüm modelleri hakkında daha fazla bilgi için bkz. [3B Dönüşümlere Genel Bakış](3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Modelleri animasyon ekleme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Aynı zamanlama ve animasyon sisteme katılan uygulama [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafik. Diğer bir deyişle, 3B Görünümü animasyon eklemek gibi modellerinin özelliklerine animasyon ekleme. Temel özellikleri doğrudan oynatmak mümkün olduğu halde konumunu veya modelleri görünümünü değiştirme dönüşümleri animasyon uygulamak genellikle daha kolay olur. Dönüştürmeler uygulanabilir olduğundan <xref:System.Windows.Media.Media3D.Model3DGroup> nesneleri ayrı ayrı modeller yanı sıra, tek bir Model3DGroup alt ve alt nesnelerin bir grubu başka bir kümesini uygulamak olabilir. Ayrıca, sahnenin aydınlatma özelliklerini animasyon tarafından birçok görsel efektler elde edebilirsiniz. Son olarak, görünüm alanı ve kamera konumuna animasyon ekleme projeksiyon animasyon uygulamak seçebilirsiniz. Üzerinde arka plan bilgileri için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamanlama ve animasyon sistemi bkz [animasyona genel bakış](animation-overview.md), [görsel taslaklara genel bakış](storyboards-overview.md), ve [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md)konuları.  
  
 İçinde bir nesneye animasyon ekleme için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir zaman çizelgesi oluşturun (gerçekten bazı özellik değerinde bir değişiklik zaman içinde) bir animasyon tanımlayın ve animasyon uygulamak istediğiniz özelliğini belirtin. Çünkü bulunan tüm nesnelerin bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne olan alt <xref:System.Windows.Controls.Viewport3D>, sahneye uygulamak istediğiniz herhangi bir animasyon tarafından hedeflenen Viewport3D özelliklerinin özelliklerdir.  
  
 Bir model yerinde sallanmasına görünür yapmak istediğinizi varsayalım. Uygulama tercih edebileceğiniz bir <xref:System.Windows.Media.Media3D.RotateTransform3D> modeline ve bir vektör döndürme başka bir eksen animasyon ekleme. Aşağıdaki kod örneği bir TransformGroup modeliyle uygulanan dönüşümlerden birini olmasını RotateTransform3D varsayıldığında, dönüşümün Rotation3D Axis özelliği bir Vector3DAnimation uygulanması gösterilmektedir.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>3B içerik için pencere Ekle  
 Bir sahneyi işleme için modelleri ve ışıklara ekleyin bir <xref:System.Windows.Media.Media3D.Model3DGroup>, ardından <xref:System.Windows.Media.Media3D.Model3DGroup> olarak <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> , bir <xref:System.Windows.Media.Media3D.ModelVisual3D>. Ekleme <xref:System.Windows.Media.Media3D.ModelVisual3D> için <xref:System.Windows.Controls.Viewport3D.Children%2A> koleksiyonunu <xref:System.Windows.Controls.Viewport3D>. Kameralar için ekleme <xref:System.Windows.Controls.Viewport3D> ayarlayarak onun <xref:System.Windows.Controls.Viewport3D.Camera%2A> özelliği.  
  
 Son olarak, ekleme <xref:System.Windows.Controls.Viewport3D> penceresine. Zaman <xref:System.Windows.Controls.Viewport3D> tuval gibi bir düzen öğenin içeriğini belirlerken Viewport3D boyutunu ayarlayarak dahildir, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri (devralınan <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [3B Dönüşümlere Genel Bakış](3-d-transformations-overview.md)
- [WPF 3B Performansını En Üst Düzeye Çıkarma](maximize-wpf-3d-performance.md)
- [Nasıl Yapılır Konuları](3-d-graphics-how-to-topics.md)
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
