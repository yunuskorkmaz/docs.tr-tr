---
title: WPF İçinde URI'leri Paketleme
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 9e7ded2869e3553eab302e150d80608b8dd7091f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377326"
---
# <a name="pack-uris-in-wpf"></a>WPF İçinde URI'leri Paketleme
Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] belirlemek ve aşağıdakiler dahil pek çok yolla dosyalarını yüklemek için kullanılır:  
  
-   Belirtme [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] göstermek için bir uygulama ilk kez başlatıldığında.  
  
-   Görüntüleri yükleniyor.  
  
-   Sayfa Gezinme.  
  
-   Yürütülebilir olmayan veri dosyaları yükleniyor.  
  
 Ayrıca, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] belirlemek ve konumları, aşağıdakiler dahil çeşitli arasından dosyaları yüklemek için kullanılabilir:  
  
-   Geçerli derleme.  
  
-   Başvurulan bir derleme.  
  
-   Bir derlemeye göreli bir konum.  
  
-   Kaynak siteyi uygulamanın.  
  
 Belirlemekten ve bu konumlardan bu tür dosyaları yüklenirken tutarlı bir mekanizma sağlamanız [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] genişletilmesinde yararlanır *URI şeması paketleme*. Bu konuda düzenine genel bir bakış sağlar, paketi oluşturmak için nasıl ele alınmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] mutlak veya göreli bir çeşitli senaryoları ele alınmaktadır [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ve [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Paketi'ni kullanma göstermeden önce çözüm, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] hem biçimlendirmeden ve kod.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>URI şeması paketleme  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması tarafından kullanılan [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) belirtimi, düzenleme ve içeriği tanımlamak için bir modeli açıklanmaktadır. Bu model önemli öğelerin paketleri ve bölümleri olan burada bir *paket* bir mantıksal bir veya daha fazla mantıksal bir kapsayıcısıdır *bölümleri*. Aşağıdaki şekil bu kavramı gösterir.  
  
 ![Paket ve bölümleri diyagramı](./media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 Bölümleri tanımlamak için genişletilebilirliği, RFC 2396 OPC belirtimi yararlanır (Tekdüzen Kaynak Tanımlayıcıları (URI): Paketi tanımlamak için genel sözdizimi) [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] düzeni.  
  
 Tarafından belirtilen düzeni bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ; kendi ön eke göre tanımlanan http, ftp ve dosya tanınmış örnekler verilmiştir. Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şema "paketi", şema olarak kullanır ve iki bileşenleri içerir: yetkilisi ve yolu. Aşağıdaki bir paketi biçimi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 paketi: / /*yetkilisi*/*yolu*
  
 *Yetkilisi* bir bölümü tarafından bulunan bir paket türünü belirtir ancak *yolu* bir bölümü bir paket içindeki konumunu belirtir.  
  
 Bu kavram aşağıdaki şekilde gösterilmiştir:  
  
 ![Paket, yetkili ve yolu arasındaki ilişkiyi](./media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 Paketler ve bölümleri, uygulamalar ve dosyalar burada bir uygulaması (paket) dahil olmak üzere bir veya daha fazla dosyaları (parça) içerebilir, benzer:  
  
-   Yerel bütünleştirilmiş kod içine derlenmiş kaynak dosyaları.  
  
-   Başvurulan bir bütünleştirilmiş kod içine derlenmiş kaynak dosyaları.  
  
-   Bir başvuru bütünleştirilmiş kod içine derlenmiş kaynak dosyaları.  
  
-   İçerik dosyaları.  
  
-   Kaynak dosyaları sitesi.  
  
 Bu tür dosyaları, erişmeye [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] iki yetkilileri destekler: uygulama: / / / ve siteoforigin: / / /. Uygulama: / / / yetkilisi kaynak ve içerik dosyaları dahil olmak üzere derleme zamanında bilinen uygulama veri dosyalarını tanımlar. Siteoforigin: / / / yetkilisi kaynak dosyaları sitesi tanımlar. Her yetki kapsamını aşağıdaki şekilde gösterilmiştir.  
  
 ![Pack URI'si diyagram](./media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Bir paketi yetkili bileşeni [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir Embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir pakete işaret ve RFC 2396 uymalıdır. Ayrıca, "/" karakteri "," karakteri ile değiştirilmelidir ve ayrılmış karakterler gibi "%" ve "?" kaçış karakterleri eklenmelidir. OPC Ayrıntılar için bkz.  
  
 Aşağıdaki bölümlerde, paketi oluşturmak anlatan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynağı, içerik ve kaynak dosyaları sitesi tanımlamak için bu iki yetkilileri uygun yolları ile birlikte kullanarak.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>Kaynak dosya paketi URI'ler  
 Kaynak dosyaları olarak yapılandırılmış [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` öğeleri ve derlemeleri haline getirilebilen. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Paketi oluşumu destekler [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel bütünleştirilmiş kod içine derlenmiş veya yerel bütünleştirilmiş koddan başvurulan bir derleme içinde derlenen kaynak dosyaları belirlemek için kullanılabilir.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Yerel bütünleştirilmiş kod kaynak dosyası  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol için bir kaynak yerel bütünleştirilmiş kod içine derlenmiş olan dosya kullanır:  
  
-   **Yetkilisi**: uygulama: / / /.  
  
-   **Yol**: Yerel derleme proje klasörü köküne yolunu da dahil olmak üzere kaynak dosyanın adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlemenin yerel proje klasörünün kök dizininde bulunan kaynak dosyası.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak dosyası, derlemenin yerel proje klasörünün bir alt klasörde yer alır.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Başvurulan bütünleştirilmiş kod kaynak dosyası  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol için bir kaynak bir başvurulan bütünleştirilmiş kod içine derlenmiş dosya kullanır:  
  
-   **Yetkilisi**: uygulama: / / /.  
  
-   **Yol**: Başvurulan bir bütünleştirilmiş kod içine derlenmiş bir kaynak dosyasının adıdır. Yol aşağıdaki biçime uymalıdır:  
  
     *AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*  
  
    -   **AssemblyShortName**: başvurulan derleme için kısa bir ad.  
  
    -   **; Sürüm** [isteğe bağlı]: kaynak dosyasını içeren başvurulan derlemenin sürümü. Bu kısa aynı ada sahip iki veya daha fazla başvurulan derlemeler yüklü olduğunda kullanılır.  
  
    -   **; PublicKey** [isteğe bağlı]: başvurulan derlemeyi imzalamak için kullanılan ortak anahtar. Bu kısa aynı ada sahip iki veya daha fazla başvurulan derlemeler yüklü olduğunda kullanılır.  
  
    -   **; Bileşen**: başvurulan derleme yerel bütünleştirilmiş koddan başvurulur belirtir.  
  
    -   **/ Yol**: başvurulan derlemenin proje klasörünün göreli yolunu da dahil olmak üzere kaynak dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünün kök dizininde bulunan kaynak dosyası.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan derlemenin proje klasörünün bir alt klasöründe bulunan kaynak dosyası.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan, sürüme özgü bir derlemenin proje klasörünün kök klasöründe bulunan kaynak dosyası.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Unutmayın paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurulan bütünleştirilmiş kod kaynak dosyalar için söz dizimi, yalnızca uygulama ile kullanılabilir: / / / yetkilisi. Örneğin, aşağıdaki desteklenmeyen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>İçerik dosyası paketi URI'ler  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir içerik dosyası aşağıdaki yetkilisi ve yolu kullanır:  
  
-   **Yetkilisi**: uygulama: / / /.  
  
-   **Yol**: Dosya sistemi konumu uygulamanın ana yürütülebilir derlemenin göreli yolu da dahil olmak üzere içerik dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çalıştırılabilir derlemesinin aynı klasörde bulunan içerik dosyası.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içerik dosyası, uygulamanın yürütülebilir derleme göreli bir alt klasör bulunur.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] İçerik dosyaları için erişilemeyeceğini. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Düzeni yalnızca Gezinti destekler [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] kaynak sitede bulunan dosyalar.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>Kaynak Paketi URI'lerin site  
 Paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] aşağıdaki yetkilisi ve yol bir kaynak sitesi için dosya kullanır:  
  
-   **Yetkilisi**: siteoforigin: / / /.  
  
-   **Yol**: Sitenin içinden çalıştırılabilir derlemesinin başlatıldı konumun göreli yolunu da dahil olmak üzere kaynak dosyasının adı.  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çalıştırılabilir derlemesinin başlatıldığı konumda depolanan kaynak dosyasının site.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 Paketi aşağıdaki örnekte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site kaynak dosyası, uygulamanın yürütülebilir derleme başlatıldığı konumdur göreli alt klasöründe depolanır.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Sayfa dosyası  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak yapılandırılmış olan dosyaları [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri derlemelerine kaynak dosyaları aynı şekilde derlenir. Sonuç olarak, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` öğeleri paketi kullanarak belirlenebilir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynak dosyaları için.  
  
 Tür [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yaygın olarak yapılandırılmış olan dosyaları [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` aşağıdaki kendi kök öğe olarak birine sahip öğeleri:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Mutlak vs. Paketi göreli URI'ler  
 Bir tam paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] şeması ve yetkilisi yolu içerir ve bu mutlak bir paketi varsayılır [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Bir basitleştirme geliştiricileri olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğeleri genellikle izin göreli paketi uygun özniteliklerle ayarlamanızı [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], yalnızca yolu içerir.  
  
 Örneğin, aşağıdaki mutlak paketi düşünün [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerel bütünleştirilmiş kod kaynak dosyası için.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bu kaynağa başvuran dosya, aşağıdaki olur.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Kaynak dosyaları sitesi olmadığından derlemeleri ile ilişkili, bunlar yalnızca mutlak paketiyle başvurulabilen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Varsayılan olarak, göreli bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] işaretleme veya başvuru içeren kod konumun göreli olarak kabul edilir. Önde gelen bir ters eğik çizgi kullanılır, ancak göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuru uygulama köküne göreli sonra kabul edilir. Örneğin, aşağıdaki proje yapısını göz önünde bulundurun.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Page1.XAML içeriyorsa bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran *kök*\SubFolder\Page2.xaml, başvuru şu göreli paketi kullanabilirsiniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Page1.XAML içeriyorsa bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvuran *kök*\Page2.xaml, başvuru şu göreli paketi kullanabilirsiniz [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Pack URI'si çözümleme  
 Paketi biçimi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] paketi mümkün kılar [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dosyaları aynı aramak için farklı türleri için. Örneğin, aşağıdaki mutlak paketi düşünün [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Bu mutlak bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] yerel bütünleştirilmiş kod içinde bir kaynak dosyası veya bir içerik dosyası için başvuru yapabilir. Şu göreli için aynı geçerlidir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Belirlemek için, dosya türü, bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başvurduğu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çözümler [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] yerel derlemeleri ve aşağıdaki buluşsal yöntemlerini kullanarak içerik dosyaları kaynak dosyalar için:  
  
1.  Derleme meta verileri araştırma bir <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> paketi eşleşen öznitelik [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Varsa <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> özniteliği bulunduğunda, yolun paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir içerik dosyasına başvuruyor.  
  
3.  Varsa <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> yerel bütünleştirilmiş kod içine derlenmiş kümesi kaynak dosyalarını araştırma, öznitelik bulunamadı.  
  
4.  Paketi yol ile eşleşen bir kaynak dosya [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bulunduğunda, yolun paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] bir kaynak dosyasına başvuruyor.  
  
5.  Kaynak bulunamazsa, dahili olarak oluşturulan <xref:System.Uri> geçersiz.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Çözüm için geçerli değildir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] şuna başvurun:  
  
-   İçerik dosyaları başvurulan derlemelerde: Bu dosya türlerini tarafından desteklenmeyen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Başvurulan bütünleştirilmiş kod içinde gömülü dosyalar: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] bunları tanımlayan adı başvurulan derlemenin içerirler benzersiz olduğu ve `;component` soneki.  
  
-   Kaynak dosyaları sitesi: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] bunları tanımlayan benzersiz olduğundan, çünkü bunlar yalnızca paketi tarafından tanımlanan dosyalar [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] siteoforigin içeren: / / / yetkilisi.  
  
 Paketi bir basitleştirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çözüm için kaynak ve içerik dosyalarının konumlarını biraz bağımsız olarak kodu sağlar. Örneğin, bir içerik dosyası, paketi yeniden yerel bütünleştirilmiş kod kaynak dosyası varsa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi kullanan kodu gibi kaynak aynı şekilde kalır [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Paketi bir URI'leri ile programlama  
 Birçok [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sınıfları uygulama paketi ayarlanabilir özellikleri [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]de dahil olmak üzere:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Bu özellikleri biçimlendirme hem kod ayarlayabilirsiniz. Bu bölümde, her ikisi için de temel yapılarını gösterir ve daha sonra ortak senaryo örneklerini gösterir.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>Paketi bir URI'leri biçimlendirme içinde kullanma  
 Bir paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] paketi ile bir öznitelik öğe ayarlayarak biçimlendirme içinde belirtilen [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Örneğin:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tablo 1 gösterir çeşitli mutlak paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , işaretlemede belirtebilirsiniz.  
  
 Tablo 1: Biçimlendirme içinde mutlak paketi URI'ler  
  
|Dosya|Mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Kaynak dosyası - yerel derleme|`"pack://application:,,,/ResourceFile.xaml"`|  
|Alt - yerel bütünleştirilmiş kod kaynak dosyası|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Kaynak dosyası - başvurulan derleme|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Başvurulan derlemenin alt kaynak dosyası|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Kaynak dosyasında tutulan başvurulan derleme|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|İçerik dosyası|`"pack://application:,,,/ContentFile.xaml"`|  
|İçerik dosyası alt|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Site kaynak dosyası|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Kaynak dosya alt site|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tablo 2'de çeşitli göreli paketi gösterilir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , işaretlemede belirtebilirsiniz.  
  
 Tablo 2: Biçimlendirme paketi göreli URI'ler  
  
|Dosya|Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Yerel bütünleştirilmiş kod kaynak dosyası|`"/ResourceFile.xaml"`|  
|Alt klasör yerel bütünleştirilmiş kod kaynak dosyası|`"/Subfolder/ResourceFile.xaml"`|  
|Başvurulan bütünleştirilmiş kod kaynak dosyası|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Başvurulan derlemenin alt kaynak dosyası|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|İçerik dosyası|`"/ContentFile.xaml"`|  
|İçerik dosyası alt|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Paketi bir URI'leri kodda kullanma  
 Bir paket belirtin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] örnekleme tarafından kodda <xref:System.Uri> sınıfı ve paketi geçirme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] oluşturucusuna bir parametre olarak. Bu, aşağıdaki örnekte gösterilmiştir.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Varsayılan olarak, <xref:System.Uri> sınıfı olarak değerlendirir, paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] mutlak olacak şekilde. Sonuç olarak, bir özel durum örneği oluşturulur <xref:System.Uri> sınıfı göreli bir paketi ile oluşturulan [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Neyse ki, <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> aşırı yükünü <xref:System.Uri> sınıf oluşturucusu türünde bir parametre kabul eden <xref:System.UriKind> belirtmek olanak tanımak için bir paket olup olmadığını [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] mutlak veya göreli.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Yalnızca belirtmelisiniz <xref:System.UriKind.Absolute> veya <xref:System.UriKind.Relative> olduğunuzda belirli, sağlanan paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] biri veya diğeri. Paketi türünü bilmiyorsanız [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] kullanılan, bir kullanıcı bir paketi girdiğinde gibi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] çalışma zamanında <xref:System.UriKind.RelativeOrAbsolute> yerine.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tablo 3'te gösterilir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kullanarak kod içinde belirtebileceğiniz <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tablo 3: Kod paketi mutlak URI  
  
|Dosya|Mutlak paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Kaynak dosyası - yerel derleme|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Alt - yerel bütünleştirilmiş kod kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Kaynak dosyası - başvurulan derleme|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Başvurulan derlemenin alt kaynak dosyası|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Kaynak dosyasında tutulan başvurulan derleme|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|İçerik dosyası|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|İçerik dosyası alt|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Site kaynak dosyası|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Kaynak dosya alt site|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tablo 4 gösterir çeşitli göreli paketi [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kod kullanarak belirtebileceğiniz <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tablo 4: Kod paketi göreli URI'ler  
  
|Dosya|Göreli paketi [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Kaynak dosyası - yerel derleme|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Alt - yerel bütünleştirilmiş kod kaynak dosyası|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Kaynak dosyası - başvurulan derleme|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Alt - başvurulan bütünleştirilmiş kod kaynak dosyası|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|İçerik dosyası|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|İçerik dosyası alt|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Pack URI'si senaryoları  
 Önceki bölümlerde ele alınan paketi oluşturmak nasıl [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] kaynağı, içerik ve kaynak dosyaları sitesi tanımlamak için. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bu yapılarını çeşitli şekillerde kullanılır ve aşağıdaki bölümler birkaç yaygın kullanımları kapsar.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Bir uygulama başlatıldığında göstermek için kullanıcı Arabirimi belirtme  
 <xref:System.Windows.Application.StartupUri%2A> ilk belirtir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olduğunda gösterilecek bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama başlatılır. Tek başına uygulamalar için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdaki örnekte gösterildiği gibi bir pencere olabilir.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Tek başına uygulamalar ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] bir sayfa ilk kullanıcı Arabirimi, aşağıdaki örnekte gösterildiği gibi belirtebilirsiniz.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Uygulama bir tek başına uygulamasıdır ve bir sayfa ile belirtilen <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] açılır bir <xref:System.Windows.Navigation.NavigationWindow> sayfası barındırabilir. İçin [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], konak tarayıcıda sayfası gösterilir.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Bir sayfaya gitme  
 Aşağıdaki örnek, bir sayfaya gitmek gösterilmektedir.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Gezinme için çeşitli yollar hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [gezintiye genel bakış](navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Pencere simgesini belirtme  
 Aşağıdaki örnek, bir pencerenin simgesini belirtmek için bir URI kullanmayı gösterir.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Daha fazla bilgi için bkz. <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Görüntü, ses ve Video dosyaları yükleniyor  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaların tümü algılanabilir ve paketi yüklü medya türleri, birçok farklı kullanmasını sağlayan [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]aşağıdaki örneklerde gösterildiği gibi.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Medya içeriği ile çalışma hakkında daha fazla bilgi için bkz. [grafikler ve multimedya](../graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Kaynak sitesinden bir kaynak sözlüğü yükleniyor  
 Kaynak sözlükleri (<xref:System.Windows.ResourceDictionary>) uygulama temaları desteklemek için kullanılabilir. Oluşturup temalarını yönetmek için bir yolu, bir uygulamanın kaynak sitede bulunan kaynak sözlükleri olarak birden çok tema oluşturmaktır. Bu, temalar eklenmesi ve güncelleştirilmiş yeniden derlemeden ve bir uygulama dağıtarak sağlar. Bu kaynak sözlükleri tanımlanabilir ve paketi kullanılarak yüklenen [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], aşağıdaki örnekte gösterilmiştir.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Temalar da genel bir bakış için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [stil ve şablon oluşturma](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](wpf-application-resource-content-and-data-files.md)
