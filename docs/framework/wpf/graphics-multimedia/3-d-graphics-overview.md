---
title: "3B Grafiklere Genel Bakış"
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
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58b756c24c1ca7e3f5b6b3f13c314363daf35443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="3-d-graphics-overview"></a>3B Grafiklere Genel Bakış
<a name="introduction"></a>[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] İşlevindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] geliştiricilerin çizim, dönüştürme ve 3-b grafik işaretleme ve yordam kodunda animasyon sağlar. Geliştiriciler birleştirebilirsiniz [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] ve [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] zengin denetimleri oluşturmak, veri karmaşık çizimleri sağlayın veya kullanıcı geliştirmek için grafik deneyimi bir uygulamanın arabirimi. [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]desteklemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tam özellikli bir oyun geliştirme platformu sağlamak üzere tasarlanmamıştır. Bu konu genel bir bakış sağlar [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] işlevindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik sistemi.  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>2-D kapsayıcısında 3-b  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]grafik içeriği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir öğedeki kapsüllenmiş <xref:System.Windows.Controls.Viewport3D>, iki boyutlu öğe yapısında katılmak. Grafik sistemi değerlendirir <xref:System.Windows.Controls.Viewport3D> diğer birçok gibi iki boyutlu bir görsel öğe olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D>bir pencere olarak çalışır — bir görünüm penceresinin — üç boyutlu Sahne içine. Daha doğru bir şekilde bir yüzeyine olan bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne öngörülen.  
  
 Geleneksel olarak [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] uygulama, kullanım <xref:System.Windows.Controls.Viewport3D> ızgara veya tuvale gibi başka bir kapsayıcı öğe gibi.  Kullanabilirsiniz ancak <xref:System.Windows.Controls.Viewport3D> diğer [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aynı Sahne grafiği çizim nesneleri, size işleyemezsiniz [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] ve [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içindeki nesneleri bir <xref:System.Windows.Controls.Viewport3D>.  Bu konuda çizin nasıl odaklanacaktır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafik içinde <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3-b koordinat  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Koordinat sistemi için [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafik sol üst (genellikle ekran) işleme alanının başlangıç noktasını bulur. İçinde [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sistem, pozitif x ekseni değerleri sağa devam etmek ve pozitif y ekseni değerleri aşağı doğru devam edin.  İçinde [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] koordinat sistemi, ancak kaynak pozitif x ekseni değerleri sağa ancak bunun yerine yukarı doğru devam ederek pozitif y ekseni değerleri ve dışa pozitif z ekseni değerleri işleme alan Center'da bulunan kaynaktan Görüntüleyici bulunun.  
  
 ![Koordinat sistemleri](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Geleneksel 2 ve 3 boyutlu koordinat sistemi temsili  
  
 Bu eksenler tarafından tanımlanan başvuru çerçevesidir için alandır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesnelerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Bu alanda modelleri oluşturabilir ve ışık oluşturup bunları görüntülemek için kameralar gibi bu başvuru çerçevesidir ya da "world alanı," yerel dönüşümleri uyguladığınızda, her model için oluşturduğunuz başvuru çerçevesini ayırmak yararlıdır. Ayrıca, dünya uzayındaki nesnelerin tamamen farklı arayın veya hiç görünmez, açık ve Kamera bağlı olarak ayarlar, ancak kamera konumunu değiştirmez dünya uzayındaki nesnelerin konumunu olduğunu unutmayın.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Kamera ve projeksiyonu  
 İş geliştiriciler [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] iki boyutlu bir ekranda çizim temelleri konumlandırma alışkın. Oluştururken bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne, onu sizin gerçekten oluşturma unutmamak bir [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] gösterimini [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesneleri. Çünkü bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sahne izleyicisinin bakış açısı bağlı olarak farklı görünüyor, bu bakış açısı belirtmeniz gerekir. <xref:System.Windows.Media.Media3D.Camera> Sınıfı bu bakış açısı için belirtmenize olanak sağlayan bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne.  
  
 Anlamak için başka bir şekilde nasıl bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne temsil üzerinde bir [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] yüzeyini olan bir yansıtma görüntüleme yüzeyine olarak Sahne açıklayarak. <xref:System.Windows.Media.Media3D.ProjectionCamera> Farklı tahminleri ve özelliklerinin nasıl izleyicisinin göreceğini değiştirmek için belirtmenize olanak tanır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modeller. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> Sahne foreshortens bir yansıtma belirtir.  Diğer bir deyişle, <xref:System.Windows.Media.Media3D.PerspectiveCamera> kaybolmasını noktası perspektif sağlar.  Koordinat Sahne, yön ve görünüm alanı kamera ve görünüm yönünü "yedekleme" tanımlayan vektör kamera konumu belirtebilirsiniz. Aşağıdaki diyagramda gösterilmektedir <xref:System.Windows.Media.Media3D.PerspectiveCamera>'s projeksiyon.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Ve <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> özelliklerini <xref:System.Windows.Media.Media3D.ProjectionCamera> kameranın projeksiyon aralığını sınırlayın. Kameralar Sahne bir yerde bulunan olabileceğinden, aslında bir model içinde ya da nesneleri düzgün ayırt etmek sabit yapmadan çok bir model yanına konumlandırılması kamera mümkündür.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>en az uzaklığı sonrasında nesneleri değil çizileceğini kameradan belirtmenize olanak tanır.  Buna karşılık, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> tanınabilir olmasını çok uzakta nesneleri Sahne eklenmeyecek sağlayan nesneleri değil çizilen, kamera mesafe belirtmenize olanak sağlar.  
  
 ![Kamera Kurulum](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem-6")  
Kamera konumu  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>orthogonal projeksiyon çekirdeğinin belirten bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] model için bir [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] visual yüzeyini. Diğer kameralar gibi yönü ve "yukarı" yönü görüntüleme bir konum belirtir. Farklı <xref:System.Windows.Media.Media3D.PerspectiveCamera>, ancak <xref:System.Windows.Media.Media3D.OrthographicCamera> perspektif foreshortening içermeyen bir yansıtma açıklar. Diğer bir deyişle, <xref:System.Windows.Media.Media3D.OrthographicCamera> , kenarı bir, iki tarafı da karşılayan kamera bir noktada içinde yerine paralel görüntüleme kutusunu açıklar. Aşağıdaki görüntüde aynı modeli kullanarak görüntülendiği şekilde gösterilmektedir <xref:System.Windows.Media.Media3D.PerspectiveCamera> ve <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Ortografik ve perspektif projeksiyon](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera_projections4")  
Perspektif ve Dikçizgisel projeksiyonu  
  
 Aşağıdaki kod, bazı tipik kamera ayarlarını gösterir.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Model ve kafes temelleri  
  
 <xref:System.Windows.Media.Media3D.Model3D>Genel temsil eden Özet temel sınıf [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesnesi. Derleme için bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne, görüntülemek için bazı nesneler gerekir ve Sahne grafiğin nesnelerini türetin <xref:System.Windows.Media.Media3D.Model3D>. Şu anda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile geometri modelleme destekler <xref:System.Windows.Media.Media3D.GeometryModel3D>. <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> Özelliği bu modelin kafes temel alır.  
  
 Bir model oluşturmak için bir temel oluşturarak başlayın veya kafes. A [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tek bir form köşeleri ilkel koleksiyonudur [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] varlık. Çoğu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sistemleri, en basit kapalı şekil Modellenen temelleri sağlar: üç köşeleri tarafından tanımlanan bir üçgen.  Üç nokta bir üçgen coplanar olduğundan, daha fazla model için üçgenler eklemeye devam edebilirsiniz karmaşık şekiller, kafesleri çağrılır.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sistem şu anda sağlar <xref:System.Windows.Media.Media3D.MeshGeometry3D> sınıfı, tüm geometri belirtmenize olanak sağlayan; şu anda desteklemediği önceden tanımlanmış [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] temelleri Küreler ve küp formlar gibi. Oluşturmaya başlamak bir <xref:System.Windows.Media.Media3D.MeshGeometry3D> üçgen köşeleri listesi belirterek kendi <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> özelliği. Her köşe olarak belirtilen bir <xref:System.Windows.Media.Media3D.Point3D>.  (İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bu özellik her köşesinin koordinatlarını temsil eden threes içinde gruplandırılmış sayıdan oluşan bir liste olarak belirtin.) Kendi geometri bağlı olarak, birçok üçgenler, bazıları aynı köşeleri (köşeleri) paylaşımı, kafes oluşan. Mesh doğru çizmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hakkında köşeleri hangi üçgen tarafından paylaşıldığı bilgi gerekiyor. Üçgen dizinlerini ile listesi belirterek bu bilgileri verdikten <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> özelliği. Bu liste, noktaları belirtilen sırada belirtir <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi bir üçgen belirler.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Önceki örnekte <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi küp şeklinde kafes tanımlamak için sekiz köşeleri belirtir. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Özelliği, üç dizin on iki gruplarının bir listesini belirtir.  Bir uzaklık listede her numarasını başvurduğu <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi.  Örneğin, tarafından belirtilen ilk üç köşeleri <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi olan (1,1,0) (0,1,0) ve (0,0,0). Tarafından belirtilen ilk üç dizinlerini <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> listesi: 0, 2 ve 1, ilk, üçüncü karşılık gelir ve ikinci noktaları <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listesi. Sonuç olarak, küp modelini yapar ilk üçgen (1,1,0) (0,1,0) (0,0,0) oluşur ve kalan on üçgenler benzer şekilde belirlenir.  
  
 Model için değerleri belirtilerek tanımlama devam <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> ve <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> özellikleri.  Model yüzeyinin işlemek için grafik sistemi herhangi verilen üçgen karşılıklı yönü yüzeyini hakkında bilgi gerekiyor. Modelin aydınlatma hesaplamaları yapmak için bu bilgileri kullanır: doğrudan ışık kaynağının doğru yüz yüzeyleri çıktığınızda ışık açılı olandan daha açık görünür. Ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan normal vektörlerinin belirleyebilirsiniz konumu koordinatları kullanarak eğri yüzeyleri görünümünü yaklaşık için farklı normal vektörlerinin de belirtebilirsiniz.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Özellik koleksiyonu belirtir <xref:System.Windows.Point>grafik sistemi doku kafes köşe için nasıl çizilir belirlemek koordinatları eşlemek nasıl anlatın s. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>sıfır ve 1 ' (dahil) arasında bir değer olarak belirtilir.  İle <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> özelliği, grafik sistemi hesaplamak varsayılan doku koordinatları, ancak örneğin yinelenen bir desen bölümünü içeren bir doku eşleme denetlemek için farklı doku koordinatlarını ayarlamak isteyebilirsiniz. Sonraki konularda veya yönetilen Direct3D SDK doku koordinatları hakkında daha fazla bilgi bulunabilir.  
  
 Aşağıdaki örnek yordam kodda bir yazıtipi küp modelinin oluşturulacağını gösterir. Tek bir GeometryModel3D olarak tüm küp çizebilirsiniz unutmayın; Bu örnek daha sonra ayrı dokuları her yüz uygulamak için ayrı bir model olarak küpün yüz çizer.  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Modele malzemeleri uygulama  
  
 Bir kafes üç boyutlu bir nesne gibi aramak aydınlatma ve kamera tarafından öngörülen kendi köşeleri ve üçgenler tarafından tanımlanan yüzeyini karşılamak için uygulanan bir doku sahip olmalıdır. İçinde [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], kullandığınız <xref:System.Windows.Media.Brush> renkleri, desenleri, gradyanlar veya diğer görsel içerik ekranın alanlara uygulamak için sınıf.  Görünümünü [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] nesneleri, ancak, bir işlev aydınlatma modelinin, yalnızca rengini veya desenini uygulanmış durumdadır. Gerçek dünya nesneleri yansıtma kendi yüzeyleri kalitesini bağlı olarak farklı ışık: parlak ve parlak yüzeyleri yok arayın aynı kaba veya Mat yüzeyleri ve diğerleri Parlayan sırada ışık almak amacıyla bazı nesneler gibi görünebilir. Fırçalar için aynı uygulayabilirsiniz [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] uygulayabileceğiniz nesneleri [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] nesneleri, ancak olamaz uygulamak bunları doğrudan.  
  
 Bir modelin yüzey özelliklerini tanımlamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan <xref:System.Windows.Media.Media3D.Material> soyut sınıf. Somut alt sınıfları malzeme bazı modelin yüzey görünüm özelliklerini belirlemek ve her SolidColorBrush, TileBrush veya VisualBrush geçirebilirsiniz fırça özelliği de sağlar.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial>Bu model aydınlatma gibi sorgulamanıza diffusely fırça modele uygulanır belirtir. DiffuseMaterial en kullanarak benzer Fırçalar doğrudan üzerinde kullanarak [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] modelleri; ancak parlak olarak açık yansıtacak değil modeli yüzeyleri yapın.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial>modelin yüzey gibi davranarak sabit veya parlak, vurgular yansıtma yeteneğine fırça modele uygulanır belirtir. İçin bir değer belirterek, doku önermek bu yansıtıcı kalitesini ya da "bekliyoruz," derece ayarlayabilirsiniz <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> özelliği.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial>Doku olan model yayma gibi sorgulamanıza fırça rengi hafif eşit uygulanacak belirtmenize olanak tanır. Bu model ışık yapmaz; Ancak, bunu paylaştıklarında DiffuseMaterial veya SpecularMaterial ile doku durumunda olduğu gölgeleme içinde farklı almayacak.  
  
 Daha iyi performans için arka yüzeyleri, bir <xref:System.Windows.Media.Media3D.GeometryModel3D> (Görünüm dışında kamera modelden karşı tarafındaki oldukları için olan bu yazıtipleri) Sahne culled.  Belirtmek için bir <xref:System.Windows.Media.Media3D.Material> düzlem gibi bir modelin backface uygulamak için modelin ayarlamak <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği.  
  
 Işıyan veya yansıtıcı efektler gibi bazı yüzey nitelikleri elde etmek için bir model art arda birkaç farklı fırçalar uygulamak isteyebilirsiniz. Uygulama ve birden çok malzemeleri kullanarak tekrar <xref:System.Windows.Media.Media3D.MaterialGroup> sınıfı. MaterialGroup alt ilk birden çok işleme geçişleri son uygulanır.  
  
 Düz renk ve bir çizim için Fırçalar olarak uygulamak nasıl aşağıdaki kodu örnekler [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modeller.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Sahne illuminating  
 İçinde ışık [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafik yapın ışık gerçek dünyada ne: yüzeyleri görünür yapın. Daha fazla noktasına bir Sahne hangi kısmının projeksiyon dahil edilecek ışık belirler. Açık nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli açık ve gölge efektleri oluşturun ve sonra çeşitli gerçek ışık davranışını modellenir. En az bir açık, Sahne içermelidir veya hiçbir modeli görünür olur.  
  
 Aşağıdaki ışık temel sınıfından türetilir <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Hep konumlarına veya yönlendirme bakılmaksızın tüm nesneleri gösterir ortam aydınlatma sağlar.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Bir uzak ışık kaynağının gibi gösterir.  Tek yönlü ışık sahip bir <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> belirtilmiş bir Vector3D, ancak belirtilen konumu yok.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Yakındaki bir açık kaynak gibi gösterir. PointLights bir konuma sahip ve bu konumdan açık atama. Sahne nesneler, bağlı olarak, konum ve açık göre uzaklığı ışıklı. <xref:System.Windows.Media.Media3D.PointLightBase>kullanıma sunan bir <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> sonrasında modelleri değil ışıklı tarafından açık bir uzaklık belirler özelliği. PointLight de nasıl ışık 's yoğunluğu mesafeli düşer belirleyen Zayıflatma özellikleri sunar. Açık 's Zayıflatma sabit, doğrusal veya ikinci derece ilişkilendirme belirtebilirsiniz.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: Devralınan <xref:System.Windows.Media.Media3D.PointLight>. Projektör gibi PointLight karanl ve konum ve yön vardır. Tarafından belirlenen Koni şeklinde alanında açık proje <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> ve <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> özellikler, derece cinsinden belirtilmiş.  
  
 Işık olan <xref:System.Windows.Media.Media3D.Model3D> nesneleri dönüştürme ve konum, renk, yön ve aralığı dahil olmak üzere açık özellikleri.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Dönüşüm modelleri  
 Modelleri oluşturduğunuzda Sahne belirli bir konumda sahiptirler. Sahne döndürmek ya da kendi boyutunu değiştirmek için bu modelleri hareket etmek için bu modelleri tanımlayan köşeleri değiştirmek mümkün değil.  Bunun yerine, tam olarak [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], dönüşümleri modellere uygulayın.  
  
 Her model nesnesi olan bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> ile taşıyabilir, yeniden yönlendirmek veya model yeniden boyutlandırma özelliği.  Dönüşüm uyguladığınızda, etkili bir şekilde modelinin tüm noktalarını ne olursa olsun vektör veya dönüşüm tarafından belirtilen değeri uzaklık. Diğer bir deyişle, koordinat alanında dönüştürdükten model olan ("model uzayı") tanımlı, ancak tüm Sahne ("world alanı") koordinat sistemi içinde modelin geometri oluşturan değerleri değiştirmezsiniz.  
  
 Dönüşüm modelleri hakkında daha fazla bilgi için bkz: [3-b dönüşümler genel bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Modelleri animasyon ekleme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Uygulama katılan aynı zamanlama ve animasyon sistemde [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafik. Diğer bir deyişle, 3B Sahne animasyon için kendi modellerinin özelliklerini animasyon. Elemanlar özelliklerine doğrudan animasyon mümkündür, ancak konum veya modelleri görünümünü değiştirme dönüşümleri animasyon genellikle daha kolay. Dönüşümleri uygulanabilir çünkü <xref:System.Windows.Media.Media3D.Model3DGroup> nesneleri tek tek modellerin yanı sıra tek bir Model3DGroup bir alt kümesini ve diğer alt nesnelerin bir grubuna uygulamak mümkündür. Görsel efektler çeşitli Sahne ait ışık özelliklerini animasyon tarafından da elde edebilirsiniz. Son olarak, kamera konumu ya da görünüm alanı animasyon projeksiyon hale getirmeyi tercih edebilirsiniz. Arka plan bilgileri için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamanlama ve animasyon sistemi bkz [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md), [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md), ve [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)Konular.  
  
 Bir nesnenin animasyon için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir zaman çizelgesi oluşturun (gerçekten bazı özellik değerinde bir değişiklik zaman içinde) bir animasyon tanımlayın ve animasyonun uygulanacağı özelliği belirtin. Çünkü tüm nesneleri bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Sahne olan alt <xref:System.Windows.Controls.Viewport3D>, Sahne uygulamak istediğiniz animasyon tarafından hedeflenen özellikler Viewport3D özelliklerinin özellikleridir.  
  
 Bir model yerinde sallanmasına görünür yapmak istediğinizi varsayalım. Uygula tercih edebileceğiniz bir <xref:System.Windows.Media.Media3D.RotateTransform3D> modeline ve bir vektör döndürme başka bir eksen animasyon. Aşağıdaki kod örneğinde, uygulanacak bir TransformGroup modeliyle uygulanan birkaç Dönüşümlerin biri RotateTransform3D varsayılarak dönüşümün Rotation3D eksen özelliğine bir Vector3DAnimation uygulama örneğini gösterir.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>Pencereyi 3-b içerik ekleme  
 Sahne işlemek için modelleri için ışık ekleyip bir <xref:System.Windows.Media.Media3D.Model3DGroup>, ardından <xref:System.Windows.Media.Media3D.Model3DGroup> olarak <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> , bir <xref:System.Windows.Media.Media3D.ModelVisual3D>. Ekleme <xref:System.Windows.Media.Media3D.ModelVisual3D> için <xref:System.Windows.Controls.Viewport3D.Children%2A> koleksiyonu <xref:System.Windows.Controls.Viewport3D>. İçin kameralar eklemek <xref:System.Windows.Controls.Viewport3D> ayarlayarak kendi <xref:System.Windows.Controls.Viewport3D.Camera%2A> özelliği.  
  
 Son olarak, ekleme <xref:System.Windows.Controls.Viewport3D> penceresine. Zaman <xref:System.Windows.Controls.Viewport3D> Kanvasın gibi bir düzen öğesi içeriği belirtmek gibi Viewport3D boyutunu ayarlayarak bulunur, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri (devralınan <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Viewport3D>  
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>  
 <xref:System.Windows.Media.Media3D.DirectionalLight>  
 <xref:System.Windows.Media.Media3D.Material>  
 [3B Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)  
 [WPF 3B Performansını En Üst Düzeye Çıkarma](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
