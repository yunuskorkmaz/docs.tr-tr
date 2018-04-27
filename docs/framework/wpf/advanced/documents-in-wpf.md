---
title: WPF'deki Belgeler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0fcf7281cce7e5921ad7a03011ff85c254231690
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="documents-in-wpf"></a>WPF'deki Belgeler
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çok çeşitli daha kolay erişilebilen ve okunan önceki nesil içinde olacak şekilde tasarlanmıştır yüksek kaliteli içerik oluşturulmasını sağlamak belge özellikleri sunan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Gelişmiş Özellikler ve kaliteye, ek olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belge görüntüleme, paketleme ve güvenlik için tümleşik hizmetleri de sağlar. Bu konuda tanıtılmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belge türleri ve belge paketleme.  
  
  
<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Belge türleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belgeleri kullanım amaçlarına göre iki geniş kategorilere ayırır; Bu Belge kategorileri "sabit" ve "akış belgeler." olarak adlandırılır  
  
 Sabit belgeleri bir kesin gerektiren uygulamalar için amaçlanan [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] sunu, görüntüleme ya da yazıcı donanımından kullanılan bağımsızdır. Sabit belgeler genel kullanımları masaüstü yayımlama, sözcük işleme ve özgün sayfa tasarımı bağlılığı kritik olduğu form düzeni içerir. Yerleşimi işleminin bir parçası olarak, sabit bir belge içerik öğelerinin kesin konumsal yerleştirme görüntüleme veya yazdırma aygıtı kullanımda bağımsız olarak korur. 4800 dpi phototypesetter çıktısına olduğunda bu 600 dpi lazer yazıcı için çıkış, örneğin, 96 DPI'de ekranda görüntülenen bir sabit belge sayfası tam olarak aynı görüntülenir. Her cihaz özelliklerini belge kalitesini en üst düzeye çıkarır yüklenirken sayfa düzeni tüm durumlarda aynı kalır.  
  
 Karşılaştırma akış belgeleri görüntülemeyi ve okunabilirliği iyileştirmek için tasarlanmıştır ve Okuma Kolaylığı birincil belge tüketim senaryosu olduğunda en iyi yararlanılmıştır. Önceden tanımlanmış bir düzene ayarlanan, yerine akan belgeler dinamik olarak ayarlayın ve çalışma zamanı değişkenleri pencere boyutu, aygıt çözünürlüğü ve isteğe bağlı kullanıcı tercihleri gibi temel içeriklerini yeniden akışı. Bir Web sayfası bir basit bir akış belge burada sayfa içeriği dinamik olarak geçerli penceresine sığacak şekilde biçimlendirilmiş örneğidir. Akış belgeleri görüntüleme ve çalışma zamanı ortamını temel alarak kullanıcı deneyimi okuma iyileştirin. Örneğin, aynı akan belge, yüksek çözünürlüklü 19-inch Görüntü veya küçük 2 x 3-inch PDA ekranında uygun okunabilirlik için dinamik olarak biçimlendirilmektedir. Ayrıca, akış belgeleri görüntüleme okunabilirlik ve boyutunu ve yazı tipleri görünümünü değiştirme yeteneğini en iyi duruma modları arama da dahil olmak üzere özellikleri yerleşik bir dizi sahip.  Bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md) çizimler, örnekler ve akan belgeler hakkında ayrıntılı bilgi.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Belge denetimleri ve metin düzeni  
 .NET Framework sabit belgeleri, akış belgeleri ve uygulamanızdaki genel metin kullanımını kolaylaştıran önceden derlenmiş denetimleri kümesini sağlar.  Sabit belgenin içerik görünümü kullanarak desteklenen <xref:System.Windows.Controls.DocumentViewer> denetim.  Akış belgenin içerik görünümü üç farklı denetimleri tarafından desteklenir: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> eşlemek için farklı kullanıcı senaryoları (aşağıdaki bölümlere bakın).  Diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri sağlar genel metin desteklemek için basitleştirilmiş bir düzen kullanır (bkz [metin kullanıcı arabiriminde](#text_in_the_user_interface), aşağıdaki).  
  
### <a name="fixed-document-control---documentviewer"></a>Belge denetimi - BelgeGörünümü  
 <xref:System.Windows.Controls.DocumentViewer> Denetim görüntülemek için tasarlanmıştır <xref:System.Windows.Documents.FixedDocument> içeriği. <xref:System.Windows.Controls.DocumentViewer> Denetimi yazdırma çıkış dahil olmak üzere ortak işlemleri kopyalamak için Pano, yakınlaştırma ve metin arama özellikleri için yerleşik destek sağlayan bir sezgisel bir kullanıcı arabirimi sağlar. Denetim tanıdık bir kaydırma mekanizması aracılığıyla içerik sayfalarına erişimi sağlar. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri <xref:System.Windows.Controls.DocumentViewer> destekleyen, tam veya kısmi yeniden tasarıma denetim görsel olarak herhangi bir uygulama veya ortam tümleşik olmasını sağlar.  
  
 <xref:System.Windows.Controls.DocumentViewer> salt okunur bir biçimde içeriği görüntülemek için tasarlanmıştır; düzenleme veya içerik değiştirilmesini kullanılabilir değil ve desteklenmiyor.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Akış belge denetimleri  
 **Not:** akan belge özellikleri ve bunların nasıl oluşturulacağı hakkında daha ayrıntılı bilgi için bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 Akış belgenin içerik görünümü üç denetimleri tarafından desteklenir: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> kullanıcının bir tek sayfalı (sayfa--bir zamanda) görüntüleme modu, bir iki-sayfası--a-modu ve sürekli bir kayan (sınırsız) görüntüleme modu zamanda (defter okuma biçimi) dahil olmak üzere çeşitli görüntüleme modları arasında dinamik olarak seçmesini sağlayan özellikler içerir.  Bu görüntüleme modları hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Farklı görüntüleme modları arasında dinamik geçiş özelliği gerekmiyorsa <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> hafifletilmiş akış belirli görüntüleme modunda sabit içerik görüntüleyicileri sağlar.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer ve FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Sayfa--bir zamanda içinde içerik gösterir modu, görüntülerken <xref:System.Windows.Controls.FlowDocumentScrollViewer> sürekli kaydırma modunda içerik gösterir.  Her ikisi de <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli görüntüleme moduna sabitlenmiştir. Karşılaştırılacak <xref:System.Windows.Controls.FlowDocumentReader>, kullanıcının çeşitli görüntüleme modları arasında dinamik olarak seçmesini sağlayan özellikler içerir (tarafından sağlanan gibi <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> numaralandırması), daha fazla kaynak yoğunluğu olan artırılabilir <xref:System.Windows.Controls.FlowDocumentPageViewer> veya <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Varsayılan olarak, dikey kaydırma çubuğu her zaman gösterilir ve yatay kaydırma çubuğu gerektiğinde görünür duruma gelir. Varsayılan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için <xref:System.Windows.Controls.FlowDocumentScrollViewer> bir araç çubuğu içermez; ancak, <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özelliği, yerleşik bir araç çubuğunu etkinleştirmek için kullanılabilir.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Kullanıcı arabiriminde metin  
 Belgelerde metin ekleme yanı sıra metin açıkça formlar gibi uygulama kullanıcı Arabirimi kullanılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekrana metin çizme için birden çok denetim içerir. Her denetim için farklı bir senaryo hedeflenen ve kendi listesi özellikleri ve sınırlamaları vardır. Genel olarak, <xref:System.Windows.Controls.TextBlock> öğesi sınırlı metin desteği içindeki kısa tümce gibi gerekli olduğunda kullanılmalıdır bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için bkz: [TextBlock genel bakış](../../../../docs/framework/wpf/controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Belge paketleme  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Uygulama verileri, belge içerik ve ilgili kaynakları taşınabilir ve dağıtımı kolay erişim için basit tek bir kapsayıcıdaki düzenlemek için verimli bir yol sağlar. ZIP dosyası örneğidir bir <xref:System.IO.Packaging.Package> türünde birden fazla nesne tek bir birim olarak tutabilen. Paketleme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] varsayılan bir sağlamak <xref:System.IO.Packaging.ZipPackage> XML ve ZIP dosyası mimarisiyle bir Open Packaging Conventions standardını kullanarak tasarlanmış uygulama. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paketleme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] paketlerini oluşturma ve depolamak ve içindeki nesneleri erişmek basitleştirir. İçinde depolanan bir nesne bir <xref:System.IO.Packaging.Package> olarak adlandırılır bir <xref:System.IO.Packaging.PackagePart> ("bölümünü"). Paketleri gönderene bir bölümü, tanımlamak ve bir paket içeriğini değiştirilmemiş doğrulamak için kullanılan dijital olarak imzalanan sertifikalar de içerir.  Paketleri de dahil bir <xref:System.IO.Packaging.PackageRelationship> ek bilginin pakete eklenmesine veya var olan bölümlerin içeriğini değiştirmeden belirli bölümlerle ilişkilendirilmesine izin veren özellik.  Paket Hizmetleri ayrıca Destek [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paket mimarisi, anahtar teknolojileri sayısı için temel görür:  
  
-   [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] uyumludur belgeleri [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Microsoft Office "12" open XML biçimi belgeleri (.docx).  
  
-   Uygulama tasarımı için özel depolama biçimleri.  
  
 API'sine, dayanarak bir <xref:System.Windows.Xps.Packaging.XpsDocument> depolamak için özel olarak tasarlanmıştır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik belgelerini sabit. Bir <xref:System.Windows.Xps.Packaging.XpsDocument> görüntülenen Görüntüleyicisi ' nde açtığınız kendi içinde bulunan bir belge bir <xref:System.Windows.Controls.DocumentViewer> için yazdırma biriktirme yönlendirilen veya doğrudan çıktı denetimi, bir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-uyumlu yazıcı.  
  
 Aşağıdaki bölümlerde ek bilgileri sağlayan <xref:System.IO.Packaging.Package> ve <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ile sağlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Paket bileşenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paketleme API'leri uygulama verilerini ve belgelerinin bir taşınabilir ünite düzenlenmesine izin verir. ZIP dosyası en sık karşılaşılan paketleri biridir ve varsayılan paket türü ile sağlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> kendisini bir özet sınıftan olduğu <xref:System.IO.Packaging.ZipPackage> open standard XML ve ZIP dosyası mimarisi kullanılarak uygulanır.  <xref:System.IO.Packaging.Package.Open%2A> Yöntemi kullanan <xref:System.IO.Packaging.ZipPackage> oluşturulur ve ZIP dosyaları varsayılan olarak kullanılır. Bir paket üç temel türde öğe içerebilir:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Uygulama içeriği, verileri, belgeler ve kaynak dosyaları.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[X.509 sertifikası] tanımlama, kimlik doğrulaması ve doğrulama.|  
|<xref:System.IO.Packaging.PackageRelationship>|Paket veya belirli bir bölümü ilgili bilgiler eklendi.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("") parçasıdır depolanan bir nesneye başvuruda bulunan bir Özet sınıf bir <xref:System.IO.Packaging.Package>. ZIP dosyasında, paket bölümleri ZIP dosyasının içinde depolanan bireysel dosyalara karşılık gelir.  <xref:System.IO.Packaging.ZipPackagePart> serileştirilebilir nesneler depolanan varsayılan uygulamasını sağlar bir <xref:System.IO.Packaging.ZipPackage>.  Bir dosya sistemi gibi pakette yer alan bölümleri hiyerarşik dizin veya "klasör stili" kuruluş içinde depolanır.  Kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'leri paketleme, uygulamalar yazma, depolamak ve birden çok okuma <xref:System.IO.Packaging.PackagePart> tek bir ZIP dosyası kapsayıcısı kullanarak nesneleri.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Güvenlik için bir <xref:System.IO.Packaging.PackageDigitalSignature> ("dijital imzası") bir paket içinde bölümleri ile ilişkili olabilir. A <xref:System.IO.Packaging.PackageDigitalSignature> [509] içererek iki özellik sağlar:  
  
1.  Tanımlar ve bölümünün gönderenin kimliğini doğrular.  
  
2.  Bölümü değiştirilmedi doğrular.  
  
 Dijital imza bir bölümü değiştirilmesini değil, ancak herhangi bir şekilde bölümü değiştirilirse, dijital imza karşı doğrulama denetimi başarısız olur. Uygulama daha sonra uygun eylemi alabilir — Örneğin, bölümün açılmasını engellemek veya Kullanıcı bildirim bölümü değiştirildi ve güvenli değildir.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("ilişki") ek bilgileri paket veya bir bölümü paket içinde ilişkilendirmek için bir mekanizma sağlar. Ek bilgi bölümü ile gerçek bölümü içeriğini değiştirmeden ilişkilendirebilirsiniz bir paket düzeyi tesis ilişkidir. Yeni veri doğrudan bölümü içeriğini ekleme genellikle birçok durumda pratik değildir:  
  
-   Bölümü ve içerik şeması gerçek türü bilinmiyor.  
  
-   Bilinen olsa bile, içerik şeması yeni bilgi eklemek için bir yol sağlamayabilir.  
  
-   Bölümü dijital olarak olabilir imzalanmış veya şifrelenmiş, değişimi engellemek.  
  
 Paket ilişkileri ekleme ve ek bilgileri tek tek parçaları veya tüm paketi ile ilişkilendirmek için bulunabilirlik olanağı sağlar. Paket ilişkileri iki birincil işlevleri için kullanılır:  
  
1.  Başka bir bölümü bir bölümünden bağımlılık ilişkileri tanımlama.  
  
2.  Notlar veya bölümü ilişkili diğer veri ekleme bilgi ilişkileri tanımlama.  
  
 A <xref:System.IO.Packaging.PackageRelationship> bağımlılıkları tanımlamak ve bir paket veya bir bütün olarak paketin parçası ile ilişkili diğer bilgileri eklemek için bir hızlı, keşfedilebilir yollar sağlar.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Bağımlılık ilişkileri  
 Bağımlılık ilişkileri diğer bölümlerine parçası yapar bağımlılıkları tanımlamak için kullanılır. Örneğin, bir paket birini veya daha fazla bilgi içeren bir HTML bölümü içerebilir \<img > görüntü etiketi. Görüntü etiketleri ya da diğer bölümleri pakete iç veya dış pakete olarak bulunduğu görüntülere bakın (gibi Internet üzerinden erişilebilir). Oluşturma bir <xref:System.IO.Packaging.PackageRelationship> bulmak ve bağımlı kaynaklara erişimi hızlı ve kolay HTML dosyası yapar ile ilişkilendirilmiş. Bir tarayıcı veya Görüntüleyicisi uygulaması doğrudan bölümü ilişkileri erişebilir ve şemayı bilmeden veya belge ayrıştırma bağımlı kaynaklar atayarak hemen başlayın.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Bilgi ilişkileri  
 Bir not veya ek açıklama, benzer bir <xref:System.IO.Packaging.PackageRelationship> başka tür gerçekte bölümü içeriğini değiştirmek zorunda kalmadan bir bölümü ile ilişkilendirilecek bilgileri depolamak için de kullanılabilir.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS belgeleri  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] Belge tüm kaynaklara ve işleme için gereken bilgilerle birlikte bir veya daha fazla sabit-belgeleri içeren bir pakettir.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] aynı zamanda yerel olan [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] yazdırma biriktirme dosya biçimidir.  Bir <xref:System.Windows.Xps.Packaging.XpsDocument> standart ZIP veri kümesinde depolanır ve XML ve görüntü ve yazı tipi dosyaları gibi ikili bileşenleri bir birleşimini içerebilir. [PackageRelationships](#PackageRelationships) içerik ve tam olarak belgeyi işlemek için gereken kaynaklar arasındaki bağımlılıkları tanımlamak için kullanılır.  <xref:System.Windows.Xps.Packaging.XpsDocument> Tasarımı birden çok kullandığı destekleyen tek, yüksek doğruluk belge çözümü sağlar:  
  
-   Okuma, yazma ve sabit belgesinin içeriği ve kaynakları tek, taşınabilir ve kolay dağıtmak dosyası olarak depolamak.  
  
-   Belgelerle görüntüleme [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] görüntüleyici uygulaması.  
  
-   Çıktı biçimi yerel yazdırma biriktirme belgelerde çıktısını [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Yönlendirme belgeleri doğrudan bir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-uyumlu yazıcı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.FixedDocument>  
 <xref:System.Windows.Documents.FlowDocument>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.IO.Packaging.ZipPackage>  
 <xref:System.IO.Packaging.ZipPackagePart>  
 <xref:System.IO.Packaging.PackageRelationship>  
 <xref:System.Windows.Controls.DocumentViewer>  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Akış Belgesine Genel Bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Belge Serileştirme ve Depolama](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)
