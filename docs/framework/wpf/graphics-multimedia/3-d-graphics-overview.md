---
title: 3B Grafiklere Genel Bakış
description: Hem biçimlendirme hem de yordamsal kodda 3B grafikleri çizmek, dönüştürmek ve hareketlendirmek için Windows Presentation Foundation (WPF) içindeki 3B grafiklerle tanışın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: aa4f45ac426c59b829b6be9e63e8f0ed50512661
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358927"
---
# <a name="3d-graphics-overview"></a>3B Grafiklere Genel Bakış
<a name="introduction"></a> İçindeki 3B işlevselliği, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] geliştiricilerin hem biçimlendirme hem de yordamsal koddaki 3B grafikleri çizmesini, dönüştürmesini ve animasyonunu sağlar. Geliştiriciler zengin denetimler oluşturmak, karmaşık veri çizimleri sağlamak ya da bir uygulamanın arabiriminin Kullanıcı deneyimini geliştirmek için 2B ve 3B grafikleri birleştirebilir. ' da 3B desteği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , tam özellikli bir oyun geliştirme platformu sağlamak üzere tasarlanmamıştır. Bu konuda, grafik sisteminde 3B işlevlere genel bir bakış sunulmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>2B kapsayıcıda 3B  
 içindeki 3B grafik içeriği, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Viewport3D> iki boyutlu öğe yapısına katılabileceğiniz bir öğesi içinde kapsüllenir. Grafik sistemi, <xref:System.Windows.Controls.Viewport3D> ' de birçok farklı gibi iki boyutlu bir görsel öğe gibi davranır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . <xref:System.Windows.Controls.Viewport3D> üç boyutlu bir sahneye pencere görünümü (Görünüm penceresi) olarak işlevler. Daha doğru bir şekilde, 3B sahnenin yansıtılmasına yönelik bir yüzey vardır.  
  
 Geleneksel bir 2B uygulamada, <xref:System.Windows.Controls.Viewport3D> kılavuz veya tuval gibi başka bir kapsayıcı öğesi gibi kullanın.  <xref:System.Windows.Controls.Viewport3D>Aynı sahne grafiğinde diğer 2B çizim nesneleriyle birlikte kullanabilseniz de, 2B ve 3B nesnelerini bir içinde iç değerlendirin <xref:System.Windows.Controls.Viewport3D> .  Bu konu, içinde 3B grafiklerin nasıl çizildiği üzerine odaklanacaktır <xref:System.Windows.Controls.Viewport3D> .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>3B koordinat alanı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]2B grafik için koordinat sistemi, oluşturma alanının sol üst kısmındaki kaynağı bulur (genellikle ekran). 2B sistemde, pozitif x ekseni değerleri doğru ve pozitif y ekseni değerleri aşağı devam ediyor.  Ancak, 3B koordinat sisteminde, kaynak işleme alanının ortasında bulunur, pozitif x ekseni değerleri sağa devam ediyor ancak pozitif y ekseni değerleri sıfırdan devam ediyor, ancak pozitif z ekseni değerleri, görüntüleyiciye doğru, sıfırdan dışarı doğru devam ediyor.  
  
 ![Koordinat sistemleri](./media/coordsystem-1.png "CoordSystem-1")  
Geleneksel 2B ve 3B koordinat sistemi gösterimleri  
  
 Bu eksenlerde tanımlanan alan, içindeki 3D nesneler için sabit başvuru çerçevesidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Bu alanda modeller oluştururken ve bunları görüntülemek için ışıklar ve kameralar oluşturdığınızda, buna dönüşümler uyguladığınızda, bu sabit başvuru çerçevesini veya "Dünya alanı" ' nı her bir model için oluşturduğunuz yerel başvuru çerçevelerinden ayırt etmek yararlı olur. Ayrıca, açık ve kamera ayarlarına bağlı olarak dünya alanındaki nesnelerin tamamen farklı görünebileceğini veya hiç görünmediğine de unutmayın, ancak kameranın konumu Dünya alanındaki nesnelerin konumunu değiştirmez.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Kameralar ve Projeksiyonler  
 2B ' de çalışan geliştiriciler, çizim temel temellerine iki boyutlu bir ekrana konumlandırması için tasarlanmıştır. 3B bir görünüm oluşturduğunuzda, gerçekten 3B nesne 2B gösterimi oluşturduğunuz unutulmamalıdır. Bir 3B sahne, onlooker 'ın görünüm noktasına bağlı olarak farklı göründüğünden, o görünüm noktasını belirtmeniz gerekir. <xref:System.Windows.Media.Media3D.Camera>Sınıfı, bir 3B sahnenin bu görünüm noktasını belirtmenizi sağlar.  
  
 3B sahnenin 2B bir yüzey üzerinde nasıl temsil edileceğini anlamak için bir diğer yol, sahneyi görüntüleme yüzeyi üzerine bir projeksiyon olarak açıklamalıdır. , <xref:System.Windows.Media.Media3D.ProjectionCamera> Onlooker 'ın 3B modellerini nasıl göreceğini değiştirmek için farklı projeksiyonlar ve bunların özelliklerini belirtmenize olanak tanır. <xref:System.Windows.Media.Media3D.PerspectiveCamera>Sahne, sahneyi oluşturan bir projeksiyonu belirler.  Diğer bir deyişle, <xref:System.Windows.Media.Media3D.PerspectiveCamera> ufuk noktası perspektifi sağlar.  Kameranın koordinat alanında sahnenin konumunu, kameranın görünüm yönünü ve alanını ve sahnede "Up" yönünü tanımlayan bir vektörü belirtebilirsiniz. Aşağıdaki diyagramda, <xref:System.Windows.Media.Media3D.PerspectiveCamera> projeksiyonu gösterilmektedir.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>Ve <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> Özellikleri, <xref:System.Windows.Media.Media3D.ProjectionCamera> kameranın projeksiyonunun aralığını sınırlar. Kameralar sahnenin herhangi bir yerinde konumlandırıldığından, kameranın gerçekten bir modelin içine yerleştirilmesi veya bir modelin yakınında konumlandırılması, nesneleri düzgün bir şekilde ayırt edebilmesini mümkün hale getirir.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> kameradan, nesnelerin çizilmeyecek olan en küçük mesafeyi belirtmenize olanak tanır.  Buna karşılık, nesnelerin <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> çizilmeyeceği bir uzaklığı belirtmenize izin verir, bu da nesnelerin çok fazla uzakta olmasını sağlar sahneye dahil edilmez.  
  
 ![Kamera kurulumu](./media/coordsystem-6.png "CoordSystem-6")  
Kamera konumu  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> 2B görsel yüzeyle 3B modelin diksel projeksiyonunu belirtir. Diğer kameralar gibi, bir konum, görüntüleme yönü ve "yukarı" yönü belirtir. <xref:System.Windows.Media.Media3D.PerspectiveCamera>Ancak aksine, <xref:System.Windows.Media.Media3D.OrthographicCamera> perspektif foreshorcu içermeyen bir projeksiyon açıklanmaktadır. Diğer bir deyişle, tarafları <xref:System.Windows.Media.Media3D.OrthographicCamera> kameranın bir noktasında buluşmak yerine, kenarları paralel olan bir görüntüleme kutusunu açıklar. Aşağıdaki görüntüde ve kullanılarak görüntülenen aynı model gösterilmektedir <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> .  
  
 ![Orgraphic ve perspektif projeksiyonu](./media/camera-projections4.png "Camera_projections4")  
Perspektif ve Dikçizgisel Projeksiyler  
  
 Aşağıdaki kodda bazı tipik kamera ayarları gösterilmektedir.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Model ve kafes temelleri  
  
 <xref:System.Windows.Media.Media3D.Model3D> , genel bir 3B nesneyi temsil eden soyut temel sınıftır. 3B bir sahne oluşturmak için bazı nesnelerin görüntüleneceği ve sahne grafiğini oluşturan nesnelerin türevi olması gerekir <xref:System.Windows.Media.Media3D.Model3D> . Şu anda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile modelleme geometrileri destekler <xref:System.Windows.Media.Media3D.GeometryModel3D> . <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>Bu modelin özelliği bir kafes temel alır.  
  
 Bir model oluşturmak için, bir temel veya ağ oluşturarak başlayın. 3B temel, tek bir 3B varlık oluşturan köşelerin koleksiyonudur. Birçok 3B sistem, en basit kapalı şekle göre modellenen temel elemanlar sağlar: üç köşelere göre tanımlanan bir üçgen.  Bir üçgenin üç noktası coplanar olduğundan, kafesler olarak adlandırılan daha karmaşık şekilleri modellemek için üçgenler eklemeye devam edebilirsiniz.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3B sistem şu anda <xref:System.Windows.Media.Media3D.MeshGeometry3D> herhangi bir geometri belirtmenize olanak tanıyan sınıfını sağlar; Şu anda, sıntes ve üçüncü dereceden formlar gibi önceden tanımlanmış 3B temelleri desteklemez. <xref:System.Windows.Media.Media3D.MeshGeometry3D>Özelliği olarak üçgen köşelerin bir listesini belirterek oluşturma işlemini başlatın <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> . Her köşe bir olarak belirtilir <xref:System.Windows.Media.Media3D.Point3D> .  (İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , her bir köşenin koordinatlarını temsil eden Threes 'de gruplanmış sayı listesi olarak bu özelliği belirtin.) Kendi geometrisine bağlı olarak, bir kısmı aynı köşeleri (köşeler) paylaşan birçok üçgenden oluşabilir. Kafesi doğru çizmek için hangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] köşelerin hangi köşeler tarafından paylaşıldığını öğrenmek için gereken bilgiler gereklidir. Bu bilgileri, özelliği ile üçgen dizinlerinin bir listesini belirterek sağlarsınız <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> . Bu liste, listede belirtilen noktaların <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> bir üçgeni belirlemede kullanılacak sırayı belirtir.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Yukarıdaki örnekte, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste küp şeklinde bir kafes tanımlamak için sekiz köşe belirler. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>Özelliği, üç indisin on iki grubun listesini belirtir.  Listedeki her bir sayı, listenin bir denkleşi anlamına gelir <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> .  Örneğin, liste tarafından belirtilen ilk üç köşe <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> (1, 1, 0), (0, 1, 0) ve (0, 0, 0). Liste tarafından belirtilen ilk üç Dizin, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> listedeki birinci, üçüncü ve ikinci noktalara karşılık gelen 0, 2 ve 1 ' dir <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> . Sonuç olarak, küp modelini oluşturan ilk üçgen (1, 1, 0) ile (0, 1, 0) arasında (0, 0, 0) ve diğer on en çok üçgen de benzer şekilde belirlenir.  
  
 Ve özellikleri için değerler belirterek modeli tanımlamaya devam edebilirsiniz <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> .  Modelin yüzeyini işlemek için grafik sisteminde, yüzeyin herhangi bir üçgende hangi yöne bakan konusunda bilgi gerekir. Bu bilgileri, model için aydınlatma hesaplamaları yapmak amacıyla kullanır: doğrudan bir ışık kaynağına doğru olan yüzeyler, ışığın dışında bir yüzden daha parlaktır. , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Konum koordinatlarını kullanarak varsayılan normal vektörleri belirleyebilse de, eğimli yüzeylerin görünümünü tahmin etmek için farklı normal vektörler de belirtebilirsiniz.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>Özelliği, <xref:System.Windows.Point> grafik sistemine bir dokunun kafesin köşelerine nasıl çizildiğini belirleyen koordinatları nasıl eşleyeceğini söyleyen bir koleksiyonunu belirtir. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Sıfır ve 1 (dahil) arasında bir değer olarak belirtilir.  Özelliği ile olduğu gibi <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> , grafik sistemi varsayılan doku koordinatlarını hesaplayabilir, ancak yineleme deseninin bir parçasını içeren bir dokunun eşlemesini denetlemek için farklı doku koordinatları ayarlamayı tercih edebilirsiniz. Doku koordinatları hakkında daha fazla bilgi, sonraki konularda veya yönetilen Direct3D SDK 'sında bulunabilir.  
  
 Aşağıdaki örnek, yordamsal kodda küp modelinin bir yüzünün nasıl oluşturulacağını gösterir. Tüm küpü tek bir Geometrymodel3d 'nin geometrisini olarak çizebilirsiniz; Bu örnek, daha sonra her bir yüzüne ayrı dokular uygulamak için küpün yüzünü ayrı bir model olarak çizer.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Modele malzemeler uygulanıyor  
  
 Bir kafesin üç boyutlu bir nesne gibi görünmesi için, köşelere ve Üçgenlerine göre tanımlanan yüzeyi kapsayan bir dokusunun olması gerekir; böylece bu, kamera tarafından aydınlatılır ve tahmin edilebilir. 2B ' de, <xref:System.Windows.Media.Brush> renkleri, desenleri, degradeleri veya diğer görsel içerikleri ekranın bölümlerine uygulamak için sınıfını kullanırsınız.  Ancak 3B nesnelerinin görünümü yalnızca, bunlara uygulanan renge veya modele göre değil, aydınlatma modelinin bir işlevidir. Gerçek dünyadaki nesneler, yüzeylerinin kalitesine bağlı olarak ışığın farklı şekilde yansıtılmasını sağlar: parlak ve parlak yüzeyler, kaba ve mat yüzeyleriyle aynı görünmüyor ve bazı nesneler artışlarını devralarak ışığı halinde görünür. 2B nesnelere uygulayabileceğiniz 3B nesnelere aynı fırçaların tümünü uygulayabilirsiniz, ancak bunları doğrudan uygulayamazsınız.  
  
 Bir modelin yüzeyinin özelliklerini tanımlamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.Media3D.Material> soyut sınıfı kullanır. Malzemenin somut alt sınıfları, model yüzeyinin bazı görünüm özelliklerini tespit edebilir ve her biri, bir SolidColorBrush, TileBrush veya VisualBrush geçirebilmeniz için bir fırça özelliği de sağlar.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial> fırçayla birlikte kullanılması için fırçanın modele uygulanacağını belirtir. En fazla Diffusemalzemesini kullanarak doğrudan 2B modeller üzerinde fırçalar kullanın; Model yüzeyleri, ışıkla birlikte ışığı yansıtmaz.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial> Fırçanın,, vurguları yansıtmada sert veya parlak olmasına rağmen modele uygulanacağını belirtir. Dokunun bu yansıtıcı kaliteyi önereceği dereceyi veya özellik için bir değer belirterek "görünü" belirleyebilirsiniz <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> .  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial> modelin, fırçayı fırçanın rengine eşit yaymış olmasına rağmen uygulanacağını belirtmenize olanak tanır. Bu, modeli hafif yapmaz; Ancak, Diffusemalzemesi veya Specularmalzemeyle dokulu olmasaydı, gölgelendirmeye göre farklı şekilde katılır.  
  
 Daha iyi performans için <xref:System.Windows.Media.Media3D.GeometryModel3D> (bu yüzlerden biri, kameradan modelin karşıt tarafında olduklarından, görüntüleme dışı olan yüzler) sahneye yol açmıştır.  Bir modelin bir <xref:System.Windows.Media.Media3D.Material> düzlem gibi arka yüzlerine uygulanmasını belirtmek için modelin <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliğini ayarlayın.  
  
 Işıyan veya yansıtıcı efektler gibi bazı yüzey kalitelerine ulaşmak için, bir modele art arda birçok farklı fırça uygulamak isteyebilirsiniz. Sınıfını kullanarak birden çok malzemeyi uygulayabilir ve yeniden kullanabilirsiniz <xref:System.Windows.Media.Media3D.MaterialGroup> . MaterialGroup 'un alt öğeleri önce birden çok işleme geçişinde en son öğesine uygulanır.  
  
 Aşağıdaki kod örnekleri, bir düz rengin ve bir çizimin 3B modellere nasıl fırçalar olarak uygulanacağını gösterir.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]  
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Sahneyi aydınlatma  
 3B grafiklerde ışıklar gerçek dünyada hangi ışıklarının olduğunu yapar: yüzeyleri görünür hale getirir. Daha fazla nokta, ışıklar bir sahnenin projeksiyonunun ne kadar dahil edileceğini belirlemektir. İçindeki hafif nesneler, çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] açık ve gölge etkileri oluşturur ve çeşitli gerçek dünya ışıklarının davranışından sonra modellenir. Sahneye en az bir ışık ekleyin veya hiçbir model görünür olmayacaktır.  
  
 Aşağıdaki ışıklar taban sınıftan türetilir <xref:System.Windows.Media.Media3D.Light> :  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Tüm nesneleri, konumlarına veya yönüne bakılmaksızın tek bir şekilde aydınlatmaya yönelik çevresel aydınlatma sağlar.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Uzak bir ışık kaynağı gibi aydınlatma.  Yönlü ışıklar <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> Vector3D olarak belirtilir, ancak belirtilen konum değildir.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Yakın bir ışık kaynağı gibi aydınlatma. Pointlambaları o konumdan bir konum ve cast ışığı vardır. Sahnedeki nesneler, ışığa göre konumlarına ve uzaklığına bağlı olarak aydınlatılır. <xref:System.Windows.Media.Media3D.PointLightBase> bir <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> özellik sunar. Bu, hangi modellerin ışığın ışık tarafından ışıklandırılmayacak bir mesafeyi belirler. PointLight Ayrıca, ışığın şiddette mesafenin ne kadar azalduğunu belirleyen düzeltici özellikler de sunar. Işığın zayıflatımına yönelik sabit, doğrusal veya karesel ara değer enterpolasyonlarını belirtebilirsiniz.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Öğesinden devralır <xref:System.Windows.Media.Media3D.PointLight> . Spotışıkları PointLight gibi aydınlatmış ve hem konum hem de yönlere sahiptir. Bunlar <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> , ve özellikleri tarafından ayarlanan <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> , derece cinsinden belirlenen bir koni şeklinde bir alanda.  
  
 Işıklar <xref:System.Windows.Media.Media3D.Model3D> nesneler olduğundan, konum, renk, yön ve Aralık dahil olmak üzere hafif özellikleri dönüştürebilir ve hareketlendirebilirsiniz.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Modelleri dönüştürme  
 Modeller oluşturduğunuzda, sahnede belirli bir konum vardır. Bu modelleri sahne içinde hareket ettirmek, döndürmek veya boyutunu değiştirmek için modelleri tanımlayan köşeleri değiştirmek pratik değildir.  Bunun yerine, 2B ' de olduğu gibi modellere dönüşümler uygularsınız.  
  
 Her model nesnesi, <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> modeli taşıyabileceğiniz, yeniden yönlendirebileceğiniz veya yeniden boyutlandırabileceğiniz bir özelliğine sahiptir.  Bir dönüşüm uyguladığınızda, dönüşüm tarafından belirtilen vektör ya da değere göre modelin tüm noktalarını etkin bir şekilde fark edersiniz. Diğer bir deyişle, modelin tanımlandığı koordinat alanını ("model alanı") dönüştürürsünüz, ancak tüm sahnenin koordinat sisteminde modelin geometrisini oluşturan değerleri ("Dünya alanı") değiştirmezsiniz.  
  
 Modelleri dönüştürme hakkında daha fazla bilgi için bkz. [3D Dönüştürmelere genel bakış](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Modellerdeki hareketlendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3B uygulama, 2B grafiklerle aynı zamanlama ve animasyon sistemine katılır. Diğer bir deyişle, 3B sahneye animasyon uygulamak için modellerinin özelliklerine animasyon ekleyin. Temel elemanların özelliklerine doğrudan animasyon eklemek mümkündür, ancak modellerin konumunu veya görünümünü değiştiren dönüştürmelerin animasyonunu genellikle daha kolay hale gelir. Dönüşümler <xref:System.Windows.Media.Media3D.Model3DGroup> nesnelere ve ayrı modellere uygulanabileceğinden, bir animasyon kümesinin bir Model3DGroup alt öğesine ve başka bir animasyon kümesinin bir alt nesne grubuna uygulanması mümkündür. Ayrıca sahnenin ışıkınızın özelliklerini canlandırarak çeşitli görsel etkiler elde edebilirsiniz. Son olarak, kameranın konumunu veya Görünüm alanını canlandırarak projeksiyonun animasyonunu yapabilirsiniz. Zamanlama ve animasyon sistemiyle ilgili arka plan bilgileri için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [animasyon genel](animation-overview.md)bakış, görsel taslaklara [genel](storyboards-overview.md)bakış ve [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md) konularına bakın.  
  
 İçindeki bir nesneye animasyon uygulamak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir zaman çizelgesi oluşturur, bir animasyon (zaman içinde bazı özellik değerindeki bir değişiklik) tanımlayın ve animasyonun uygulanacağı özelliği belirtin. Bir 3B sahnedeki tüm nesneler alt öğesi olduğundan <xref:System.Windows.Controls.Viewport3D> , sahneye uygulamak istediğiniz herhangi bir animasyonun hedeflediği Özellikler Viewport3D ' in özellikleridir.  
  
 Bir modelin bir yerde wobble 'da görünmesini istediğinizi varsayalım. <xref:System.Windows.Media.Media3D.RotateTransform3D>Modele bir tane uygulamayı ve döndürme eksenini bir vektörden diğerine hareketlendirmek tercih edebilirsiniz. Aşağıdaki kod örneği, Vector3DAnimation 'in bir TransformGroup ile modele uygulanan birkaç dönüşümden biri olduğunu varsayarak, dönüşümün Rotation3D 'ın Axis özelliğine bir uygulamayı gösterir.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>Pencereye 3B Içerik ekleme  
 Sahneyi işlemek için bir öğesine modeller ve ışıklar ekleyin ve <xref:System.Windows.Media.Media3D.Model3DGroup> sonra ' ı ' <xref:System.Windows.Media.Media3D.Model3DGroup> a ayarlayın <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> <xref:System.Windows.Media.Media3D.ModelVisual3D> . <xref:System.Windows.Media.Media3D.ModelVisual3D>Koleksiyonunu öğesine ekleyin <xref:System.Windows.Controls.Viewport3D.Children%2A> <xref:System.Windows.Controls.Viewport3D> . Özelliğini ayarlayarak öğesine kameraları ekleyin <xref:System.Windows.Controls.Viewport3D> <xref:System.Windows.Controls.Viewport3D.Camera%2A> .  
  
 Son olarak, penceresine öğesini ekleyin <xref:System.Windows.Controls.Viewport3D> . <xref:System.Windows.Controls.Viewport3D>Tuval gibi bir düzen öğesinin içeriği olarak dahil edildiğinde, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerini ayarlayarak (öğesinden devralınmış) Viewport3D boyutunu belirtin <xref:System.Windows.FrameworkElement> .  
  
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
