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
ms.openlocfilehash: eccb333b8e9a71ea30454f8bdf9fd2bf6dc90b9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737961"
---
# <a name="documents-in-wpf"></a>WPF'deki Belgeler
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], Windows 'un önceki nesinden daha kolay erişilmesi ve okunması için tasarlanan yüksek kaliteli içerik oluşturulmasına olanak tanıyan çok çeşitli belge özellikleri sunmaktadır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], gelişmiş özellik ve kalite özelliklerine ek olarak belge görüntüleme, paketleme ve güvenlik için tümleşik hizmetler de sağlar. Bu konuda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belge türleri ve belge paketleme hakkında bir giriş sunulmaktadır.  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Belge türleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], belgeleri amaçlanan kullanım amaçlarına göre iki geniş kategoriye ayırır; Bu belge kategorileri "sabit belgeler" ve "akış belgeleri" olarak adlandırılır.  
  
 Sabit belgeler, kullanılan ekran veya yazıcı donanımından bağımsız olarak kesin bir "gördükleriniz, sizin alacağınız Özellikler" (WYSıWYG) sunumu gerektiren uygulamalar için tasarlanmıştır. Sabit belgeler için tipik kullanımlar, masaüstü yayımlama, sözcük işleme ve form düzeni içerir. Bu, Özgün sayfa tasarımına yönelik bağlılığı önemli bir öneme sahiptir. Düzeninin bir parçası olarak, sabit bir belge, kullanımda olan görüntüleme veya yazdırma cihazından bağımsız olarak içerik öğelerinin kesin konumsal yerleşimini saklar. Örneğin, 96 DPI ekran üzerinde görüntülenen sabit bir belge sayfası, bir 4800 dpi phototypesetter 'a çıktı olduğunda bir 600 DPI lazer yazıcıya çıktı olduğunda tam olarak aynı görüntülenir. Sayfa düzeni her durumda aynı kalır, ancak belge kalitesi her bir cihazın özelliklerine en üst düzeye çıkarır.  
  
 Bilgi, akış belgeleri, görüntüleme ve okunabilirliği iyileştirmek için tasarlanmıştır ve okuma kolaylığı birincil belge tüketim senaryosuyla kullanılırken en iyi şekilde kullanılır. Akış belgeleri, önceden tanımlanmış bir düzene ayarlanmaktansa, pencere boyutu, cihaz çözünürlüğü ve isteğe bağlı Kullanıcı tercihleri gibi çalışma zamanı değişkenlerine göre içeriğini dinamik olarak ayarlayıp yeniden düzenler. Web sayfası, sayfa içeriğinin dinamik olarak geçerli pencereye sığacak şekilde biçimlendirildiği bir akış belgesine ilişkin basit bir örnektir. Akış belgeleri, çalışma zamanı ortamına bağlı olarak Kullanıcı için görüntüleme ve okuma deneyimini iyileştirir. Örneğin, aynı Flow belgesi, yüksek çözünürlüklü 19 inç ekran veya küçük 2x3 inç PDA ekranında en iyi okunabilirlik için dinamik olarak yeniden biçimlendirir. Ayrıca, akış belgelerinin arama, okunabilirliği en iyileştiren modlar ve yazı tiplerinin boyutunu ve görünümünü değiştirme özelliği dahil olmak üzere çeşitli yerleşik özellikleri vardır.  Akış belgeleri hakkında çizimler, örnekler ve ayrıntılı bilgi için bkz. [akış belgesi genel bakış](flow-document-overview.md) .  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Belge denetimleri ve metin düzeni  
 .NET Framework, uygulamanızda sabit belgeler, akan belgeler ve genel metin kullanmayı kolaylaştıran önceden oluşturulmuş denetimler kümesi sağlar.  Sabit Belge içeriğinin görüntülenmesi <xref:System.Windows.Controls.DocumentViewer> denetimi kullanılarak desteklenir.  Flow belgesi içeriğinin görüntülenmesi üç farklı denetim tarafından desteklenir: farklı kullanıcı senaryolarıyla eşlenen <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> (aşağıdaki bölümlere bakın).  Diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri, genel metin kullanımlarını desteklemek için Basitleştirilmiş düzen sağlar (aşağıda, [Kullanıcı arabirimindeki metin](#text_in_the_user_interface)kısmına bakın).  
  
### <a name="fixed-document-control---documentviewer"></a>Sabit belge denetimi-DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer> denetimi <xref:System.Windows.Documents.FixedDocument> içeriğini görüntüleyecek şekilde tasarlanmıştır. <xref:System.Windows.Controls.DocumentViewer> denetimi, Yazdırma çıktısı, pano, yakınlaştırma ve metin arama özelliklerine kopyalama gibi yaygın işlemler için yerleşik destek sağlayan sezgisel bir kullanıcı arabirimi sağlar. Denetim, bildiğiniz bir kaydırma mekanizmasıyla içerik sayfalarına erişim sağlar. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri gibi, <xref:System.Windows.Controls.DocumentViewer> tamamen veya kısmi yeniden stillendirme destekler, bu da denetimin neredeyse tüm uygulama veya ortamla tümleşik olmasını sağlar.  
  
 <xref:System.Windows.Controls.DocumentViewer> içeriği salt bir şekilde görüntüleyecek şekilde tasarlanmıştır; içerik düzenlemesi veya değiştirilmesi kullanılamaz ve desteklenmez.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Akış belgesi denetimleri  

> [!NOTE]
> Akış belgesi özellikleri ve bunların nasıl oluşturulacağı hakkında daha ayrıntılı bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).  
  
 Flow belgesi içeriğini görüntüleme üç denetim tarafından desteklenir: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>, kullanıcının tek sayfalı (sayfa-bir zaman) görüntüleme modu, iki sayfalı bir-bir zaman (kitap okuma biçimi) görüntüleme modu ve sürekli kaydırma (bottomless) görüntüleme modu dahil çeşitli görüntüleme modları arasından dinamik olarak seçim kurmasını sağlayan özellikler içerir.  Bu görüntüleme modları hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Farklı görüntüleme modları arasında dinamik olarak geçiş yapma olanağına ihtiyacınız yoksa <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli bir görüntüleme modunda düzeltilen daha hafif akış içerik görüntüleyicilerini sağlar.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer ve FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>, sayfanın bir süre görüntüleme modunda, <xref:System.Windows.Controls.FlowDocumentScrollViewer> içeriği sürekli kaydırma modunda gösterdiği sırada gösterir.  <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> her ikisi de belirli bir görüntüleme moduna sabitlenmiştir. Kullanıcının çeşitli görüntüleme modları arasında (<xref:System.Windows.Controls.FlowDocumentReaderViewingMode> numaralandırması tarafından sağlandığı gibi) dinamik olarak seçmesini sağlayan özellikler içeren <xref:System.Windows.Controls.FlowDocumentReader>ile karşılaştırın <xref:System.Windows.Controls.FlowDocumentPageViewer> veya <xref:System.Windows.Controls.FlowDocumentScrollViewer>daha fazla kaynak kullanımı.  
  
 Varsayılan olarak, dikey bir kaydırma çubuğu her zaman gösterilir ve gerekirse yatay kaydırma çubuğu görünür hale gelir. <xref:System.Windows.Controls.FlowDocumentScrollViewer> için varsayılan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir araç çubuğu içermez; Ancak, <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özelliği yerleşik bir araç çubuğunu etkinleştirmek için kullanılabilir.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Kullanıcı arabirimindeki metin  
 Belgelere metin eklemenin yanı sıra metin, form gibi uygulama kullanıcı arabiriminde da kullanılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekrana metin çizme için birden çok denetim içerir. Her denetim farklı bir senaryoya yöneliktir ve kendi özellik ve kısıtlama listesine sahiptir. Genellikle, bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]kısa bir cümle gibi sınırlı metin desteği gerektiğinde <xref:System.Windows.Controls.TextBlock> öğesi kullanılmalıdır. <xref:System.Windows.Controls.Label>, en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için bkz. [TextBlock Overview](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Belge paketleme  
 <xref:System.IO.Packaging> API 'Leri, uygulama verilerini, belge içeriğini ve ilgili kaynakları kolay erişimli, taşınabilir ve dağıtımı kolay tek bir kapsayıcıda düzenlemek için etkili bir yol sağlar. ZIP dosyası, birden çok nesneyi tek bir birim olarak tutan <xref:System.IO.Packaging.Package> bir tür örneğidir. Paketleme API 'Leri, XML ve ZIP dosya mimarisiyle açık paketleme kuralları standardı kullanılarak tasarlanan varsayılan bir <xref:System.IO.Packaging.ZipPackage> uygulamasını sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paketleme API 'Leri, paketlerin oluşturulmasını ve içerdikleri nesneleri depolamak ve bunlara erişmek için basit hale getirir. <xref:System.IO.Packaging.Package> depolanan bir nesne, <xref:System.IO.Packaging.PackagePart> ("Bölüm") olarak adlandırılır. Paketler ayrıca bir bölümün kaynağını belirlemek ve bir paketin içeriğinin değiştirilmediğini doğrulamak için kullanılabilecek imzalı dijital sertifikalar içerebilir.  Paketler, ek bilgilerin bir pakete eklenmesine veya mevcut parçaların içeriğini değiştirmeden belirli bölümlerle ilişkilendirilmesine izin veren bir <xref:System.IO.Packaging.PackageRelationship> özelliği de içerir.  Paket Hizmetleri Microsoft Windows Rights Management (RM) da destekler.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paket mimarisi, bir dizi anahtar teknolojisinin temeli olarak görev yapar:  
  
- XML Kağıt Belirtimi (XPS) ile uyumlu XPS belgeleri.  
  
- "12" açık XML biçimli belgeleri (. docx) Microsoft Office.  
  
- Kendi uygulama tasarımınız için özel depolama biçimleri.  
  
 Paketleme API 'Lerine dayalı olarak, bir <xref:System.Windows.Xps.Packaging.XpsDocument>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sabit içerik belgelerinin depolanması için özel olarak tasarlanmıştır. <xref:System.Windows.Xps.Packaging.XpsDocument>, bir görüntüleyicide açılabilen, bir <xref:System.Windows.Controls.DocumentViewer> denetiminde görüntülenen, bir yazdırma kuyruğu 'na yönlendirilen veya doğrudan XPS uyumlu bir yazıcıya giden bir yazıcıda açılan bir belge olabilir.  
  
 Aşağıdaki bölümlerde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tarafından sunulan <xref:System.IO.Packaging.Package> ve <xref:System.Windows.Xps.Packaging.XpsDocument> API 'Leri hakkında ek bilgiler sağlanmaktadır.  
  
<a name="packages"></a>   
### <a name="package-components"></a>Paket bileşenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paketleme API 'Leri, uygulama verilerinin ve belgelerinin tek bir taşınabilir birimde düzenlenmesine izin verir. ZIP dosyası, en yaygın paket türlerinden biridir ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]birlikte sunulan varsayılan paket türüdür.  <xref:System.IO.Packaging.Package> kendisi, <xref:System.IO.Packaging.ZipPackage> açık standart XML ve ZIP dosya mimarisi kullanılarak uygulanmış olan soyut bir sınıftır.  <xref:System.IO.Packaging.Package.Open%2A> yöntemi, varsayılan olarak ZIP dosyalarını oluşturmak ve kullanmak için <xref:System.IO.Packaging.ZipPackage> kullanır. Bir paket, üç temel öğe türü içerebilir:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Uygulama içeriği, veriler, belgeler ve kaynak dosyaları.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|Tanımlama, kimlik doğrulama ve doğrulama için [X. 509.440 sertifikası].|  
|<xref:System.IO.Packaging.PackageRelationship>|Paketle veya belirli bir bölümden ilgili bilgiler eklendi.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 <xref:System.IO.Packaging.PackagePart> ("Part"), bir <xref:System.IO.Packaging.Package>depolanan bir nesneye başvuran bir soyut sınıftır. Bir ZIP dosyasında, paket parçaları ZIP dosyası içinde depolanan bireysel dosyalara karşılık gelir.  <xref:System.IO.Packaging.ZipPackagePart>, bir <xref:System.IO.Packaging.ZipPackage>depolanan serileştirilebilir nesneler için varsayılan uygulamayı sağlar.  Dosya sistemi gibi, pakette bulunan parçalar hiyerarşik dizinde veya "klasör stili" kuruluşta depolanır.  Uygulamalar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paketleme API 'Lerini kullanarak, tek bir ZIP dosya kapsayıcısını kullanarak birden çok <xref:System.IO.Packaging.PackagePart> nesnesini yazabilir, saklayabilir ve okuyabilir.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>Packagedigitalimzalarının  
 Güvenlik için bir <xref:System.IO.Packaging.PackageDigitalSignature> ("dijital imza"), bir paket içindeki bölümlerle ilişkilendirilebilir. <xref:System.IO.Packaging.PackageDigitalSignature> iki özellik sağlayan bir [509] içerir:  
  
1. Bölümünün kaynağını belirtir ve kimliğini doğrular.  
  
2. Bölümün değiştirilmediğini doğrular.  
  
 Dijital imza bir parçanın değiştirilmesini engellemez, ancak bölüm herhangi bir şekilde değiştirilirse dijital imzaya yönelik bir doğrulama denetimi başarısız olur. Uygulama daha sonra uygun eylemi gerçekleştirebilir — Örneğin, bölümü açmayı engelleme veya kullanıcıya parçanın değiştirildiğini ve güvenli olduğunu bildirme.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>Packagerelationsevk  
 <xref:System.IO.Packaging.PackageRelationship> ("ilişki"), ek bilgileri paket veya paket içindeki bir bölüm ile ilişkilendirmek için bir mekanizma sağlar. İlişki, gerçek bölüm içeriğini değiştirmeden ek bilgileri bir bölümüyle ilişkilendirebileceğiniz bir paket düzeyi tesisdir. ' In bölüm içeriğine doğrudan yeni veri eklemek genellikle pek çok durumda pratik değildir:  
  
- Bölümün gerçek türü ve içerik şeması bilinmiyor.  
  
- Bilinen bir deyişle, içerik şeması yeni bilgi eklemek için bir yol sunmayabilir.  
  
- Bölüm dijital olarak imzalanmış veya şifrelenmiş olabilir ve herhangi bir değişikliği daha fazla halledir.  
  
 Paket ilişkileri, farklı bölümlerle veya tüm paket ile ek bilgi ekleme ve ilişkilendirme için bulunabilir bir yol sağlar. Paket ilişkileri iki birincil işlev için kullanılır:  
  
1. Bir bölümden başka bir bölüme bağımlılık ilişkileri tanımlama.  
  
2. Bölüm ile ilgili notları veya diğer verileri ekleyen bilgi ilişkilerini tanımlama.  
  
 <xref:System.IO.Packaging.PackageRelationship>, bağımlılıkları tanımlamak ve paketin veya paketin bir bölümüyle ilişkili diğer bilgileri bir bütün olarak eklemek için hızlı, keşfedilebilir bir yol sağlar.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Bağımlılık Ilişkileri  
 Bağımlılık ilişkileri, bir bölümün diğer bölümlere yaptığı bağımlılıkları tanımlamakta kullanılır. Örneğin, bir paket bir veya daha fazla \<img > resim etiketi içeren bir HTML bölümü içerebilir. Görüntü etiketleri, paketin iç veya paketin dışında (Internet üzerinden erişilebilen gibi) diğer parçalar olarak bulunan görüntülere başvurur. HTML dosyası ile ilişkili bir <xref:System.IO.Packaging.PackageRelationship> oluşturmak, bağımlı kaynaklara hızlı ve kolay bir şekilde keşfve erişimi kolaylaştırır. Tarayıcı veya görüntüleyici uygulaması, Bölüm ilişkilerine doğrudan erişebilir ve şemayı bilmeden veya belgeyi ayrıştırmadan bağımlı kaynakları oluşturmaya hemen başlayabilir.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Bilgi Ilişkileri  
 Bir not veya ek açıklamasına benzer şekilde, Bölüm içeriğinin kendisini değiştirmek zorunda kalmadan bir bölüm ile ilişkilendirilecek diğer bilgi türlerini depolamak için de bir <xref:System.IO.Packaging.PackageRelationship> kullanılabilir.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS belgeleri  
 XML Kağıt Belirtimi (XPS) belgesi, işleme için gereken tüm kaynakları ve bilgileri içeren bir veya daha fazla sabit belge içeren bir pakettir.  XPS ayrıca yerel Windows Vista yazdırma biriktirme dosyası biçimidir.  Bir <xref:System.Windows.Xps.Packaging.XpsDocument> standart ZIP veri kümesinde depolanır ve resim ve yazı tipi dosyaları gibi XML ve ikili bileşenlerin bir birleşimini içerebilir. [Packagerelationsevk](#PackageRelationships) edilen içerik ve belgeyi tam olarak işlemek için gereken kaynaklar arasındaki bağımlılıkları tanımlamak için kullanılır.  <xref:System.Windows.Xps.Packaging.XpsDocument> tasarımı, birden çok kullanımı destekleyen tek ve yüksek uygunlukta bir belge çözümü sağlar:  
  
- Tek, taşınabilir ve dağıtımı kolay bir dosya olarak düzeltilen belge içeriğini ve kaynakları okuma, yazma ve depolama.  
  
- XPS Görüntüleyici uygulamasıyla belge görüntüleme.  
  
- Windows Vista 'nın yerel yazdırma kuyruğu çıkış biçiminde belge çıktısı.  
  
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
