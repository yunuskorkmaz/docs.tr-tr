---
title: "WPF İçinde URI'leri Paketleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05e13b8fc899b5cc6addb6d41db826f39b7528f0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="pack-uris-in-wpf"></a>WPF İçinde URI'leri Paketleme
İçinde [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] belirlemek ve aşağıdakiler dahil pek çok yolla dosyaları yüklemek için kullanılır:  
  
-   Belirtme [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] göstermek için bir uygulamayı ilk kez başlatıldığında.  
  
-   Görüntüleri yükleniyor.  
  
-   Sayfalara gezinme.  
  
-   Yürütülebilir olmayan veri dosyaları yükleniyor.  
  
 Ayrıca, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] belirlemek ve konumları, aşağıdakiler dahil çeşitli arasından dosyaları yüklemek için kullanılabilir:  
  
-   Geçerli derleme.  
  
-   Başvurulan bir derleme.  
  
-   Bir derleme göreli bir konum.  
  
-   Kaynak site uygulama.  
  
 Tutarlı bir mekanizma tanımlayan ve bu konumlardan bu tür dosyaları yükleme sağlamak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletilmesinde yararlanır *paketi URI düzeni*. Bu konuda düzenine genel bakış sağlar, paketi oluşturmak alınmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] çeşitli senaryolar için mutlak veya göreli anlatılmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketini kullanmak nasıl gösteren önce çözümleme [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] hem biçimlendirmeden ve kod.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>URI şeması paketleme  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması tarafından kullanılıyor [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) düzenleme ve içerik tanımlayan bir model açıklar (OPC) belirtimi. Bu model önemli öğelerin paketleri ve bölümleri olan burada bir *paket* bir mantıksal bir veya daha fazla mantıksal bir kapsayıcısıdır *bölümleri*. Aşağıdaki şekil bu kavramı gösterir.  
  
 ![Paket ve bölümleri diyagramı](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 Bölümleri tanımlamak için RFC 2396 genişletilebilirlik OPC belirtimi yararlanır (Tekdüzen Kaynak Tanımlayıcıları (URI): genel sözdizimi) paketi tanımlamak için [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] düzeni.  
  
 Tarafından belirtilen düzeni bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kendi önekiyle; tanımlanan http, ftp ve dosya bilinen örnekler verilmiştir. Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şema "paketi" kendi şemasını kullanır ve iki bileşenleri içerir: yetkilisi ve yolu. Bir paketi biçimi aşağıdaki şekildedir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 paketi: / /*yetkilisi*/*yolu*
  
 *Yetkilisi* bir bölümü, içerdiği paket türünü belirtir. sırada *yolu* bir bölümü bir paket içinde konumunu belirtir.  
  
 Bu kavram aşağıdaki şekilde gösterilmiştir:  
  
 ![Paket, yetkili ve yol arasındaki ilişkiyi](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 Paketler ve bölümleri uygulamaları ve dosyaları, bir uygulama (paketi) dahil olmak üzere bir veya daha fazla dosyaları (parça), burada içerebilir benzer:  
  
-   Yerel bütünleştirilmiş koda derlenmiş kaynak dosyaları.  
  
-   Başvurulan bütünleştirilmiş koda derlenmiş kaynak dosyaları.  
  
-   Başvuruda bulunan bir bütünleştirilmiş koda derlenmiş kaynak dosyaları.  
  
-   İçerik dosyaları.  
  
-   Kaynak dosyaları sitesi.  
  
 Bu tür dosyaları, erişmek için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iki yetkilileri destekler: uygulama: / / / ve siteoforigin: / / /. Uygulama: / / / yetkilisi içerik ve kaynak dosyaları dahil olmak üzere derleme zamanında bilinen uygulama verileri dosyaları tanımlar. Siteoforigin: / / / yetkilisi kaynak dosyaları sitesi tanımlar. Her yetki kapsamını aşağıdaki çizimde gösterilmiştir.  
  
 ![Paket URI diyagramı](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Bir paketi yetkilisi bileşeninin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] katıştırılmış olan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] noktalarını bir pakete ve RFC 2396 uygun olmalıdır. Ayrıca, "/" karakter "," karakteri ile değiştirilmelidir ve ayrılmış "%" gibi karakterler ve "?" kaçış uygulanmalıdır. OPC Ayrıntılar için bkz.  
  
 Aşağıdaki bölümlerde, paketi oluşturmak açıklanmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak, içerik ve kaynak dosyaları sitesi tanımlamak için bu iki yetkililerine uygun yolları ile birlikte kullanma.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>Kaynak dosya Pack URI  
 Kaynak dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` öğeleri ve derlemelerine derlenir. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Paketi yapımı destekleyen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel bütünleştirilmiş koda derlenmiş ya da yerel derlemesinden başvuruda bulunulan bir bütünleştirilmiş koda derlenmiş kaynak dosyaları belirlemek için kullanılabilir.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Yerel derleme kaynak dosyası  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol için bir kaynak yerel bütünleştirilmiş koda derlenmiş dosyasını kullanır:  
  
-   **Yetkilisi**: uygulama: / / /.  
  
-   **Yol**: yerel derleme projesi klasörü köküne göre yolunu da içeren kaynak dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel derlemenin proje klasörünü kök dizininde bulunan kaynak dosyası.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yerel derlemenin proje klasörünün alt klasöründe bulunan kaynak dosyası.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Başvurulan derleme kaynak dosyası  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol için bir kaynak başvurulan bütünleştirilmiş koda derlenmiş dosyasını kullanır:  
  
-   **Yetkilisi**: uygulama: / / /.  
  
-   **Yol**: başvurulan bütünleştirilmiş koda derlenmiş bir kaynak dosyasının adı. Yol aşağıdaki biçime uygun olmalıdır:  
  
     *AssemblyShortName*{*; Sürüm*] {*; PublicKey*]; bileşen /*yolu*  
  
    -   **AssemblyShortName**: başvurulan derlemeyi için kısa bir ad.  
  
    -   **; Sürüm** [isteğe bağlı]: kaynak dosyası içeren başvurulan bütünleştirilmiş kod sürümü. Bu, iki veya daha fazla başvurulan derlemeleri aynı kısa adı ile yüklü olduğunda kullanılır.  
  
    -   **; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar. Bu, iki veya daha fazla başvurulan derlemeleri aynı kısa adı ile yüklü olduğunda kullanılır.  
  
    -   **; bileşeni**: yerel derlemesinden başvuruda bulunulan derleme başvuruluyor belirtir.  
  
    -   **/ Yol**:, başvurulan derlemenin proje klasörünü kök göreli yolunu da içeren kaynak dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünü kök dizininde bulunan kaynak dosyası.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünün alt klasöründe bulunan kaynak dosyası.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan, sürüme özgü derlemenin proje klasörünü kök klasöründe yer alan kaynak dosyası.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Unutmayın paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurulan derleme kaynak dosyaları için sözdizimi yalnızca uygulamayla birlikte kullanılabilir: / / / yetkilisi. Örneğin, aşağıdaki desteklenmeyen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>İçerik dosyası Pack URI  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir içerik dosyası aşağıdaki yetkilisi ve yolunu kullanır:  
  
-   **Yetkilisi**: uygulama: / / /.  
  
-   **Yol**: dosya sistemi konumu uygulamanın ana yürütülebilir derlemenin göreli yolunu da içeren içerik dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik dosyası, yürütülebilir derleme ile aynı klasörde bulunur.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamanın yürütülebilir derleme göreli bir alt klasöründe bulunan içeriği dosyası.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]İçerik dosyaları için erişilemeyeceğini. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Düzeni yalnızca gezinme destekler [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kaynak sitede bulunan dosyalar.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>Kaynak Paketi URI'ler site  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir kaynak sitesi için dosya aşağıdaki yetkilisi ve yolu kullanır:  
  
-   **Yetkilisi**: siteoforigin: / / /.  
  
-   **Yol**: site içinden yürütülebilir derleme başlatılmış konumu göreli yolunu da içeren kaynak dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site yürütülebilir derleme başlatıldığı konumunda depolanan kaynak dosya.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site uygulamanın yürütülebilir derleme başlatıldığı konumuna göre alt depolanan kaynak dosya.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Sayfa dosyası  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olarak yapılandırılmış dosyalar [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri kaynak dosyaları aynı şekilde derlemelerine derlenir. Sonuç olarak, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri paketi kullanarak belirlenebilir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak dosyaları için.  
  
 Türlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yaygın olarak yapılandırılmış dosyalar [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleriniz kendi kök öğesi olarak şunlardan biri:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Mutlak vs. Göreli Pack URI  
 Tam bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şema, yetkili ve yol içerir ve bir mutlak paketi kabul edilen [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Geliştiriciler, basitleştirme olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri genellikle izin göreli paketiyle uygun özniteliklere ayarlamanızı [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], yalnızca yolunu içerir.  
  
 Örneğin, aşağıdaki mutlak paketi göz önünde bulundurun [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerel derleme kaynak dosyası için.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bu kaynağa başvuruyor dosya, aşağıdaki olacaktır.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Kaynak dosyaları sitesi olmadığından derlemeler ile ilişkilendirilmiş, bunlar yalnızca mutlak paketiyle başvurulabilen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Varsayılan olarak, göreli bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] işaretleme veya başvuru içeren kodu konumuna göre değerlendirilir. Başında bir eğik çizgi kullanılırsa, ancak göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuru sonra uygulama kök göreli olarak kabul. Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Page1.XAML içeriyorsa bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran *kök*\SubFolder\Page2.xaml, başvuru aşağıdaki göreli paketi kullanabilirsiniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Page1.XAML içeriyorsa bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran *kök*\Page2.xaml, başvuru aşağıdaki göreli paketi kullanabilirsiniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Paketi URI çözümleme  
 Paketi biçimi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] paketi mümkündür yapar [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aynı aramak için dosyalarını farklı türde. Örneğin, aşağıdaki mutlak paketi göz önünde bulundurun [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Bu mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerel derlemede bir kaynak dosyası veya içerik dosyasına başvuruyor olabilir. Aynı için aşağıdaki göreli geçerlidir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Belirlemek için, dosya türü, bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurduğu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çözümler [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel derlemeler ve aşağıdaki buluşsal yöntemlerini kullanarak içerik dosyaları kaynak dosyaları:  
  
1.  Derleme meta verilerini araştırma bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> paketi eşleşen öznitelik [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Varsa <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunduğunda, yolun paketinin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] içerik dosyasına başvuruyor.  
  
3.  Varsa <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunamadı, yerel bütünleştirilmiş koda derlenmiş kümesi kaynak dosyalarını araştırma.  
  
4.  Yolun paketinin eşleşen bir kaynak dosya [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bulunursa, yolun paketinin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kaynak dosyasına başvuruyor.  
  
5.  Kaynak bulunmazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]çözümleme için geçerli olmayan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] aşağıdaki bakın:  
  
-   İçerik başvurulan derlemelerin dosyalarında: Bu dosya türlerini tarafından desteklenmeyen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Başvurulan derlemeleri gömülü dosyalar: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , tanımlamak bunları hem başvurulan bütünleştirilmiş kodun adını içerdiğinden benzersizdir ve `;component` soneki.  
  
-   Kaynak dosyaları sitesi: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , tanımlamak bunları paketi tarafından tanımlanan yalnızca dosyaları olduklarından benzersizdir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] siteoforigin içerir: / / / yetkilisi.  
  
 Paketi bir basitleştirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çözümleme sağlar ve içerik kaynak dosyaları konumlarını biraz bağımsız olması için kodu. Örneğin, bir içerik dosyası paketi olacak şekilde yeniden yerel derleme kaynak dosyası varsa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi kullanan kodu yaptığı gibi kaynak aynı kalır [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Pack URI ile programlama  
 Birçok [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sınıfları uygulama paketi ayarlanabilir özellikleri [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]dahil:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Bu özellikler, biçimlendirme ve kodun ayarlanabilir. Bu bölümde her ikisi için de temel kurulumlarını gösterir ve yaygın senaryolar örnekleri gösterilir.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>Biçimlendirme Pack URI kullanma  
 Bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi olan bir öznitelik öğesi ayarlayarak biçimlendirme içinde belirtilen [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Örneğin:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tablo 1 gösterilmektedir çeşitli mutlak paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , biçimlendirme belirtebilirsiniz.  
  
 Tablo 1: Mutlak Pack URI biçimlendirme  
  
|Dosya|Mutlak paketi[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Kaynak dosya - yerel derleme|`"pack://application:,,,/ResourceFile.xaml"`|  
|Alt - yerel derleme kaynak dosyası|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Kaynak dosya - başvurulan derleme|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Alt başvurulan derleme kaynak dosyası|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Sürümü tutulan başvurulan derleme kaynak dosyası|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|İçerik dosyası|`"pack://application:,,,/ContentFile.xaml"`|  
|İçerik dosyası alt|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Kaynak dosya site|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Kaynak dosya alt site|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tablo 2 gösterilmektedir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , biçimlendirme belirtebilirsiniz.  
  
 Tablo 2: Göreli Pack URI biçimlendirme  
  
|Dosya|Göreli paketi[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Yerel derleme kaynak dosyası|`"/ResourceFile.xaml"`|  
|Yerel derleme alt kaynak dosyası|`"/Subfolder/ResourceFile.xaml"`|  
|Başvurulan derleme kaynak dosyası|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Alt başvurulan derleme kaynak dosyası|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|İçerik dosyası|`"/ContentFile.xaml"`|  
|İçerik dosyası alt|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Pack URI kod içinde kullanma  
 Bir paketi belirtmeniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] örneği tarafından kodda <xref:System.Uri> sınıfı ve paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Oluşturucusu parametre olarak. Bu, aşağıdaki örnekte gösterilmiştir.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Varsayılan olarak, <xref:System.Uri> sınıfı, paketi göz önünde bulundurur [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] mutlak olmalıdır. Sonuç olarak, bir özel durum örneği tetiklenir <xref:System.Uri> sınıfı göreli bir paketi ile oluşturulan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Neyse ki, <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> , aşırı <xref:System.Uri> sınıfı oluşturucusu türünde bir parametre kabul eden <xref:System.UriKind> belirtmek izin vermek için bir paket olup olmadığını [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] mutlak veya göreli.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Yalnızca belirtmelisiniz <xref:System.UriKind.Absolute> veya <xref:System.UriKind.Relative> olduğunuzda belirli, sağlanan paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] biri veya diğer. Paketi türünü bilmiyorsanız [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kullanılan, bir kullanıcı bir paketi girdiğinde gibi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çalışma zamanında <xref:System.UriKind.RelativeOrAbsolute> yerine.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tablo 3 gösterilmektedir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kullanarak kod içinde belirtebileceğiniz <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tablo 3: Mutlak Pack URI kodu  
  
|Dosya|Mutlak paketi[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Kaynak dosya - yerel derleme|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Alt - yerel derleme kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Kaynak dosya - başvurulan derleme|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Alt başvurulan derleme kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Sürümü tutulan başvurulan derleme kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|İçerik dosyası|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|İçerik dosyası alt|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Kaynak dosya site|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Kaynak dosya alt site|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tablo 4 gösterilmektedir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kodu kullanarak belirttiğiniz <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tablo 4: Göreli Pack URI kodu  
  
|Dosya|Göreli paketi[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Kaynak dosya - yerel derleme|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Alt - yerel derleme kaynak dosyası|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Kaynak dosya - başvurulan derleme|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Alt - başvurulan derleme kaynak dosyası|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|İçerik dosyası|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|İçerik dosyası alt|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Paketi URI senaryoları  
 Önceki bölümlerde paketi oluşturmak nasıl ele alınan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak, içerik ve kaynak dosyaları sitesi tanımlamak için. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bu kurulumlarını çeşitli şekillerde kullanılır ve aşağıdaki bölümler birkaç genel kullanımları kapsar.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Bir uygulama başlatıldığında göstermek için kullanıcı Arabirimi belirtme  
 <xref:System.Windows.Application.StartupUri%2A>ilk belirtir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ne zaman göstermek için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatıldığında. Bağımsız uygulamalar için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] penceresinde, aşağıdaki örnekte gösterildiği gibi olabilir.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Bağımsız uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ayrıca bir sayfa ilk kullanıcı Arabirimi, aşağıdaki örnekte gösterildiği gibi belirtebilirsiniz.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Uygulama başına bir uygulamadır ve bir sayfa ile belirtilen <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açılır bir <xref:System.Windows.Navigation.NavigationWindow> sayfası barındırabilir. İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], ana bilgisayar tarayıcıda sayfası gösterilir.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Bir sayfaya gezinme  
 Aşağıdaki örnek, bir sayfaya gitmek gösterilmiştir.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Gezinme için çeşitli yollar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Pencereyi simge belirtme  
 Aşağıdaki örnekte bir URI pencerenin simge belirtmek için nasıl kullanılacağını gösterir.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Görüntü, ses ve Video dosyaları yükleniyor  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]uygulamaların her biri algılanabilir ve paketiyle yüklenen medya türleri, çok geniş bir yelpazedeki kullanmasını sağlayan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]aşağıdaki örneklerde gösterildiği gibi.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Medya içeriği ile çalışma hakkında daha fazla bilgi için bkz: [grafik ve çoklu ortam](../../../../docs/framework/wpf/graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Kaynak sitesinden bir kaynak sözlüğü yükleniyor  
 Kaynak sözlüklerindeki (<xref:System.Windows.ResourceDictionary>) uygulama temaları desteklemek için kullanılabilir. Oluşturun ve Temalar yönetmek için bir yol, bir uygulamanın kaynak sitede bulunan kaynak sözlüklerindeki olarak birden çok tema oluşturmaktır. Bu eklenmesi ve güncelleştirilmiş yeniden derlenmesi ve bir uygulama dağıtarak Temalar sağlar. Bu kaynak sözlüklerindeki tanımlanabilir ve paketi kullanılarak yüklenen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], aşağıdaki örnekte gösterilen.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Temalar da genel bir bakış için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama kaynağı, içerik ve veri dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
