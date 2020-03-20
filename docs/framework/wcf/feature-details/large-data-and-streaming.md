---
title: Büyük Veriler ve Akış Yapma
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 91e53f66fb0f2f94a315c318eb0b203d78427bae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184673"
---
# <a name="large-data-and-streaming"></a>Büyük Veriler ve Akış Yapma

Windows Communication Foundation (WCF) XML tabanlı bir iletişim altyapısıdır. XML verileri genellikle [XML 1.0 belirtiminde](https://www.w3.org/TR/REC-xml/)tanımlanan standart metin biçiminde kodlandığı için, bağlı sistem geliştiricileri ve mimarlar genellikle ağ üzerinden gönderilen iletilerin tel ayak izi (veya boyutu) ile ilgilidir ve XML'nin metin tabanlı kodlaması ikili verilerin verimli aktarımı için özel zorluklar oluşturur.  
  
## <a name="basic-considerations"></a>Temel Hususlar  
 WCF için aşağıdaki bilgiler hakkında arka plan bilgileri sağlamak için, bu bölümde, genellikle bağlı sistem altyapıları için geçerli olan kodlamalar, ikili veriler ve akış la ilgili bazı genel endişeler ve hususlar vurgulanır.  
  
### <a name="encoding-data-text-vs-binary"></a>Kodlama Verileri: Metin vs İkili  
 Yaygın olarak ifade edilen geliştirici endişeleri, xml'in başlangıç etiketleri ve bitiş etiketlerinin yinelenen doğası nedeniyle ikili biçimlerle karşılaştırıldığında önemli ek yükü olduğu, sayısal değerlerin kodlanmasının önemli ölçüde daha büyük olduğu algısını içerir metin değerleri yle ifade edildikleri ve ikili verilerin metin biçimine katıştırılması için özel olarak kodlanmaları gerektiğinden verimli bir şekilde ifade edilemeyeceği için.  
  
 Bu ve benzer kaygıların çoğu geçerli olmakla birlikte, XML Web hizmetleri ortamındaXML metin kodlanmış iletiler ile eski bir uzak yordam çağrısı (RPC) ortamındaki ikili kodlanmış iletiler arasındaki gerçek fark genellikle çok daha az ilk dikkate önerebilir.  
  
 XML-metin kodlanmış iletiler saydam ve "insan tarafından okunabilir" olsa da, ikili iletiler genellikle karşılaştırma da oldukça belirsizdir ve araçlar olmadan çözülmesi zordur. Okunabilirlikteki bu fark, ikili iletilerin genellikle yükte satır altı meta verileri taşıdığını göz ardı etmeye yol açar ve bu da xml metin iletilerinde olduğu gibi genel ek yük ekler. Bu, gevşek bağlantı ve dinamik çağırma özellikleri sağlamayı amaçlayan ikili biçimler için özellikle geçerlidir.  
  
 Ancak, ikili biçimler genellikle aşağıdaki veri kayıtları için veri düzenini bildiren bir "üstbilgi" içinde bu tür açıklayıcı meta veri bilgilerini taşır. Taşıma daha sonra bu ortak meta veri bloğu bildirimini en az ek yük ile izler. Bunun aksine, XML her veri öğesini bir öğeye veya öznitelike içine, böylece çevreleyen meta verilerin her serileştirilmiş yük nesnesi için tekrar tekrar dahil edilir. Sonuç olarak, bazı açıklayıcı meta veriler her ikisi için de ifade edilmesi gerektiğinden, tek bir serileştirilmiş yük nesnesinin boyutu, metinle ikili gösterimlerle karşılaştırıldığında benzerdir, ancak ikili biçim her ek ile paylaşılan meta veri açıklamasından yararlanır daha düşük genel ek yük nedeniyle aktarılan yük nesnesi.  
  
 Yine de, sayılar gibi belirli veri türleri için, düz metin gösterimi birkaç bayt daha küçük olabileceğinden, düz metin gösterimi yerine 128 bit ondalık yazı gibi sabit boyutlu, ikili sayısal gösterimler kullanmanın bir dezavantajı olabilir. Metin verilerinin genellikle daha esnek XML metin kodlama seçeneklerinden boyut avantajları olabilir, ancak bazı ikili biçimler .NET İkili XML Biçimi için geçerli olmayan 16 bit ve hatta 32 bit Unicode varsayılan olarak varsayılan olabilir.  
  
 Sonuç olarak, metin veya ikili arasında karar vermek, ikili iletilerin her zaman XML-metin iletilerinden daha küçük olduğunu varsaymak kadar kolay değildir.  
  
 XML metin mesajlarının açık bir avantajı, standartlara dayalı olmaları ve en geniş birlikte çalışabilirlik seçenekleri ve platform desteği seçenekleri sunabildikleridir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Kodlamalar" bölümüne bakın.  
  
### <a name="binary-content"></a>İkili İçerik  
 İkili kodlamaların, ortaya çıkan ileti boyutu açısından metin tabanlı kodlamalardan daha üstün olduğu bir alan, resimler, videolar, ses klipleri veya hizmetler ile bunların arasında değiş tokuş edilmesi gereken herhangi bir opak, ikili veri biçimi gibi büyük ikili veri öğeleridir. Tüketici. Bu tür verileri XML metnine sığdırmak için ortak yaklaşım, bunları Base64 kodlamasını kullanarak kodlamaktır.  
  
 Base64 kodlanmış bir dizede, her karakter orijinal 8-bit verilerin 6 bitini temsil eder ve bu da Base64 için 4:3 kodlama ek yükü oranıyla sonuçlanır ve genellikle kural kuralı tarafından eklenen ek biçimlendirme karakterlerini (satır başı/satır akışı) saymaz. XML ve ikili kodlamalar arasındaki farkların önemi genellikle senaryoya bağlı olsa da, 500 MB'lık bir yükü aktarırken %33'ten fazla bir boyut kazancı genellikle kabul edilemez.  
  
 Bu kodlama yükü önlemek için, İleti Aktarım Optimizasyonu Mekanizması (MTOM) standardı, iletide bulunan büyük veri öğelerini dışsallaştırmaya ve iletiyle birlikte herhangi bir özel kodlama olmaksızın ikili veri olarak taşımaya olanak tanır. MTOM ile iletiler, ekleri veya gömülü içerik (resimler ve diğer katıştırılmış içerik) içeren Basit Posta Aktarım Protokolü (SMTP) e-posta iletilerine benzer şekilde değiştirilir; MTOM iletileri çok parçalı/ilişkili MIME dizileri olarak paketlenir ve kök kısmı gerçek SOAP iletisi dir.  
  
 Bir MTOM SOAP iletisi, kodlanmamış sürümünden değiştirilir, böylece ilgili MIME parçalarına başvuran özel öğe etiketleri ikili veri içeren iletideki özgün öğelerin yerini alır. Sonuç olarak, SOAP iletisi onunla gönderilen MIME parçaları işaret ederek ikili içerik anlamına gelir, ama aksi takdirde sadece XML metin verileri taşır. Bu model iyi kurulmuş SMTP modeliyle yakından uyumlu olduğundan, birçok platformda MTOM iletilerini kodlamak ve çözmek için geniş bir araç desteği vardır, bu da onu son derece birlikte çalışabilir bir seçim yapar.  
  
 Yine de, Base64'te olduğu gibi, MTOM da MIME formatı için gerekli bazı ek yükü ile birlikte gelir, böylece MTOM kullanmanın avantajları yalnızca ikili veri elemanının boyutu yaklaşık 1 KB'yi aştığında görülür. Genel ek yük nedeniyle, ikili yük bu eşiğin altında kalırsa, MTOM kodlu iletiler ikili veriler için Base64 kodlamasını kullanan iletilerden daha büyük olabilir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Kodlamalar" bölümüne bakın.  
  
### <a name="large-data-content"></a>Büyük Veri İçeriği  
 Tel ayak izi bir yana, daha önce bahsedilen 500 MB'lık yük de hizmet ve istemci için büyük bir yerel sorun teşkil etmektedir. Varsayılan olarak, WCF iletileri *arabelleğe alınan modda*işler. Bu, iletinin tüm içeriğinin gönderilmeden önce veya alındıktan sonra bellekte bulunduğu anlamına gelir. Bu çoğu senaryo için iyi bir strateji olsa da ve dijital imzalar ve güvenilir teslim gibi mesajlaşma özellikleri için gerekli olsa da, büyük iletiler bir sistemin kaynaklarını tüketebilir.  
  
 Büyük yüklerle başa çıkma stratejisi akıyor. İletiler, özellikle XML'de ifade edileniletiler genellikle nispeten kompakt veri paketleri olarak düşünülse de, iletinin boyutu birden çok gigabayt olabilir ve bir veri paketinden daha fazla sürekli veri akışına benzeyebilir. Veriler arabelleğe alınan mod yerine akış modunda aktarıldığında, gönderen ileti gövdesinin içeriğini akış biçiminde alıcının kullanımına gönderir ve ileti altyapısı verileri gönderenden alıcıya sürekli olarak iletir Kullanılabilir.  
  
 Bu tür büyük veri içerik aktarımlarının gerçekleştiği en yaygın senaryo, ikili veri nesnelerinin aktarımlarıdır:  
  
- İleti dizisine kolayca bölünemez.  
  
- Zamanında teslim edilmelidir.  
  
- Aktarım başlatıldığında bunların bütünüyle kullanılamaz.  
  
 Bu kısıtlamalara sahip olmayan veriler için, genellikle bir büyük iletiyerine bir oturum kapsamında ileti dizileri göndermek daha iyidir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Veri Akışı" bölümüne bakın.  
  
 Büyük miktarda veri `maxAllowedContentLength` gönderirken IIS ayarını (daha fazla bilgi için [IIS İstek Limitlerini Yapılandırmaya](https://docs.microsoft.com/iis/configuration/system.webServer/security/requestFiltering/requestLimits/)bakın) ve `maxReceivedMessageSize` bağlayıcı ayarı (örneğin <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A> [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) veya) ayarlamanız gerekir. Özellik `maxAllowedContentLength` varsayılan olarak 28,6 MB `maxReceivedMessageSize` ve özellik varsayılan olarak 64KB'dir.  
  
## <a name="encodings"></a>Kodlamalar  
 *Kodlama,* iletilerin kabloya nasıl sunulacağını anlatan bir dizi kural tanımlar. Bir *kodlayıcı* böyle bir kodlama yı uygular ve gönderen tarafında, bellek <xref:System.ServiceModel.Channels.Message> içi bir akışın veya ağ üzerinden gönderilebilen bayt arabelleğine dönüştürülmesinden sorumludur. Alıcı tarafında, kodlayıcı bir bayt dizisini bellek içi iletiye dönüştürür.  
  
 WCF üç kodlayıcı içerir ve gerekirse kendi kodlayıcılarınızı yazmanızı ve takmanızı sağlar.  
  
 Standart bağlamaların her biri önceden yapılandırılmış bir kodlayıcı içerir, böylece Net* önekiile bağlanan bağlayıcılar ikili <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> kodlayıcıyı <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WSHttpBinding> (sınıfı dahil ederek) kullanırken, sınıflar <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> metin iletisi kodlayıcısını (sınıf aracılığı ile) varsayılan olarak kullanır.  
  
|Kodlayıcı bağlama öğesi|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Metin iletisi kodlayıcısı, tüm HTTP tabanlı bağlamalar için varsayılan kodlayıcıdır ve birlikte çalışabilirliğin en yüksek sorun olduğu tüm özel bağlamalar için uygun seçimdir. Bu kodlayıcı, ikili veriler için özel bir işlem olmadan standart SOAP 1.1/SOAP 1.2 metin mesajlarını okur ve yazar. Bir <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> iletinin özelliği <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>, SOAP zarf sarıcı çıktıdan atlanır ve yalnızca ileti gövdesi içeriği seri hale getirilmiştir.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|MTOM ileti kodlayıcısı, ikili veriler için özel işleme uygulayan bir metin kodlayıcısıdır ve standart bağlamaların hiçbirinde varsayılan olarak kullanılmaz, çünkü bu kesinlikle tek tek optimizasyon yardımcı programıdır. İleti, MTOM kodlamasının bir yarar sağladığı bir eşiği aşan ikili veri içeriyorsa, veriler ileti zarfını izleyen bir MIME bölümüne dışsallaştırılır. Daha sonra bu bölümde MTOM'u etkinleştirme bölümüne bakın.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|İkili ileti kodlayıcısı, Net* bağlamaları için varsayılan kodlayıcıdır ve her iki iletişim tarafı wcf'ye dayalı olduğunda uygun seçimdir. İkili ileti kodlayıcısı, xml bilgi kümeleri (Bilgi Kümeleri) için Microsoft'a özgü bir ikili gösterim olan ve genellikle eşdeğer XML 1.0 gösteriminden daha küçük bir ayak izi sağlayan ve ikili verileri bayt olarak kodlayan .NET İkili XML Biçimini kullanır Akışı.|  
  
 Metin iletisi kodlaması genellikle birlikte çalışabilirlik gerektiren herhangi bir iletişim yolu için en iyi seçimdir, ikili ileti kodlaması ise diğer iletişim yolu için en iyi seçimdir. İkili ileti kodlaması genellikle tek bir iletinin metniyle karşılaştırıldığında daha küçük ileti boyutları ve iletişim oturumu süresince giderek daha küçük ileti boyutları verir. Metin kodlamanın aksine, ikili kodlama, Base64'ü kullanmak gibi ikili veriler için özel işleme kullanmak zorunda değildir, ancak baytları bayt olarak temsil eder.  
  
 Çözümünüz birlikte çalışabilirlik gerektiriyorsa, ancak yine de HTTP aktarımını <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> kullanmak istiyorsanız, taşıma <xref:System.ServiceModel.Channels.HttpTransportBindingElement> için sınıfı kullanan özel bir bağlama oluşturabilirsiniz. Hizmetinizdeki birkaç istemci birlikte çalışabilirlik gerektiriyorsa, her birinin etkinleştirilen ilgili istemciler için uygun aktarım ve kodlama seçeneklerine sahip olduğu paralel uç noktaları ortaya çıkarmanız önerilir.  
  
### <a name="enabling-mtom"></a>MTOM'u etkinleştirme  
 Birlikte çalışabilirlik bir gereklilik olduğunda ve büyük ikili verilerin gönderilmesi gerektiğinde, <xref:System.ServiceModel.BasicHttpBinding> MTOM ileti kodlaması, <xref:System.ServiceModel.WSHttpBinding> ilgili `MessageEncoding` özelliği <xref:System.ServiceModel.WSMessageEncoding.Mtom> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> bir . <xref:System.ServiceModel.Channels.CustomBinding> MTOM Kodlama örneğinden çıkarılan aşağıdaki örnek kod, Yapılandırmada [MTOM'un](../../../../docs/framework/wcf/samples/mtom-encoding.md) nasıl etkinleştirilen olduğunu gösterir.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <wsHttpBinding>  
        <binding name="ExampleBinding" messageEncoding="Mtom"/>  
      </wsHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Daha önce de belirtildiği gibi, MTOM kodlamasını kullanma kararı gönderdiğiniz veri hacmine bağlıdır. Ayrıca, MTOM bağlama düzeyinde etkinleştirildiğinden, MTOM'un belirli bir bitiş noktasındaki tüm işlemleri etkilemesini sağlar.  
  
 MTOM kodlayıcısı, ikili verilerin dışsallaştırılıp sonuçlanmadığına bakılmaksızın her zaman MTOM kodlu bir MIME/çok parçalı ileti yayan lardan, genellikle yalnızca 1 KB'den fazla ikili veri ile ileti alışverişinde bulunan uç noktalar için MTOM'u etkinleştirmelisiniz. Ayrıca, MTOM özellikli uç noktalarıyla kullanılmak üzere tasarlanmış hizmet sözleşmeleri, mümkün olduğunda bu tür veri aktarım işlemlerini belirtmekle sınırlandırılmalıdır. İlgili denetim işlevselliği ayrı bir sözleşmede yer almalıdır. Bu "Yalnızca MTOM" kuralı yalnızca MTOM etkin bir bitiş noktası üzerinden gönderilen iletiler için geçerlidir; MTOM kodlayıcısı gelen MTOM olmayan iletileri de çözebilir ve ayrıştabilir.  
  
 MTOM kodlayıcının kullanılması diğer tüm WCF özellikleriyle uyumlu. Oturum desteğinin gerekli olduğu durumlar gibi tüm durumlarda bu kurala uymanın mümkün olmayabileceğini unutmayın.  
  
### <a name="programming-model"></a>Programlama Modeli  
 Uygulamanızda kullandığınız üç yerleşik kodlayıcıdan hangisiolursa olsun, programlama deneyimi ikili veri aktarımı açısından aynıdır. Fark, WCF'nin verileri veri türlerine göre nasıl işlediğidir.  
  
```csharp
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}
```  
  
 MTOM kullanılırken, önceki veri sözleşmesi aşağıdaki kurallara göre seri hale getirilir:  
  
- Base64 kodlaması ile karşılaştırıldığında MTOM dışsallaştırma yükü (MIME üstbilgileri vb.) haklı çıkarmak için yeterli veri `binaryBuffer` içermiyorsa `null` ve tek tek içeriyorsa, veriler dışsallaştırılır ve iletiyle ikili MIME parçası olarak taşınır. Eşik aşıldığında, veriler Base64 olarak kodlanır.  
  
- Dize (ve ikili olmayan diğer tüm türler) boyutu ne olursa olsun, her zaman ileti gövdesi içinde bir dize olarak temsil edilir.  
  
 MTOM kodlamaüzerindeki etkisi, önceki örnekte gösterildiği gibi açık bir veri sözleşmesi kullanıp kullanmadığınız, bir işlemde parametre listesi kullansanız, veri sözleşmelerini iç içe mi yoksa bir veri sözleşmesi nesnesini bir koleksiyona aktarSanız aynıdır. Bayt dizileri her zaman optimizasyon için adaydır ve optimizasyon eşikleri karşılanıyorsa en iyi duruma getirilir.  
  
> [!NOTE]
> Veri sözleşmeleri içinde <xref:System.IO.Stream?displayProperty=nameWithType> türetilmiş türleri kullanmamalısınız. Akış verileri aşağıdaki "Veri Akışı" bölümünde açıklanan akış modeli kullanılarak iletilmelidir.  
  
## <a name="streaming-data"></a>Veri Akışı  
 Aktarım için büyük miktarda veri varsa, WCF'deki akış aktarım modu, iletileri bellekte tümüyle arabelleğe alma ve işleme varsayılan davranışına uygun bir alternatiftir.  
  
 Daha önce de belirtildiği gibi, veriler bölümlere ayrılamıyorsa, iletizamanında teslim edilmesi gerekiyorsa veya aktarım başlatıldığında veriler henüz tam olarak kullanılamıyorsa, yalnızca büyük iletiler (metin veya ikili içerikli) için akışı etkinleştirin.  
  
### <a name="restrictions"></a>Kısıtlamalar  
 Akış etkinleştirildiğinde önemli sayıda WCF özelliği kullanamazsınız:  
  
- İleti gövdesi için dijital imzalar gerçekleştirilemez, çünkü tüm ileti içeriği üzerinde bir karma bilgisayar gerektirir. Akış la birlikte, ileti üstbilgisi oluşturulduğunda ve gönderildiğinde içerik tam olarak kullanılamaz ve bu nedenle dijital imza hesaplanamaz.  
  
- Şifreleme, verilerin doğru şekilde yeniden oluşturuldurıldığını doğrulamak için dijital imzalara bağlıdır.  
  
- İleti transferde kaybolursa, güvenilir oturumlar istemciye gönderilen iletileri yeniden teslim etmek üzere arabelleğe almalı ve iletilerin alınması durumunda ileti siparişini korumak için hizmet uygulamasına teslim etmeden önce iletileri hizmette tutmalı sıra dışı.  
  
 Bu işlevsel kısıtlamalar nedeniyle, akış için yalnızca aktarım düzeyinde güvenlik seçeneklerini kullanabilirsiniz ve güvenilir oturumları açamazsınız. Akış yalnızca aşağıdaki sistem tanımlı bağlamalarla kullanılabilir:  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 Temel taşımalar <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> http aksine, doğal güvenilir teslimat ve bağlantı tabanlı oturum desteği olduğundan, bu iki bağlama pratikte, bu kısıtlamalar sadece en az etkilenir.  
  
 İleti Sıralaması (MSMQ) aktarımı ile akış kullanılamaz ve bu <xref:System.ServiceModel.NetMsmqBinding> nedenle <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıf la kullanılamaz. İleti Sıraya aktarımı yalnızca kısıtlı ileti boyutuyla arabelleğe alınan veri aktarımlarını desteklerken, diğer tüm aktarımların senaryoların büyük çoğunluğu için herhangi bir pratik ileti boyutu sınırı yoktur.  
  
 Eş Kanal aktarımını kullanırken akış da kullanılamıyor, <xref:System.ServiceModel.NetPeerTcpBinding>bu nedenle .  
  
#### <a name="streaming-and-sessions"></a>Akış ve Oturumlar  
 Oturum tabanlı bağlama yla çağrıları akışa aktarırken beklenmeyen davranışlar alabilirsiniz. Tüm akış çağrıları, kullanılan bağlama oturumları kullanmak üzere yapılandırılan olsa bile oturumları desteklemeyen tek bir kanal (datagram kanalı) üzerinden yapılır. Birden çok istemci oturum tabanlı bağlama üzerinden aynı hizmet nesnesine akış çağrıları yaparsa ve hizmet nesnesinin eşzamanlılık modu tek olarak ayarlanmışsa ve örnek bağlam modu PerSession olarak ayarlanmışsa, tüm aramalar datagram kanalından geçmelidir ve bu nedenle yalnızca bir arama bir defada işlenir. Bir veya daha fazla istemci daha sonra zaman dışarı olabilir. Bu sorunu, hizmet nesnesinin Örnek Bağlam Modu'nu PerCall'a veya Eşzamanlılık Modunu Çoklu'ya ayarlayarak çözebilirsiniz.  
  
> [!NOTE]
> Yalnızca bir "oturum" olduğundan MaxConcurrentSessions bu durumda hiçbir etkisi vardır.  
  
### <a name="enabling-streaming"></a>Akışı Etkinleştirme  
 Akışı aşağıdaki yollarla etkinleştirebilirsiniz:  
  
- Akış modunda istek gönderme ve kabul et ve arabelleğe<xref:System.ServiceModel.TransferMode.StreamedRequest>alma modunda yanıtları kabul edip iade eder ( ).  
  
- Arabelleğe alma modunda istek gönderme ve kabul et ve<xref:System.ServiceModel.TransferMode.StreamedResponse>akışları akış modunda yanıtları kabul edip döndür ( ).  
  
- Her iki yönde de akış modunda istek ve yanıt gönderin ve alın. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Tüm bağlamaların varsayılan ayarı olan <xref:System.ServiceModel.TransferMode.Buffered>aktarım modunu (tüm bağlamalar için varsayılan ayar) ayarlayarak akışı devre dışı kullanabilirsiniz. Aşağıdaki kod, yapılandırmada aktarım modunun nasıl ayarlanır olduğunu gösterir.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streamed"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Parolayla bağlamanızı anında yaptığınızda, bağlamanın ilgili `TransferMode` özelliğini (veya özel bir bağlama oluşturuyorsanız aktarım bağlama öğesi) daha önce belirtilen değerlerden birine ayarlamanız gerekir.  
  
 İstek ler ve yanıtlar için veya her iki yönde de işlevselliği etkilemeden iletişim taraflarının her iki tarafında bağımsız olarak akış açabilirsiniz. Ancak, aktarılan veri boyutunun, bir iletişim bağlantısının her iki uç noktasında da akışı etkinleştirmek için çok önemli olduğunu varsaymalısınız. Uç noktalardan birinin WCF ile uygulanmadığı çapraz platform iletişimi için, akış kullanma yeteneği platformun akış özelliklerine bağlıdır. Başka bir nadir özel durum, istemci veya hizmetin çalışma kümesini en aza indirmesi gereken ve yalnızca küçük arabellek boyutlarını karşılayabileceği bellek tüketimine dayalı bir senaryo olabilir.  
  
### <a name="enabling-asynchronous-streaming"></a>Eşzamanlı Akışı Etkinleştirme  
 Eşzamanlı akışı etkinleştirmek için, <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> bitiş noktası davranışını hizmet ana <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> bilgisayara ekleyin ve özelliğini '' olarak `true`ayarlayın. Ayrıca, gönder tarafında gerçek asynchronous akış yeteneğini de ekledik. Bu, bazıları ağ tıkanıklığı nedeniyle okumada yavaş olan veya hiç okumayan birden çok istemciye ileti akışı yaptığı senaryolarda hizmetin ölçeklenebilirliğini artırır. Bu senaryolarda artık istemci başına hizmetteki tek tek iş parçacıklarını engellemeyiz. Bu, hizmetin çok daha fazla istemciyi işleme sini sağlayarak hizmetin ölçeklenebilirliğini artırmasını sağlar.  
  
### <a name="programming-model-for-streamed-transfers"></a>Akışlı Aktarımlar için Programlama Modeli  
 Akış için programlama modeli basittir. Akışlı verileri almak için, tek <xref:System.IO.Stream> bir daktilile giriş parametresi olan bir işlem sözleşmesi belirtin. Akışlı verileri döndürmek için <xref:System.IO.Stream> bir başvuru döndürün.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamedService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
    [OperationContract]  
    Stream RequestInfo(string query);  
    [OperationContract(OneWay=true)]  
    void ProvideInfo(Stream data);  
}  
```  
  
 Önceki `Echo` örnekteki işlem bir akış alır ve döndürür ve <xref:System.ServiceModel.TransferMode.Streamed>bu nedenle bir bağlama kullanılmalıdır . Operasyon `RequestInfo`için, <xref:System.ServiceModel.TransferMode.StreamedResponse> en uygun, çünkü sadece <xref:System.IO.Stream>bir . Tek yönlü işlem için en <xref:System.ServiceModel.TransferMode.StreamedRequest>uygun.  
  
 Aşağıdaki `Echo` veya `ProvideInfo` işlemlere ikinci bir parametre eklenmesinin hizmet modelinin arabelleğe geçmiş bir stratejiye geri dönmesine ve akışın çalışma zamanı serileştirme gösterimini kullanmasına neden olduğunu unutmayın. Yalnızca tek bir giriş akışı parametresi olan işlemler uçtan uca istek akışıyla uyumludur.  
  
 Bu kural benzer şekilde ileti sözleşmeleri için de geçerlidir. Aşağıdaki ileti sözleşmesinde gösterildiği gibi, ileti sözleşmenizde akış olan yalnızca tek bir gövdeli üyeniz olabilir. Akışla ek bilgi iletmek istiyorsanız, bu bilgilerin ileti üstbilgileri nde taşınması gerekir. İleti gövdesi yalnızca akış içeriği için ayrılmıştır.  
  
```csharp
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}
```  
  
 Akışak aktarımları sona erer ve akış dosyanın sonuna (EOF) ulaştığında ileti kapatılır. İleti gönderirken (bir değer döndürerek veya bir işlemi <xref:System.IO.FileStream> çağırırken), bir geçişi geçebilir ve WCF altyapısı, akış tamamen okunup EOF'ye ulaşana kadar bu akıştaki tüm verileri çeker. Önceden oluşturulmuş <xref:System.IO.Stream> türemiş bir sınıfın bulunmadığı kaynak için akışlı veri aktarmak için, böyle bir sınıf oluşturmak, akış kaynağınızın üzerine o sınıfı bindirme ve bunu bağımsız değişken veya iade değeri olarak kullanın.  
  
 Bir ileti alırken, WCF Base64 kodlanmış ileti gövdesi içeriği (veya MTOM kullanıyorsanız ilgili MIME bölümü) üzerinde bir akış oluşturuyor ve içerik okunduğunda akış EOF'ye ulaşıyor.  
  
 Aktarım düzeyi akışı, diğer ileti sözleşmesi türüyle (parametre listeleri, veri sözleşmesi bağımsız değişkenleri ve açık ileti sözleşmesi) da çalışır, ancak bu tür tür iletilerin serileştirilmesi ve deserializasyonu serileştirici tarafından arabelleğe alma gerektirdiğinden , bu tür sözleşme türevlerini kullanmak tavsiye edilmez.  
  
### <a name="special-security-considerations-for-large-data"></a>Büyük Veriler için Özel Güvenlik Hususları  
 Tüm bağlamalar, hizmet reddi saldırılarını önlemek için gelen iletilerin boyutunu kısıtlamanızı sağlar. Örneğin, <xref:System.ServiceModel.BasicHttpBinding>gelen iletinin boyutunu sınırlayan bir [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) özelliğini ortaya çıkarır ve böylece iletiyi işlerken erişilen maksimum bellek miktarını da sınırlar. Bu birim, varsayılan değeri 65.536 bayt olan baytolarak ayarlanır.  
  
 Büyük veri akışı senaryosuna özgü bir güvenlik tehdidi, alıcı akışı istediğinde verilerin arabelleğe alınmasına neden olarak hizmet reddine neden olur. Örneğin, WCF her zaman bir iletinin SOAP üstbilgilerini arabelleğe alır ve bu nedenle saldırgan, verilerin arabelleğe alınmasına zorlamak için tamamen üstbilgilerden oluşan büyük bir kötü amaçlı ileti oluşturabilir. Akış etkinleştirildiğinde, `MaxReceivedMessageSize` alıcı iletinin tamamının bellekte aynı anda arabelleğe alınmasını beklemediği için, son derece büyük bir değere ayarlanabilir. WCF iletiyi arabelleğe almaya zorlanırsa, bellek taşması oluşur.  
  
 Bu nedenle, bu durumda gelen en büyük ileti boyutunu kısıtlamak yeterli değildir. Özellik, `MaxBufferSize` WCF arabelleklerini kısıtlayan belleği kısıtlamak için gereklidir. Akış sırasında bunu güvenli bir değere (veya varsayılan değerde tutmak) ayarlamak önemlidir. Örneğin, hizmetinizin 4 GB boyutuna kadar dosyaları alması ve bunları yerel diskte depolaması gerektiğini varsayalım. Ayrıca, belleğinizin aynı anda yalnızca 64 KB veri arabelleğe alabileceğiniz şekilde kısıtlanmış olduğunu da varsayalım. Sonra 4 GB `MaxReceivedMessageSize` ve `MaxBufferSize` 64 KB ayarlamak istiyorsunuz. Ayrıca, hizmet uygulamanızda, yalnızca 64-KB'lik parçalar halinde gelen akıştan okuduğunuzdan emin olmalısınız ve bir önceki parça diske yazılmadan ve bellekten atılmadan önce bir sonraki parçayı okumamalısınız.  
  
 Bu kotanın yalnızca WCF tarafından yapılan arabelleğe alma alanını sınırladığını ve kendi hizmetinizde veya istemci uygulamanızda yaptığınız herhangi bir arabelleğe alma yla sizi koruyamayacağını da anlamak önemlidir. Ek güvenlik konuları hakkında daha fazla bilgi için, [Veriler için Güvenlik Hususları'na](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)bakın.  
  
> [!NOTE]
> Arabelleğe alınan veya akışlı aktarımları kullanma kararı bitiş noktasının yerel bir kararıdır. HTTP aktarımları için aktarım modu bir bağlantı boyunca veya proxy sunucuları ve diğer aracılara yayılmaz. Aktarım modunun ayarlanması hizmet arabiriminin açıklamasına yansıtılmaz. Bir hizmete bir WCF istemcisi sağladıktan sonra, modu ayarlamak için akışlı aktarımlarla kullanılmak üzere tasarlanmış hizmetler için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış boru aktarımları için aktarım modu bir ilke iddiası olarak yayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
