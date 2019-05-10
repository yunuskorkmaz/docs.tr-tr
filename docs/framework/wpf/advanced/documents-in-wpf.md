---
title: WPF'deki Belgeler
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
ms.openlocfilehash: cdd0331ee8ffc664e9fbe04bd1494f1f7d714464
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663392"
---
# <a name="documents-in-wpf"></a>WPF'deki Belgeler
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çok çeşitli daha kolay erişilebilen ve önceki nesil içinde salt okunur olacak şekilde tasarlanan yüksek kaliteli içeriğinin oluşturulmasını belge özellikleri sunan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Gelişmiş Özellikler ve kalite, ek olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belge görüntüleme, paketleme ve güvenlik için tümleşik hizmetleri de sağlar. Bu konuda tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belge türleri ve belge paketleme.  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Belge türleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belgeleri, kullanım amaçlarına göre iki geniş kategoriye ayırır; Bu Belge kategorileri "sabit" ve "flow belgeler." olarak adlandırılır  
  
 Sabit belgeleri kesin bir gerektiren uygulamalar için hedeflenen [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] sunum, kullanılan görüntülemek ya da yazıcı donanımı bağımsız. Sabit belgeler için genel kullanımlar masaüstü yayıncılık ve sözcük işlem özgün sayfa tasarımı kıldığı kritik olduğu form düzenini içerir. Yerleşimi işleminin bir parçası olarak sabit bir belge görünen veya yazdırma cihazı kullanımda bağımsız olarak, içerik öğeleri kesin konumsal yerleşimini korur. 4800 DPI phototypesetter çıkışı olduğunda bunu 600 DPI lazer yazıcı için çıkış, örneğin, 96 DPI ekranda görüntülenen bir sabit belge sayfası tam olarak aynı görünür. Sayfa düzeni, belge kalitesini yeteneklerini her cihaz için en üst düzeye çıkarır ancak her durumda aynı kalır.  
  
 Buna karşılık olarak akış belgeleri görüntüleme ve okunabilirliği iyileştirmek için tasarlanmıştır ve Okuma Kolaylığı birincil belge tüketimi senaryo olduğunda en iyi şekilde kullanılır. Önceden tanımlanmış bir düzene ayarlanıyor, yerine akış belgeleri dinamik olarak ayarlama ve çalışma zamanı değişkenleri isteğe bağlı kullanıcı tercihlerini pencere boyutunu ve cihaz çözünürlüğü gibi temel alarak kendi içerik yeniden akışı. Bir Web sayfası bir basit bir akış belgesi burada sayfa içeriği dinamik olarak geçerli penceresine sığacak şekilde biçimlendirilir örneğidir. Akış belgeleri görüntüleme ve çalışma zamanı ortamı tabanlı kullanıcı deneyimini okuma iyileştirin. Örneğin, aynı akışı belge, yüksek çözünürlüklü 19-inch ekran veya küçük 2x3lük inç PDA ekranında en iyi okunabilirlik için dinamik olarak biçimlendirilmektedir. Ayrıca, akış belge özelliklerini görüntüleme okunabilirlik ve boyutunu ve yazı tipleri görünümünü değiştirme özelliği en iyi duruma modları, arama da dahil olmak üzere yerleşik bir dizi mevcuttur.  Bkz: [akış belgesine genel bakış](flow-document-overview.md) çizimler, örnekler ve akış belgeleri hakkında ayrıntılı bilgi için.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Belge denetimleri ve metin düzeni  
 .NET Framework, bir dizi sabit belgeleri, akış belgeleri ve genel metin uygulamanızın kullanımını kolaylaştıran önceden oluşturulmuş denetimler sağlar.  Sabit belge içeriğinin görünümünü kullanarak desteklenen <xref:System.Windows.Controls.DocumentViewer> denetimi.  Akış belgenin içerik görünümü, üç farklı denetimler tarafından desteklenir: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> eşlemek için farklı kullanıcı senaryoları (aşağıdaki bölümlere bakın).  Diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri sağlar genel metin desteklemek için basitleştirilmiş bir düzen kullanır (bkz [metin kullanıcı arabiriminde](#text_in_the_user_interface)aşağıdaki).  
  
### <a name="fixed-document-control---documentviewer"></a>DocumentViewer denetimi belge - düzeltildi  
 <xref:System.Windows.Controls.DocumentViewer> Denetim görüntülemek üzere tasarlanan <xref:System.Windows.Documents.FixedDocument> içeriği. <xref:System.Windows.Controls.DocumentViewer> Denetim yazdırma çıkış dahil olmak üzere sık kullanılan işlemler kopyalamak için Pano, yakınlaştırma ve metin arama özellikleri için yerleşik destek sağlayan bir sezgisel bir kullanıcı arabirimi sağlar. Denetim tanıdık bir kaydırma mekanizması aracılığıyla içerik sayfalarına erişimi sağlar. Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri <xref:System.Windows.Controls.DocumentViewer> destekleyen, tam veya kısmi yeniden tasarıma görsel olarak neredeyse tüm uygulama veya ortamla tümleştirilecek denetim sağlar.  
  
 <xref:System.Windows.Controls.DocumentViewer> salt okunur bir biçimde içeriği görüntülemek için tasarlanmıştır; düzenleme veya içerik değişikliği yok ve desteklenmiyor.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Akış belge denetimleri  
 **Not:** Akış belge özellikleri ve bunların nasıl oluşturulacağı hakkında daha ayrıntılı bilgi için bkz: [akış belgesine genel bakış](flow-document-overview.md).  
  
 Akış belgenin içerik görünümü, üç denetim tarafından desteklenir: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> dinamik olarak bir tek sayfa (sayfa--bir zamanda) görüntüleme modu, bir iki-sayfası--a-mod ve sürekli bir kayan (sınırsız) görüntüleme modunda görüntüleme zamanda (kitap Okuma biçimi) dahil olmak üzere çeşitli görüntüleme modları arasında seçim yapması sağlayan özellikler içerir.  Bu izleme modları hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Dinamik olarak farklı görüntüleme modları arasında geçiş yapma özelliğini gerekmiyorsa <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> hafifletilmiş akış belirli görüntüleme modunda sabit içerik görüntüleyicileri sağlar.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer and FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> içerik sayfası--bir zamanda içinde gösterir modu, görüntülerken <xref:System.Windows.Controls.FlowDocumentScrollViewer> sürekli kaydırma modunda içerik gösterir.  Her ikisi de <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli görüntüleme moduna düzeltildi. Karşılaştırılacak <xref:System.Windows.Controls.FlowDocumentReader>, dinamik olarak çeşitli görüntüleme modları arasında seçim yapması özellikleri içerir (tarafından sağlanan <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> numaralandırma), daha fazla kaynak yoğunluğu olan karşılığında <xref:System.Windows.Controls.FlowDocumentPageViewer> veya <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Varsayılan olarak, dikey bir kaydırma çubuğuna her zaman gösterilir ve yatay bir ScrollBar'ın gerektiğinde görünür duruma gelir. Varsayılan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için <xref:System.Windows.Controls.FlowDocumentScrollViewer> araç dahil değildir; ancak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özelliği, yerleşik bir araç çubuğu etkinleştirmek için kullanılabilir.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Kullanıcı arabiriminde metin  
 Metin belgeleri eklemenin yanı sıra, metin açıkça forms gibi uygulama kullanıcı Arabirimi kullanılabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekrana metnin çizmek için birden fazla denetim içerir. Her denetim için farklı bir senaryo hedeflenen ve kendi listesi özellikler ve sınırlamalar vardır. Genel olarak, <xref:System.Windows.Controls.TextBlock> öğesi sınırlı metin desteği kısa bir cümle gibi gerekli olduğunda kullanılmalıdır bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> en az metin desteği gerekli olduğunda kullanılabilir. Daha fazla bilgi için [TextBlock genel bakışı](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Belge paketleme  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Uygulama verileri, belge içeriğini ve taşınabilir ve dağıtımı kolay erişim için basit bir tek bir kapsayıcıda ilgili kaynakları düzenlemek için verimli bir yöntem sağlar. Bir ZIP dosyası örneğidir bir <xref:System.IO.Packaging.Package> türünde tek bir birim olarak birden çok nesne tutabilen. Paketleme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] varsayılan bir sağlamak <xref:System.IO.Packaging.ZipPackage> Open Packaging Conventions standart XML ve ZIP dosyası mimarisi ile kullanarak tasarlanmış uygulaması. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paketleme [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] paketler oluşturmak ve depolamak ve bunları nesnelerinde erişmek basit hale getirin. İçinde depolanan bir nesne bir <xref:System.IO.Packaging.Package> şeklinde adlandırılan bir <xref:System.IO.Packaging.PackagePart> ("Bölüm"). Paketler ayrıca gönderene bir bölümü, tanımlamak ve bir paket içeriğini değiştirilmemiş doğrulamak için kullanılan dijital olarak imzalanan sertifikaları içerir.  Paketleri de dahil bir <xref:System.IO.Packaging.PackageRelationship> bir pakete eklenen ya da mevcut bölümlerinin içeriğinin değiştirmeden belirli bölümleri ile ilgili ek bilgiler sağlayan özelliği.  Paket Hizmetleri ayrıca Destek [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paket mimarisi anahtar teknolojileri sayısı için temel olarak görev alır:  
  
- [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeler uyumludur [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
- "12" Microsoft Office open XML biçimi belgeleri (.docx).  
  
- Kendi uygulama tasarımı için özel depolama birimi biçimlendirir.  
  
 API'sine, temel bir <xref:System.Windows.Xps.Packaging.XpsDocument> depolamak için özel olarak tasarlanmıştır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik belgeleri düzeltildi. Bir <xref:System.Windows.Xps.Packaging.XpsDocument> görüntülenen bir Görüntüleyicisi ' nde açılabilen bir bağımsız birer belge olur bir <xref:System.Windows.Controls.DocumentViewer> için bir yazdırma biriktiricisi yönlendirilen veya doğrudan çıkış denetimi bir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-uyumlu yazıcı.  
  
 Aşağıdaki bölümlerde, ilgili ek bilgiler sağlar. <xref:System.IO.Packaging.Package> ve <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ile sağlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Paket bileşenleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Paketleme uygulama verilerini ve belgelerin bir taşınabilir ünite düzenlenir ve API'leri sağlar. Bir ZIP dosyası en sık karşılaşılan paketleri biridir ve varsayılan paket türü ile sağlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> kendisi, soyut bir sınıf olan <xref:System.IO.Packaging.ZipPackage> açık standart XML ve ZIP dosyası mimarisi kullanılarak uygulanır.  <xref:System.IO.Packaging.Package.Open%2A> Yöntemi kullanan <xref:System.IO.Packaging.ZipPackage> oluşturulur ve ZIP dosyaları varsayılan olarak kullanılır. Bir paket öğelerinin üç temel türleri içerebilir:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Uygulama içeriği, veri, belgeler ve kaynak dosyaları.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[X.509 sertifikası] tanımlama, kimlik doğrulaması ve doğrulama.|  
|<xref:System.IO.Packaging.PackageRelationship>|Paket veya özel bir bölümü ile ilgili bilgiler eklendi.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("") bir parçasıdır, depolanan bir nesneye başvuran bir Özet sınıf bir <xref:System.IO.Packaging.Package>. Bir ZIP dosyasında, paket bölümleri tek tek dosyaları ZIP dosyası içinde depolanan karşılık gelir.  <xref:System.IO.Packaging.ZipPackagePart> serileştirilebilir nesneler depolanan varsayılan uygulamasını sağlar bir <xref:System.IO.Packaging.ZipPackage>.  Bir dosya sistemi gibi pakette yer alan bölümleri hiyerarşik dizin veya "klasörü-style" kuruluş içinde depolanır.  Kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'leri paketleme, uygulamalar yazma, depolamak ve birden çok okuma <xref:System.IO.Packaging.PackagePart> tek bir ZIP dosyası kapsayıcısı kullanarak nesneleri.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Güvenlik için bir <xref:System.IO.Packaging.PackageDigitalSignature> ("dijital imzası") bir paket içindeki bölümleri ile ilişkili olabilir. A <xref:System.IO.Packaging.PackageDigitalSignature> [509] içererek, iki özellik sağlar:  
  
1. Tanımlar ve gönderene Bölümü'nün kimliğini doğrular.  
  
2. Bölümü değiştirilmemiş olduğunu doğrular.  
  
 Dijital imza bir bölümü değiştirilmesini değil, ancak bölümü herhangi bir şekilde değiştirilirse, bir dijital imza doğrulama denetimi başarısız olur. Uygulama ardından uygun eylemi gerçekleştirebilirsiniz — Örneğin, bölümün açılmasını engellemek veya bölümü değiştirilmiş ve güvenli olmayan kullanıcıya bildir.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("ilişkisi"), paket veya bir paket içindeki ek bilgileri ilişkilendirmek için bir mekanizma sağlar. Ek bilgi bölümü ile gerçek bölümü içeriğini değiştirmeden ilişkilendirebilirsiniz bir paket düzeyinde tesis ilişkidir. Yeni veri doğrudan bölümü içeriğini ekleme genellikle çoğu durumda pratik değildir:  
  
- Bölümü ve içerik şeması gerçek türü bilinmiyor.  
  
- Bilinen olsa bile, içerik şeması yeni bilgi eklemek için bir yol sağlamayabilir.  
  
- Bölümü dijital olarak olabilir imzalanmış veya şifrelenmiş, herhangi bir değişiklik çağrısı.  
  
 Paket ilişkileri ekleme ve ek bilgileri paketin tamamını veya tek tek bölümleri ile ilişkilendirmek için bulunabilirlik olanağı sağlar. Paket ilişkileri iki birincil işlevleri için kullanılır:  
  
1. Başka bir bölümü bir bölümünden bağımlılık ilişkileri tanımlama.  
  
2. Tanımlama bilgileri notları veya diğer veri bölümü için ilgili ekleme ilişkiler.  
  
 A <xref:System.IO.Packaging.PackageRelationship> bağımlılıkları tanımlayın ve bir paket veya paket bir bütün olarak parçası ile ilişkili diğer bilgileri eklemek için hızlı, keşfedilebilir bir yol sağlar.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Bağımlılık ilişkileri  
 Bağımlılık ilişkileri diğer bölümlerine bir parçası yapar bağımlılıklarını tanımlamak için kullanılır. Örneğin, bir paket birini veya daha fazlasını içeren HTML kısmının içerebilir \<img > görüntü etiketi. Görüntü etiketleri ya da diğer kısımlarıyla paketi için iç veya dış paketin bulunduğu görüntülerine bakın (gibi Internet üzerinden erişilebilir). Oluşturma bir <xref:System.IO.Packaging.PackageRelationship> keşfetme ve bağımlı kaynaklarını hızlı ve kolay erişim HTML dosyası yapar ile ilişkili. Bir tarayıcıyı veya Görüntüleyici uygulamasını bölümü ilişkileri doğrudan erişebilir ve şemayı bilmeden veya belge ayrıştırma ve bağımlı kaynaklarını derleyerek hemen başlayın.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Bilgi ilişkileri  
 Bir not ya da ek açıklama, benzer bir <xref:System.IO.Packaging.PackageRelationship> başka tür gerçekten bölümü içeriğini değiştirmek zorunda kalmadan bir bölümü ile ilişkilendirilecek bilgileri depolamak için de kullanılabilir.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>XPS belgeleri  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] Belge bir veya daha fazla sabit belgeleri yanı sıra tüm kaynakları ve işleme için gerekli bilgileri içeren bir pakettir.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Ayrıca yerel olan [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] yazdırma biriktiricisi dosya biçimi.  Bir <xref:System.Windows.Xps.Packaging.XpsDocument> standart ZIP kümesinde depolanır ve XML ve ikili bileşenleri, görüntü ve yazı tipi dosyaları gibi bir birleşimini içerebilir. [PackageRelationships](#PackageRelationships) içerik ve tam belgeyi işlemek için gereken kaynaklar arasındaki bağımlılıkları tanımlamak için kullanılır.  <xref:System.Windows.Xps.Packaging.XpsDocument> Tasarım birden fazla kullanımlar destekleyen tek, yüksek kaliteli bir belge çözümü sağlar:  
  
- Okuma, yazma ve sabit belge içerik ve kaynakları tek, taşınabilir ve kolay dağıtmak dosya olarak depolamak.  
  
- Belgelerle görüntüleme [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] görüntüleyici uygulaması.  
  
- Yerel yazdırma biriktiricisi belgelerde çıktısı, çıktı biçimi [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
- Yönlendirme belgeleri doğrudan bir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-uyumlu yazıcı.  
  
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
