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
ms.openlocfilehash: 725a6dc8e4b4a7b474a7dd85c87cdedd93ba09c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186956"
---
# <a name="3-d-graphics-overview"></a>3B Grafiklere Genel Bakış
<a name="introduction"></a>3-B işlevselliği, geliştiricilerin hem biçimlendirme hem de yordam kodunda 3-B grafikler çizmesini, dönüştürmesini ve animasyona dönüştürmesini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar. Geliştiriciler, zengin denetimler oluşturmak, karmaşık veri çizimleri sağlamak veya bir uygulamanın arabiriminin kullanıcı deneyimini geliştirmek için 2-B ve 3-B grafikleri birleştirebilir. 3-D desteği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tam özellikli bir oyun geliştirme platformu sağlamak için tasarlanmaz. Bu konu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik sisteminde3-B işlevselliği genel bir bakış sağlar.  

<a name="threed_in_2d"></a>
## <a name="3-d-in-a-2-d-container"></a>2-B Konteynerde 3-B  
 3-B grafik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği iki boyutlu eleman <xref:System.Windows.Controls.Viewport3D>yapısına katılabilen bir eleman içinde kapsüllenir. Grafik sistemi diğerleri <xref:System.Windows.Controls.Viewport3D> gibi iki boyutlu bir görsel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]unsur olarak davranır. <xref:System.Windows.Controls.Viewport3D>üç boyutlu bir sahneye açılan bir pencere-bir görünüm noktası olarak işlev görür. Daha doğrusu, 3-B sahnenin yansıtıldığı bir yüzeydir.  
  
 Geleneksel bir 2-B uygulamada, Grid veya Canvas gibi başka bir kapsayıcı öğesi gibi kullanın. <xref:System.Windows.Controls.Viewport3D>  Aynı sahne <xref:System.Windows.Controls.Viewport3D> grafiğindeki diğer 2-B çizim nesneleri ile birlikte kullanabiliyor olsanız da, 2-B <xref:System.Windows.Controls.Viewport3D>ve 3-B nesneleri içinde bir .  Bu konu içinde 3-D grafik çizmek <xref:System.Windows.Controls.Viewport3D>için nasıl üzerinde durulacak.  
  
<a name="coord_space"></a>
## <a name="3-d-coordinate-space"></a>3-B Koordinat Alanı  
 2-B grafikleriçin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koordinat sistemi, oluşturma alanının sol üst kısmındaki kaynağı (genellikle ekran) bulur. 2-B sisteminde pozitif x ekseni değerleri sağa, pozitif y ekseni değerleri aşağı doğru ilerler.  Ancak 3-B koordinat sisteminde, menşe, pozitif x ekseni değerlerinin sağa doğru ilerlerken, pozitif y ekseni değerlerinin yukarı doğru ilerlerken, pozitif z ekseni değerlerinin ise oriktan dışa doğru ilerleyerek işleme alanının merkezinde yer alır. , izleyiciye doğru.  
  
 ![Koordinat sistemleri](./media/coordsystem-1.png "CoordSystem-1")  
Konvansiyonel 2-B ve 3-B koordinat sistemi gösterimleri  
  
 Bu eksenler tarafından tanımlanan alan, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3-B nesneler için 'deki sabit başvuru çerçevesidir. Bu alanda modeller oluştururken ve bunları görüntülemek için ışıklar ve kameralar oluştururken, dönüşümleri uyguladığınızda her model için oluşturduğunuz yerel referans çerçevesinden bu sabit referans çerçevesini veya "dünya alanı"nı ayırt etmek yararlıdır. Ayrıca, dünya uzayında nesnelerin ışık ve kamera ayarlarına bağlı olarak tamamen farklı görünebileceğini veya hiç görünmeyebileceğini, ancak kameranın konumunun nesnelerin dünya uzasındaki konumunu değiştirmediğini unutmayın.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Kameralar ve Projeksiyonlar  
 2-B'de çalışan geliştiriciler, iki boyutlu bir ekranda ilkel çizimleri konumlandırmaya alışkındır. Bir 3-B sahne oluşturduğunuzda, gerçekten 3-B nesnelerin 2-B gösterimi oluşturduğunuzu unutmamak önemlidir. Bir 3-B sahne, görüntüleyenin bakış açısına bağlı olarak farklı göründüğünden, bu bakış açısını belirtmeniz gerekir. Sınıf, <xref:System.Windows.Media.Media3D.Camera> 3 B sahne için bu bakış açısını belirtmenizi sağlar.  
  
 3-B sahnenin 2-B yüzeyde nasıl temsil edildiğini anlamanın bir başka yolu da, sahneyi görüntüleme yüzeyine bir projeksiyon olarak tanımlamaktır. Bu, <xref:System.Windows.Media.Media3D.ProjectionCamera> izleyicilerin 3-B modelleri nasıl gördüğünü değiştirmek için farklı projeksiyonları ve özelliklerini belirtmenizi sağlar. Bir <xref:System.Windows.Media.Media3D.PerspectiveCamera> sahne foreshortens bir projeksiyon belirtir.  Başka bir deyişle, ufuk noktası <xref:System.Windows.Media.Media3D.PerspectiveCamera> perspektifi sağlar.  Kameranın sahnenin koordinat alanındaki konumunu, kameranın yönünü ve görüş alanını ve sahnedeki "yukarı" yönünü tanımlayan bir vektörü belirtebilirsiniz. Aşağıdaki diyagram 'projeksiyon <xref:System.Windows.Media.Media3D.PerspectiveCamera>göstermektedir.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Kameranın <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera> projeksiyon aralığını ve özellikleri sınırdır. Kameralar sahnenin herhangi bir yerinde bulunabildiği için, kameranın aslında bir modelin içine veya bir modelin çok yakınına yerlebir olması mümkündür, bu da nesneleri düzgün bir şekilde ayırt etmeyi zorlar.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>nesnelerin çizilmeyeceğinin ötesinde kameradan en az bir mesafe belirlemenizi sağlar.  Tersine, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> kameradan nesnelerin çizilmeyeceği bir mesafe belirtmenizi sağlar, bu da nesnelerin fark edilemeyecek kadar uzakta olmasını sağlar.  
  
 ![Kamera kurulumu](./media/coordsystem-6.png "CoordSystem-6")  
Kamera konumu  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>2-B görsel yüzeye 3-B modelin ortogonal projeksiyon belirtir. Diğer kameralar gibi, bir konum, görüntüleme yönü ve "yukarı" yönü belirtir. Aksine, <xref:System.Windows.Media.Media3D.PerspectiveCamera>ancak, <xref:System.Windows.Media.Media3D.OrthographicCamera> perspektif foreshortening içermeyen bir projeksiyon açıklar. Başka bir <xref:System.Windows.Media.Media3D.OrthographicCamera> deyişle, kenarları kameranın bir noktasında buluşan bir kutu yerine kenarları paralel olan bir görüntüleme kutusunu tanımlar. Aşağıdaki resimde, görüntülenen <xref:System.Windows.Media.Media3D.PerspectiveCamera> model ve <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Ortografik ve perspektif projeksiyonu](./media/camera-projections4.png "Camera_projections4")  
Perspektif ve Ortografik Projeksiyonlar  
  
 Aşağıdaki kod, bazı tipik kamera ayarlarını gösterir.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Model ve Örgü İlkeller  
  
 <xref:System.Windows.Media.Media3D.Model3D>genel bir 3-B nesneyi temsil eden soyut taban sınıfıdır. 3-B sahne oluşturmak için, görüntülemek için bazı nesneler gerekir ve sahne grafiği oluşturan <xref:System.Windows.Media.Media3D.Model3D>nesneler. Şu anda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] destekler geometrileri modelleme <xref:System.Windows.Media.Media3D.GeometryModel3D>. Bu <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> modelin özelliği bir örgü ilkel alır.  
  
 Bir model oluşturmak için, ilkel veya örgü oluşturarak başlayın. 3-B ilkel, tek bir 3-B varlığı oluşturan vertices topluluğudur. Çoğu 3-B sistemler, en basit kapalı şekil üzerinde modellenmiş ilkel sistemler sağlar: üç tepe ile tanımlanan bir üçgen.  Bir üçgenin üç noktası koplanar olduğundan, daha karmaşık şekilleri modellemek için üçgen eklemeye devam edebilirsiniz, meshes denir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3-B sistemi şu <xref:System.Windows.Media.Media3D.MeshGeometry3D> anda herhangi bir geometri belirtmenizi sağlayan sınıf sağlar; şu anda küreler ve kübik formlar gibi önceden tanımlanmış 3-B ilkel leri desteklememektedir. Özelliği olarak <xref:System.Windows.Media.Media3D.MeshGeometry3D> üçgen vertices listesini belirterek bir oluşturmaya başlayın. <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> Her tepe noktası bir <xref:System.Windows.Media.Media3D.Point3D>. olarak belirtilir  (Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]özelliği, her tepe noktasının koordinatlarını temsil eden üçler halinde gruplanmış sayıların listesi olarak belirtin.) Geometrisine bağlı olarak, örgünüz, bazıları aynı köşeleri (köşeleri) paylaşan birçok üçgenden oluşabilir. Kafesi doğru çizmek için, hangi tepelerin hangi üçgenler tarafından paylaşıldığı hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bilgi gerekir. Bu bilgileri, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> özellik ile üçgen endeksleri listesini belirterek sağlarsınız. Bu liste, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listede belirtilen noktaların bir üçgen belirleyeceği sırayı belirtir.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Önceki örnekte, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste küp şeklinde bir örgü tanımlamak için sekiz vertices belirtir. Özellik, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> üç endeksten oluşan on iki grubun bir listesini belirtir.  Listedeki her numara, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listeye bir mahsup anlamına gelir.  Örneğin, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste tarafından belirtilen ilk üç vertices (1,1,0), (0,1,0) ve (0,0,0) vardır. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Listede belirtilen ilk üç endeks, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listedeki birinci, üçüncü ve ikinci noktalara karşılık gelen 0, 2 ve 1'dir. Sonuç olarak, küp modelini oluşturan ilk üçgen (1,1,0) ile (0,1,0) ile (0,0,0) arasında oluşacak ve kalan on bir üçgen de benzer şekilde belirlenecektir.  
  
 Özellikleri ve <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> değerleri belirterek modeli tanımlamaya <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> devam edebilirsiniz.  Modelin yüzeyini işlemek için grafik sisteminin herhangi bir üçgende yüzeyin hangi yöne baktığı hakkında bilgi gerekir. Bu bilgileri, model için aydınlatma hesaplamaları yapmak için kullanır: doğrudan bir ışık kaynağına bakan yüzeyler ışıktan uzağa açılı yüzeylerden daha parlak görünür. Konum [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koordinatlarını kullanarak varsayılan normal vektörleri belirleyebilse de, eğri yüzeylerin görünümünü yaklaşık olarak belirlemek için farklı normal vektörler de belirtebilirsiniz.  
  
 Özellik, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> grafik sistemine bir <xref:System.Windows.Point>dokunun kafesin tepelerine nasıl çizildiğini belirleyen koordinatların nasıl eşlendiğini anlatan bir s koleksiyonunu belirtir. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>dahil, sıfır ve 1 arasında bir değer olarak belirtilir.  <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> Özellikte olduğu gibi, grafik sistemi varsayılan doku koordinatlarını hesaplayabilir, ancak örneğin yinelenen desenin bir parçasını içeren bir dokunun eşlemeyi denetlemek için farklı doku koordinatları ayarlamayı seçebilirsiniz. Doku koordinatları hakkında daha fazla bilgiyi sonraki konularda veya Yönetilen Direct3D SDK'da bulabilirsiniz.  
  
 Aşağıdaki örnek, yordam kodunda küp modelinin bir yüzünün nasıl oluşturuleceğini gösterir. Tüm küpü tek bir GeometryModel3D olarak çizebileceğinizi unutmayın; Bu örnek, daha sonra her yüze ayrı dokular uygulamak için küpün yüzünü farklı bir model olarak çizer.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>
## <a name="applying-materials-to-the-model"></a>Modele Malzeme Uygulama  
  
 Bir kafesin üç boyutlu bir nesne gibi görünmesi için, ön ve üçgenleri tarafından tanımlanan yüzeyi kapsayacak şekilde uygulamalı bir dokuya sahip olması gerekir, böylece kamera tarafından aydınlatılabilir ve yansıtılabilir. 2-B'de, sınıfı <xref:System.Windows.Media.Brush> ekran alanlarına renk, desen, degrade veya diğer görsel içerik uygulamak için kullanırsınız.  Ancak, 3-B nesnelerin görünümü, aydınlatma modelinin bir fonksiyonudur, sadece renk veya desen onlara uygulanan. Gerçek dünya nesneleri, yüzeylerinin kalitesine bağlı olarak ışığı farklı yansıtır: parlak ve parlak yüzeyler pürüzlü veya mat yüzeylerle aynı görünmüyor ve bazı nesneler ışığı emerken diğerleri parlıyor gibi görünüyor. Aynı fırçaların tümlerini 2B nesnelere uygulayabileceğiniz 3-B nesnelere uygulayabilirsiniz, ancak doğrudan uygulayamazsınız.  
  
 Bir modelin yüzeyinin özelliklerini tanımlamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için <xref:System.Windows.Media.Media3D.Material> soyut sınıfı kullanır. Malzemenin beton alt sınıfları modelin yüzeyinin bazı görünüm özelliklerini belirler ve her biri solidcolorbrush, TileBrush veya VisualBrush geçirebileceğiniz bir Fırça özelliği de sağlar.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>fırçanın modele, bu model yaygın bir şekilde yanmış gibi uygulanacağını belirtir. DiffuseMaterial'ı kullanmak en çok 2-B modellerde doğrudan fırça kullanmak gibidir; model yüzeyleri ışığı parlak gibi yansıtmaz.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>fırçanın modele, modelin yüzeyi sert veya parlak, vurguları yansıtabilecek şekilde uygulanacağını belirtir. Özellik için <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> bir değer belirterek, dokunun bu yansıtıcı kaliteyi veya "parlaklık"ı önerme derecesini ayarlayabilirsiniz.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>doku modeli fırçanın rengine eşit ışık yayan sanki uygulanacak belirtmenizi sağlar. Bu modeli bir ışık yapmaz; ancak, diffuseMaterial veya SpecularMaterial ile dokulu ise daha gölgeleme farklı katılacak.  
  
 Daha iyi performans için, <xref:System.Windows.Media.Media3D.GeometryModel3D> bir arka yüzler (kameradan modelin karşı tarafında oldukları için görüntülenmemiş olan yüzler) sahneden itlaf edilir.  Düzlem gibi <xref:System.Windows.Media.Media3D.Material> bir modelin arka yüzüne uygulanacak bir model belirtmek <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> için modelin özelliğini ayarlayın.  
  
 Parlayan veya yansıtıcı efektler gibi bazı yüzey niteliklerielde etmek için, bir modele art arda birkaç farklı fırça uygulamak isteyebilirsiniz. <xref:System.Windows.Media.Media3D.MaterialGroup> Sınıfı kullanarak birden fazla Materyal uygulayabilir ve yeniden kullanabilirsiniz. MaterialGroup'un alt ları, birden çok işleme geçişinde ilk olarak last'e uygulanır.  
  
 Aşağıdaki kod örnekleri, düz bir rengin ve çizimin 3-B modellere fırça olarak nasıl uygulanacağı gösterilmektedir.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Sahneyi Aydınlatma  
 3-B grafikteki ışıklar, ışıkların gerçek dünyada yaptığı şeyi yapar: yüzeyleri görünür hale getirin. Daha da önemlisi, ışıklar bir sahnenin hangi bölümünün projeksiyona dahil olacağını belirler. Işık nesneleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ışık ve gölge efektleri çeşitli oluşturmak ve çeşitli gerçek dünya ışıkları davranışı sonra modellenmiştir. Sahnenize en az bir ışık eklemeniz gerekir, yoksa hiçbir model görünmez.  
  
 Aşağıdaki ışıklar taban sınıftan <xref:System.Windows.Media.Media3D.Light>türetilmiştir:  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Konumları veya yönlendirmeleri ne olursa olsun tüm nesneleri eşit olarak aydınlatan ortam aydınlatması sağlar.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Uzak bir ışık kaynağı gibi yanar.  Yön ışıkları Vector3D olarak belirtilir, ancak belirli bir <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> konum yoktur.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Yakındaki bir ışık kaynağı gibi yanar. PointLights bir konuma sahip ve bu konumdan ışık döküm. Sahnedeki nesneler ışığa göre konumlarına ve uzaklıklarına bağlı olarak aydınlatılır. <xref:System.Windows.Media.Media3D.PointLightBase>modellerin ışıkla aydınlatılmayacağı mesafeyi belirleyen bir <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> özelliği ortaya çıkarır. PointLight ayrıca ışığın yoğunluğunun mesafe boyunca nasıl azaldığını belirleyen zayıflama özelliklerini de ortaya çıkarır. Işığın zayıflaması için sabit, doğrusal veya kuadratik enterpolasyonlar belirtebilirsiniz.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Miras <xref:System.Windows.Media.Media3D.PointLight>alır . Spot ışıkları PointLight gibi yanar ve hem konuma hem de yöne sahiptir. Işığı, <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> derece cinsinden belirlenen koni şeklindebir alanda ve <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> özelliklerde yansıtabilirler.  
  
 Işıklar <xref:System.Windows.Media.Media3D.Model3D> nesnelerdir, böylece konum, renk, yön ve aralık gibi ışık özelliklerini dönüştürebilir ve canlandırabilirsiniz.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Modelleri Dönüştürme  
 Modelleri oluşturduğunuzda, sahnede belirli bir konuma sahiptirler. Bu modelleri sahnede hareket ettirebilmek, döndürmek veya boyutlarını değiştirmek için modelleri tanımlayan tepe bilgilerini değiştirmek pratik değildir.  Bunun yerine, tıpkı 2-B'de olduğu gibi, dönüşümleri modellere uygularsınız.  
  
 Her model nesnesinin, modeli taşıyabileceğiniz, yeniden yönlendirebileceğiniz veya yeniden boyutlandırabileceğiniz bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği vardır.  Bir dönüştürme uyguladığınız zaman, dönüşümün belirlediği vektör veya değere göre modelin tüm noktalarını etkili bir şekilde dengelersiniz. Başka bir deyişle, modelin tanımlandığı koordinat alanını ("model uzayı") dönüştürdüniz, ancak modelin geometrisini oluşturan değerleri tüm sahnenin koordinat sisteminde ("dünya uzayı") değiştirmedin.  
  
 Modelleri dönüştürme hakkında daha fazla bilgi için [3-B Dönüşümlere Genel Bakış'a](3-d-transformations-overview.md)bakın.  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animating Modelleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3-B uygulaması, 2-B grafikile aynı zamanlama ve animasyon sistemine katılır. Başka bir deyişle, 3-B sahneyi canlandırmak için, modellerinin özelliklerini canlandırın. İlkel lerin özelliklerini doğrudan canlandırmak mümkündür, ancak modellerin konumunu veya görünümünü değiştiren dönüşümleri canlandırmak genellikle daha kolaydır. Dönüşümler nesnelerin yanı <xref:System.Windows.Media.Media3D.Model3DGroup> sıra tek tek modellere de uygulanabildiği için, bir Model3DGroup'un çocuğuna bir animasyon kümesi ve bir grup alt nesneiçin başka bir animasyon kümesi uygulamak mümkündür. Ayrıca, sahnenizin Aydınlatma özelliklerini canlandırarak çeşitli görsel efektler elde edebilirsiniz. Son olarak, kamera konumunu veya görüş alanını canlandırarak projeksiyonu animasyona sunmayı seçebilirsiniz. Zamanlama ve animasyon sistemi hakkında arka plan bilgileri için [Animasyona Genel Bakış,](animation-overview.md) [Storyboards Genel Bakış](storyboards-overview.md)ve [Serbest Nesnelere Genel Bakış](../advanced/freezable-objects-overview.md) konularına bakın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 Bir nesneyi canlandırmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]için bir zaman çizelgesi oluşturursunuz, bir animasyon tanımlarsınız (ki bu gerçekten zaman içinde bazı özellik değerinde bir değişikliktir) ve animasyonun uygulanacağı özelliği belirtin. 3-B sahnedeki tüm nesneler çocuklar <xref:System.Windows.Controls.Viewport3D>olduğundan, sahneye uygulamak istediğiniz herhangi bir animasyontarafından hedeflenen özellikler Viewport3D özellikleridir.  
  
 Bir modelin yerinde sallanıyormuş gibi görünmesini istediğinizi varsayalım. Modele bir <xref:System.Windows.Media.Media3D.RotateTransform3D> uygulama ve bir vektörden diğerine döndürme eksenini animasyona savurabilirsiniz. Aşağıdaki kod örneği, TransformGroup ile modele uygulanan birkaç dönüşümden biri olarak RotateTransform3D'nin varsayarak, dönüşümün Rotation3D'sinin Eksen özelliğine bir Vector3DAnimation uygulandığını gösterir.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3-d-content-to-the-window"></a>Pencereye 3-B İçerik Ekleme  
 Sahneyi işlemek için, modelleri ve <xref:System.Windows.Media.Media3D.Model3DGroup>ışıkları eklemek <xref:System.Windows.Media.Media3D.Model3DGroup> bir <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> , <xref:System.Windows.Media.Media3D.ModelVisual3D>sonra bir olarak ayarlayın . <xref:System.Windows.Media.Media3D.ModelVisual3D> <xref:System.Windows.Controls.Viewport3D>Toplama <xref:System.Windows.Controls.Viewport3D.Children%2A> ekle. <xref:System.Windows.Controls.Viewport3D.Camera%2A> Özelliğini <xref:System.Windows.Controls.Viewport3D> ayarlayarak kameralar ekleyin.  
  
 Son olarak, <xref:System.Windows.Controls.Viewport3D> pencereye ekleyin. Canvas <xref:System.Windows.Controls.Viewport3D> gibi bir düzen öğesinin içeriği ne zaman dahil edildiğinde, viewport3D <xref:System.Windows.FrameworkElement.Height%2A> boyutunu <xref:System.Windows.FrameworkElement.Width%2A> ve özelliklerini <xref:System.Windows.FrameworkElement>(devralınan) ayarlayarak belirtin.  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [3B Dönüşümlere Genel Bakış](3-d-transformations-overview.md)
- [WPF 3B Performansını En Üst Düzeye Çıkarma](maximize-wpf-3d-performance.md)
- [Nasıl Dır Konular](3-d-graphics-how-to-topics.md)
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
