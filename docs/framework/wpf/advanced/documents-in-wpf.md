---
title: Belgeler
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174686"
---
# <a name="documents-in-wpf"></a>WPF'deki Belgeler
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]önceki nesil Windows'a göre daha kolay erişilebilmek ve okunacak şekilde tasarlanmış yüksek kaliteli içerik oluşturulmasını sağlayan çok çeşitli belge özellikleri sunar. Gelişmiş yeteneklere ve kaliteye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ek olarak, belge görüntüleme, paketleme ve güvenlik için entegre hizmetler de sağlar. Bu konu, belge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türlerine ve belge paketlemeye giriş sağlar.  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>Belge Türleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]belgeleri kullanım amaçlarına göre iki geniş kategoriye ayırır; bu belge kategorileri "sabit belgeler" ve "akış belgeleri" olarak adlandırılır.  
  
 Sabit belgeler, kullanılan ekran veya yazıcı donanımından bağımsız olarak kesin bir "ne gördüğünüzü elde ettiğinizdir" (WYSIWYG) sunusu gerektiren uygulamalar için tasarlanmıştır. Sabit belgeler için tipik kullanımlar masaüstü yayımlama, sözcük işleme ve özgün sayfa tasarımına bağlılığın kritik olduğu form düzenini içerir. Düzeninbir parçası olarak, sabit bir belge, kullanımdaki görüntü veya yazdırma aygıtından bağımsız içerik öğelerinin kesin konumsal yerleşimini korur. Örneğin, 96 dpi ekranda görüntülenen sabit bir belge sayfası, 4800 dpi fototipbelirleyiciye çıktıalındığında olduğu gibi 600 dpi lazer yazıcıya çıktıalındığında tam olarak aynı görünür. Belge kalitesi her aygıtın yeteneklerini en üst düzeye çıkarırken, sayfa düzeni her durumda aynı kalır.  
  
 Buna karşılık, akış belgeleri görüntüleme ve okunabilirliği optimize etmek için tasarlanmıştır ve okuma kolaylığı birincil belge tüketim senaryosu olduğunda en iyi şekilde kullanılır. Akış belgeleri, önceden tanımlanmış bir düzene ayarlanmak yerine, pencere boyutu, aygıt çözünürlüğü ve isteğe bağlı kullanıcı tercihleri gibi çalışma zamanı değişkenlerine göre içeriklerini dinamik olarak ayarlar ve yeniden atarım. Web sayfası, sayfa içeriğinin geçerli pencereye uyacak şekilde dinamik olarak biçimlendirilmiş akış belgesinin basit bir örneğidir. Akış belgeleri, çalışma zamanı ortamına bağlı olarak kullanıcı için görüntüleme ve okuma deneyimini optimize eder. Örneğin, aynı akış belgesi, yüksek çözünürlüklü 19 inç ekranda veya küçük bir 2x3 inç PDA ekranda en iyi okunabilirlik için dinamik olarak yeniden biçimlendirilebilir. Buna ek olarak, akış belgeleri arama, okunabilirliği en iyi duruma getiren görüntüleme modları ve yazı tiplerinin boyutunu ve görünümünü değiştirme olanağı dahil olmak üzere yerleşik özellikler içeren bir dizi özelliğe sahiptir.  Akış belgeleriyle ilgili resimler, örnekler ve ayrıntılı bilgiler için [Akış Belgesine Genel Bakış'a](flow-document-overview.md) bakın.  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>Belge Denetimleri ve Metin Düzeni  
 .NET Framework, uygulamanızdaki sabit belgeleri, akış belgelerini ve genel metni kullanmayı basitleştiren bir dizi önceden oluşturulmuş denetim sağlar.  Sabit belge içeriğinin görüntülenmesi <xref:System.Windows.Controls.DocumentViewer> denetim kullanılarak desteklenir.  Akış belgesi içeriğinin görüntülenmesi üç farklı <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>denetimle <xref:System.Windows.Controls.FlowDocumentScrollViewer> desteklenir: , , ve farklı kullanıcı senaryolarına hangi eş (aşağıdaki bölümlere bakın).  Diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimler, genel metin kullanımlarını desteklemek için basitleştirilmiş düzen sağlar (aşağıdaki [Kullanıcı Arabirimindeki Metin'e](#text_in_the_user_interface)bakın).  
  
### <a name="fixed-document-control---documentviewer"></a>Sabit Belge Kontrolü - DocumentViewer  
 Denetim <xref:System.Windows.Controls.DocumentViewer> içeriği görüntülemek <xref:System.Windows.Documents.FixedDocument> için tasarlanmıştır. Denetim, <xref:System.Windows.Controls.DocumentViewer> yazdırma çıktısı, panoya kopyalama, yakınlaştırma ve metin arama özellikleri gibi yaygın işlemler için yerleşik destek sağlayan sezgisel bir kullanıcı arabirimi sağlar. Denetim, tanıdık bir kaydırma mekanizması aracılığıyla içerik sayfalarına erişim sağlar. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimler <xref:System.Windows.Controls.DocumentViewer> gibi, denetimin hemen hemen her uygulamaya veya ortama görsel olarak entegre edilmesini sağlayan tam veya kısmi yeniden şekillendirmeyi destekler.  
  
 <xref:System.Windows.Controls.DocumentViewer>içeriği salt okunur şekilde görüntülemek için tasarlanmıştır; içeriğin düzenlenmesi veya değiştirilmesi kullanılamaz ve desteklenmez.  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>Akış Belgesi Denetimleri  

> [!NOTE]
> Akış belgesi özellikleri ve bunların nasıl oluşturulması hakkında daha ayrıntılı bilgi için Akış [Belgesine Genel Bakış'a](flow-document-overview.md)bakın.  
  
 Akış belgesi içeriğinin görüntülenmesi üç <xref:System.Windows.Controls.FlowDocumentReader>denetimle desteklenir: , , <xref:System.Windows.Controls.FlowDocumentPageViewer>ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>tek sayfalık (aynı anda sayfa) görüntüleme modu, aynı anda iki sayfa (kitap okuma biçimi) görüntüleme modu ve sürekli kaydırma (dipsiz) görüntüleme modu gibi çeşitli görüntüleme modları arasında dinamik olarak seçim yapabilmesini sağlayan özellikler içerir.  Bu görüntüleme modları hakkında daha <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>fazla bilgi için bkz.  Farklı görüntüleme modları arasında dinamik olarak geçiş yapma <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli bir görüntüleme modunda sabitlenmiş daha hafif akış içeriği görüntüleyiciler sağlama yeteneğine ihtiyacınız yoksa.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer ve FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>içeriği sürekli kaydırma modunda gösterirken, <xref:System.Windows.Controls.FlowDocumentScrollViewer> içeriği zamanında sayfa görüntüleme modunda gösterir.  Her <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> ikisi de ve belirli bir görüntüleme moduna sabitlenir. Karşılaştırın <xref:System.Windows.Controls.FlowDocumentReader>, kullanıcı dinamik olarak çeşitli görüntüleme modları arasında seçim sağlayan <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> özellikleri içeren (numaralandırma tarafından sağlanan), daha <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer>fazla kaynak yoğun olma pahasına veya .  
  
 Varsayılan olarak, dikey kaydırma çubuğu her zaman gösterilir ve gerekirse yatay kaydırma çubuğu görünür hale gelir. Varsayılan <xref:System.Windows.Controls.FlowDocumentScrollViewer> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir araç çubuğu içermez; ancak, <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özellik yerleşik bir araç çubuğu etkinleştirmek için kullanılabilir.  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>Kullanıcı Arabirimindeki Metin  
 Belgelere metin eklemenin yanı sıra, metin açıkça formlar gibi uygulama kullanıcı bilgisinde kullanılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekrana metin çizmek için birden çok denetim içerir. Her denetim farklı bir senaryoyu hedeflemektedir ve kendi özellik ve sınırlamalar listesi vardır. Genel olarak, <xref:System.Windows.Controls.TextBlock> öğe sınırlı metin desteği gerektiğinde kullanılmalıdır( örneğin bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>en az metin desteği gerektiğinde kullanılabilir. Daha fazla bilgi için [TextBlock Genel Bakış'a](../controls/textblock-overview.md)bakın.  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>Belge Paketleme  
 API'ler, <xref:System.IO.Packaging> uygulama verilerini, belge içeriğini ve ilgili kaynakları, erişimi kolay, taşınabilir ve dağıtılması kolay tek bir kapsayıcıda düzenlemek için etkili bir araç sağlar. ZIP dosyası, birden çok <xref:System.IO.Packaging.Package> nesneyi tek bir birim olarak tutabilen bir türörneğidir. Ambalaj API'leri, <xref:System.IO.Packaging.ZipPackage> XML ve ZIP dosya mimarisine sahip bir Açık Ambalaj Kuralları standardı kullanılarak tasarlanmış varsayılan bir uygulama sağlar. Ambalaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'leri, paketler oluşturmayı ve içindeki nesneleri depolamayı ve bunlara erişmelerini kolaylaştırır. A'da <xref:System.IO.Packaging.Package> depolanan bir <xref:System.IO.Packaging.PackagePart> nesneye ("parça") denir. Paketler, bir parçanın kaynağını belirlemek ve paketin içeriğinin değiştirilmediğini doğrulamak için kullanılabilecek imzalı dijital sertifikalar da içerebilir.  Paketler ayrıca, <xref:System.IO.Packaging.PackageRelationship> bir pakete ek bilgi eklenmesini veya varolan parçaların içeriğini gerçekten değiştirmeden belirli parçalarla ilişkilendirilmesine olanak tanıyan bir özellik de içerir.  Paket hizmetleri, Microsoft Windows Hakları Yönetimi'ni (RM) da destekler.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paket mimarisi, bir dizi önemli teknolojinin temelini oluşturur:  
  
- XML Kağıt Belirtimi 'ne (XPS) uygun XPS belgeleri.  
  
- Microsoft Office "12" açık XML biçimli belgeler (.docx).  
  
- Kendi uygulama tasarımınız için özel depolama biçimleri.  
  
 Ambalaj API'lerine göre, sabit <xref:System.Windows.Xps.Packaging.XpsDocument> içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belgelerini depolamak için özel olarak tasarlanmıştır. An, <xref:System.Windows.Xps.Packaging.XpsDocument> görüntüleyicide açılabilir, <xref:System.Windows.Controls.DocumentViewer> denetimde görüntülenebilir, yazdırma havuzuna yönlendirilebilir veya doğrudan XPS uyumlu bir yazıcıya çıktı elde edilebilen bağımsız bir belgedir.  
  
 Aşağıdaki bölümlerde, sağlanan <xref:System.IO.Packaging.Package> API'ler <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve API'ler hakkında ek bilgiler sağlanır.  
  
<a name="packages"></a>
### <a name="package-components"></a>Paket Bileşenleri  
 Ambalaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'leri, uygulama verilerinin ve belgelerinin tek bir taşınabilir birim halinde düzenlenmesine olanak sağlar. ZIP dosyası en yaygın paket türlerinden biridir ve varsayılan paket [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]türü ile sağlanır.  <xref:System.IO.Packaging.Package>kendisi açık standart XML ve ZIP dosya mimarisi kullanılarak uygulanan soyut bir <xref:System.IO.Packaging.ZipPackage> sınıftır.  Yöntem, <xref:System.IO.Packaging.Package.Open%2A> <xref:System.IO.Packaging.ZipPackage> varsayılan olarak ZIP dosyaları oluşturmak ve kullanmak için kullanır. Paket üç temel öğe türü içerebilir:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Uygulama içeriği, veriler, belgeler ve kaynak dosyaları.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[X.509 Sertifikası] tanımlama, kimlik doğrulama ve doğrulama için.|  
|<xref:System.IO.Packaging.PackageRelationship>|Paketle veya belirli bir parçayla ilgili bilgiler eklendi.|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>Paket Parçaları  
 A <xref:System.IO.Packaging.PackagePart> ("bölüm"), bir 'de depolanan nesneye <xref:System.IO.Packaging.Package>başvuran soyut bir sınıftır. Bir ZIP dosyasında, paket parçaları ZIP dosyasında depolanan tek tek dosyalara karşılık gelir.  <xref:System.IO.Packaging.ZipPackagePart>bir <xref:System.IO.Packaging.ZipPackage>' de depolanan serileştirilebilir nesneler için varsayılan uygulama sağlar.  Dosya sistemi gibi, pakette bulunan parçalar da hiyerarşik dizin veya "klasör stili" organizasyonunda depolanır.  Uygulamalar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ambalaj API'lerini kullanarak tek bir <xref:System.IO.Packaging.PackagePart> ZIP dosya kapsayıcısı kullanarak birden çok nesne yazabilir, depolayabilir ve okuyabilir.  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>PaketDijital İmzalar  
 Güvenlik için, <xref:System.IO.Packaging.PackageDigitalSignature> bir paket içindeki parçalarla ("dijital imza") ilişkilendirilebilir. A, <xref:System.IO.Packaging.PackageDigitalSignature> iki özellik sağlayan bir [509] içerir:  
  
1. Parçanın kaynağını tanımlar ve doğrular.  
  
2. Parçanın değiştirilmediğini doğrular.  
  
 Dijital imza bir parçanın değiştirilmesini engellemez, ancak parça herhangi bir şekilde değiştirilirse dijital imzaya karşı doğrulama denetimi başarısız olur. Uygulama daha sonra uygun eylemi gerçekleştirebilir (örneğin, parçanın açılmasını engelleyebilir veya kullanıcıya parçanın değiştirildiğini ve güvenli olmadığını bildirebilir.  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>Paket İlişkileri  
 Bir <xref:System.IO.Packaging.PackageRelationship> ("ilişki"), paketle veya paket içindeki bir parçayla ek bilgileri ilişkilendirme mekanizması sağlar. İlişki, gerçek parça içeriğini değiştirmeden ek bilgileri bir parçayla ilişkilendirebilen paket düzeyindeki bir tesistir. Yeni verilerin doğrudan parça içeriğine eklenmesi çoğu durumda genellikle pratik değildir:  
  
- Parçanın gerçek türü ve içeriği şeması bilinmemektedir.  
  
- Bilinse bile, içerik şeması yeni bilgi eklemek için bir araç sağlamayabilir.  
  
- Parça dijital olarak imzalanmış veya şifrelenmiş olabilir, herhangi bir değişiklik engelleyici.  
  
 Paket ilişkileri, tek tek parçalarla veya paketin tamamıyla ek bilgi eklemek ve ilişkilendirmek için keşfedilebilir bir araç sağlar. Paket ilişkileri iki birincil işlev için kullanılır:  
  
1. Bağımlılık ilişkilerini bir bölümden diğerine tanımlama.  
  
2. Bölümle ilgili notlar veya diğer veriler ekleyen bilgi ilişkilerini tanımlama.  
  
 A, <xref:System.IO.Packaging.PackageRelationship> bağımlılıkları tanımlamak ve paketin bir parçası yla veya paketin bir bütün olarak bir parçasıyla ilişkili diğer bilgileri eklemek için hızlı ve keşfedilebilir bir araç sağlar.  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>Bağımlılık İlişkileri  
 Bağımlılık ilişkileri, bir bölümün diğer bölümlere yaptığı bağımlılıkları açıklamak için kullanılır. Örneğin, bir paket, bir veya daha fazla \<img> resim etiketlerini içeren bir HTML parçası içerebilir. Resim etiketleri, paketin dahili diğer parçaları veya paketin dışında bulunan (Internet üzerinden erişilebilir gibi) görüntülere atıfta bulunur. HTML <xref:System.IO.Packaging.PackageRelationship> dosyasıyla ilişkili bir dosya oluşturmak, bağımlı kaynakları hızlı ve kolay bir şekilde keşfetmeyi ve erişmelerini sağlar. Tarayıcı veya görüntüleyici uygulaması, parça ilişkilerine doğrudan erişebilir ve şema bilmeden veya belgeyi ayrıştırmadan bağımlı kaynakları hemen bir araya etmeye başlayabilir.  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>Bilgi İlişkileri  
 Not veya ek açıklamaya benzer <xref:System.IO.Packaging.PackageRelationship> şekilde, parça içeriğinin kendisini gerçekten değiştirmek zorunda kalmadan bir parçayla ilişkilendirilecek diğer bilgi türlerini depolamak için de kullanılabilir.  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>XPS Belgeleri  
 XML Kağıt Belirtimi (XPS) belgesi, işleme için gerekli tüm kaynaklar ve bilgilerle birlikte bir veya daha fazla sabit belge içeren bir pakettir.  XPS aynı zamanda ana Windows Vista baskı makara dosya biçimidir.  Bir <xref:System.Windows.Xps.Packaging.XpsDocument> standart ZIP veri kümesinde depolanır ve görüntü ve yazı tipi dosyaları gibi XML ve ikili bileşenlerin bir birleşimini içerebilir. [Packageİlişkiler,](#PackageRelationships) belgeyi tam olarak işlemek için içerik ve gereken kaynaklar arasındaki bağımlılıkları tanımlamak için kullanılır.  Tasarım, <xref:System.Windows.Xps.Packaging.XpsDocument> birden çok kullanımı destekleyen tek bir yüksek doğruluklu belge çözümü sağlar:  
  
- Sabit belge içeriği ve kaynakları tek, taşınabilir ve dağıtılması kolay bir dosya olarak okuma, yazma ve depolama.  
  
- XPS Görüntüleyici uygulamasıyla belgeleri görüntüleme.  
  
- Belgeleri Windows Vista'nın yerel yazdırma makara çıktı biçiminde çıkarma.  
  
- Belgeleri doğrudan XPS uyumlu bir yazıcıya yönlendirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Metin](optimizing-performance-text.md)
- [Akış Belgesine Genel Bakış](flow-document-overview.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Belge Serileştirme ve Depolama](document-serialization-and-storage.md)
