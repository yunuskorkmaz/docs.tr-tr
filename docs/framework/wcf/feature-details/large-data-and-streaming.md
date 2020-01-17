---
title: Büyük Veriler ve Akış Yapma
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 5719f941c71867699960c6029f9cc512021986f3
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212201"
---
# <a name="large-data-and-streaming"></a>Büyük Veriler ve Akış Yapma

Windows Communication Foundation (WCF), XML tabanlı bir iletişim altyapısıdır. XML verileri yaygın olarak [xml 1,0 belirtiminde](https://www.w3.org/TR/REC-xml/)tanımlanan standart metin biçiminde kodlandığı için, bağlı sistemler geliştiricileri ve mimarları, genellikle ağ üzerinden gönderilen iletilerin Tel kaplama (veya boyutu) ile ILGILIDIR ve XML 'nin metin tabanlı kodlaması, ikili verilerin verimli bir şekilde aktarılması için özel zorluk sağlar.  
  
## <a name="basic-considerations"></a>Temel konular  
 WCF için aşağıdaki bilgiler hakkında arka plan bilgileri sağlamak için bu bölümde, genellikle bağlı sistem altyapılarına uygulanan kodlamalar, ikili veriler ve akışa yönelik bazı genel sorunlar ve önemli noktalar vurgulanmıştır.  
  
### <a name="encoding-data-text-vs-binary"></a>Kodlama verileri: metin ile Ikili  
 Yaygın olarak ifade edilen geliştirici sorunları, başlangıç etiketlerinin ve bitiş etiketlerinin yinelenen doğası nedeniyle XML 'nin önemli ölçüde ek yüke neden olduğu konusunda, sayısal değerler kodlamasının büyük ölçüde daha büyük olduğu kabul edilir Bunlar metin değerlerinde ifade edildiğinden ve bu ikili veriler etkin bir şekilde ifade edilemediğinden, metin biçiminde katıştırılması için özel olarak kodlanmalıdır.  
  
 Bu ve benzer kaygılardan birçoğu geçerli olsa da, bir XML Web Hizmetleri ortamındaki XML metin kodlamalı iletiler ve eski bir uzak yordam çağrısı (RPC) ortamındaki ikili kodlu iletiler arasındaki gerçek fark, genellikle bu değerden çok daha az önem taşıyor ilk değerlendirme önergelebilir.  
  
 XML metin kodlamalı iletiler saydam ve "insanlar okunabilir" olsa da, ikili iletiler genellikle büyük bir şekilde karşılaştırılmakta ve araç olmadan çözülmesi zor olur. Okunabilirliği içinde bu fark, tek bir deyişle, ikili iletilerin, genellikle XML metin iletileriyle olduğu gibi ek yük ekleyen satır içi meta verileri de daha fazla görünmesini sağlar. Bu, gevşek bir ve dinamik çağırma özellikleri sağlamaya yönelik ikili biçimler için özellikle doğrudur.  
  
 Ancak, ikili biçimler genellikle bu tür açıklayıcı meta veri bilgilerini, aşağıdaki veri kayıtları için de veri düzeni bildiren bir "üstbilgiye" taşır. Yük daha sonra bu ortak meta veri bloğu bildirimini daha az ek yük ile izler. Buna karşılık XML, bir öğe veya öznitelik içindeki her bir veri öğesini, kapsayan meta verilerin her seri hale getirilmiş yük nesnesine dahil kaldı olmasını sağlayacak şekilde barındırır. Sonuç olarak, tek bir seri hale getirilmiş yük nesnesinin boyutu metin ikili gösterimlerle karşılaştırılırken benzerdir, ancak her ikisi için de bazı tanımlayıcı meta veriler belirtilmelidir, ancak her ek ile paylaşılan meta veri açıklamadan ikili biçim avantajları alt genel yük nedeniyle aktarılan yük nesnesi.  
  
 Yine de, sayılar gibi belirli veri türleri için, düz metin temsili birkaç bayt daha küçük olabileceğinden, düz metin yerine 128 bitlik ondalık tür gibi sabit boyutlu, ikili sayısal gösterimler kullanmanın bir dezavantajı olabilir. Metin verileri, genellikle daha esnek XML metin kodlama seçimlerinden de boyut avantajlarına sahip olabilir, ancak bazı ikili biçimler, .NET Ikili XML biçimi için de olmayan 16 bit veya hatta 32 bit Unicode olarak varsayılan olabilir.  
  
 Sonuç olarak, ikili iletilerin her zaman XML-metin iletilerinden daha küçük olduğu varsayımıyla, metin veya ikili arasında seçim yapma oldukça kolay değildir.  
  
 XML metinlerinden oluşan net bir avantaj, standartlara dayalıdır ve en geniş birlikte çalışabilirlik seçenekleri ve platform desteği sunar. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "kodlamalar" bölümüne bakın.  
  
### <a name="binary-content"></a>İkili Içerik  
 İkili kodlamaları, sonuçta elde edilen ileti boyutu açısından metin tabanlı kodlamalar için üst düzey olan bir alan; resimler, videolar, ses klipleri veya hizmetler arasında alışverişi gereken diğer donuk, ikili veriler gibi büyük ikili veri öğeleridir. tüketicilere. Bu veri türlerini XML metnine uydurmak için, yaygın yaklaşım, Base64 kodlaması kullanarak bunları kodlayamalıdır.  
  
 Base64 ile kodlanmış bir dizede, her karakter orijinal 8 bit 4:3 verilerin 6 bitlik kısmını temsil eder. Bu, genellikle kural tarafından eklenen fazladan biçimlendirme karakterlerini (satır başı/satır akışı) saymaz. XML ve ikili kodlamalar arasındaki farklığın önemi genellikle senaryoya bağlı olsa da, 500 MB yük aktarılırken genellikle %33 ' den büyük bir boyut kazanımı kabul edilemez.  
  
 Bu kodlama yüküyle karşılaşmamak için Ileti Iletimi Iyileştirme mekanizması (MTOM) standardı, bir iletide yer alan büyük veri öğelerinin ve bunları özel bir kodlama olmadan iletiyi ikili veri olarak taşıyan bir ileti ile taşımak için izin verir. MTOM ile iletiler, ekler veya katıştırılmış içerik (Resimler ve diğer ekli içerik) ile Basit Posta Aktarım Protokolü (SMTP) e-posta iletilerine benzer şekilde değiştirilir; MTOM iletileri, asıl SOAP iletisi olan kök bölüm olan çok parçalı/ilgili MIME dizileri olarak paketlenir.  
  
 Bir MTOM SOAP iletisi, karşılık gelen MIME bölümlerine başvuran özel öğe etiketlerinin, ikili verileri içeren iletideki özgün öğelerin yerini alması için, yönetilmeyen sürümden değiştirilir. Sonuç olarak, SOAP iletisi, onunla birlikte gönderilen MIME parçalarını işaret ederek ikili içeriğe başvurur, aksi halde XML metin verilerini taşır. Bu model iyi şekilde belirlenmiş SMTP modeliyle yakından hizalandığından, MTOM iletilerini çok sayıda platformda kodlamak ve kodunu çözmek için çok yönlü bir seçenek sunan geniş bir araç vardır.  
  
 Yine de Base64 ile olduğu gibi, MTOM kullanmanın avantajları yalnızca bir ikili veri öğesinin boyutu yaklaşık 1 KB 'yi aştığında görülür. Ek yük nedeniyle, MTOM kodlu iletiler ikili veriler için Base64 kodlaması kullanan iletilerden daha büyük olabilir, ikili yük ise bu eşiğin altında kalır. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "kodlamalar" bölümüne bakın.  
  
### <a name="large-data-content"></a>Büyük veri Içeriği  
 Tel kaplama, daha önce bahsedilen 500 MB yükü de hizmet ve istemci için harika bir yerel zorluk doğurur. Varsayılan olarak, WCF iletileri *arabellekli modda*işler. Bu, bir iletinin tüm içeriğinin gönderilmeden veya alındıktan sonra bellekte bulunduğu anlamına gelir. Bu pek çok senaryo için iyi bir stratejidir ve dijital imzalar ve güvenilir teslim gibi mesajlaşma özellikleri için gerekli olsa da, büyük mesajlar sistemin kaynaklarını tüketebilir.  
  
 Büyük yükleri ele alma stratejisi akışdır. Özellikle de XML olarak ifade edilen iletiler görece veri paketleri olarak düşünülirken, bir ileti boyutu birden fazla gigabayt olabilir ve bir veri paketinden sürekli bir veri akışına benzer. Veriler, akış modunda, ara belleğe alınmış mod yerine aktarıldığında, gönderen ileti gövdesinin içeriğini bir akış biçiminde kullanılabilir hale getirir ve ileti altyapısı, verileri gönderenin bulunduğu haliyle alıcıya sürekli iletir kullanılabileceğini.  
  
 Bu büyük veri içeriği aktarımlarının oluştuğu en yaygın senaryo, şu şekilde olan ikili veri nesnelerinin aktarımları:  
  
- Bir ileti dizisine kolayca ayrılabilir.  
  
- Zamanında teslim edilmesi gerekir.  
  
- , Aktarım başlatıldığında tamamen kullanılamaz.  
  
 Bu kısıtlamalara sahip olmayan veriler için, bir oturumun kapsamındaki ileti dizilerini bir büyük ileti olarak göndermek genellikle daha iyidir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "veri akışı" bölümüne bakın.  
  
 Büyük miktarlarda veri gönderirken `maxAllowedContentLength` IIS ayarını ayarlamanız gerekir (daha fazla bilgi için bkz. [IIS Istek sınırlarını yapılandırma](https://docs.microsoft.com/iis/configuration/system.webServer/security/requestFiltering/requestLimits/)) ve `maxReceivedMessageSize` bağlama ayarı (örneğin [System. ServiceModel. BasicHttpBinding. MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) veya <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` özelliği varsayılan olarak 28,6 MB ve `maxReceivedMessageSize` özelliğinin varsayılan değeri 64 ' dir.  
  
## <a name="encodings"></a>Kodlamalar  
 Bir *kodlama* , iletileri tel sunma hakkında bir kural kümesi tanımlar. *Kodlayıcı* böyle bir kodlama uygular ve gönderen tarafında, bir bellek içi <xref:System.ServiceModel.Channels.Message>, ağ üzerinden gönderilebilecek bir bayt akışına veya bayt arabelleğine dönüştürmek için sorumludur. Alıcı tarafında, kodlayıcı bir bayt dizisini bellekteki bir iletiye dönüştürür.  
  
 WCF üç kodlayıcı içerir ve gerekirse kendi kodlayıcılarınızı yazmanızı ve eklemenizi sağlar.  
  
 Standart bağlamaların her biri, ağ * ön ekine sahip bağlamaların ikili Kodlayıcısı (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> sınıfını ekleyerek) kullandığı, <xref:System.ServiceModel.BasicHttpBinding> ve <xref:System.ServiceModel.WSHttpBinding> sınıfları varsayılan olarak metin iletisi kodlayıcısını (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> sınıfı aracılığıyla) kullanırken önceden yapılandırılmış bir kodlayıcı içerir.  
  
|Kodlayıcı bağlama öğesi|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|SMS mesajı Kodlayıcısı, tüm HTTP tabanlı bağlamalar için varsayılan kodlayıcıdır ve birlikte çalışabilirliği en yüksek sorun olduğu tüm özel bağlamalar için uygun seçenektir. Bu kodlayıcı, ikili veriler için özel bir işleme olmadan standart SOAP 1.1/SOAP 1,2 metin iletilerini okur ve yazar. Bir iletinin <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>olarak ayarlanırsa, SOAP Zarf sarmalayıcı çıktısından çıkarılır ve yalnızca ileti gövdesi içeriği serileştirilir.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|MTOM ileti Kodlayıcısı, ikili veriler için özel işleme uygulayan ve yalnızca büyük/küçük harfe göre iyileştirme yardımcı programı olduğu için standart bağlamalarda varsayılan olarak kullanılmayan bir metin kodlayıcıdır. İleti, MTOM kodlamasının bir avantaj sağladığı bir eşiği aşan ikili veriler içeriyorsa, veriler ileti zarfının ardından bir MIME bölümüne externalized. Bu bölümde daha sonra MTOM 'yi etkinleştirme bölümüne bakın.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|İkili ileti Kodlayıcısı, ağ * bağlamaları için varsayılan kodlayıcı ve iletişim kuran her iki taraf da WCF 'yi temel alan uygun seçenektir. İkili ileti Kodlayıcısı, genellikle eşdeğer XML 1,0 gösteriminden daha küçük bir kaplama veren ve ikili verileri bayt olarak kodlayan XML bilgi kümeleri (Infosets) için Microsoft 'a özgü bir ikili gösterim olan .NET Binary XML biçimini kullanır ka.|  
  
 Kısa mesaj kodlaması genellikle birlikte çalışabilirlik gerektiren herhangi bir iletişim yolu için en iyi seçenektir; ikili ileti kodlaması ise diğer iletişim yolları için en iyi seçenektir. İkili ileti kodlaması genellikle, bir iletişim oturumu süresince tek bir iletinin metniyle ve aşamalı olarak daha küçük ileti boyutlarına kıyasla daha küçük ileti boyutları verir. Metin kodlamasının aksine, ikili kodlamanın ikili veriler için Base64 kullanma gibi özel işleme kullanması gerekmez, ancak baytları bayt olarak temsil eder.  
  
 Çözümünüz birlikte çalışabilirlik gerektirmiyorsa, ancak yine de HTTP taşıması kullanmak istiyorsanız, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> aktarım için <xref:System.ServiceModel.Channels.HttpTransportBindingElement> sınıfını kullanan özel bir bağlamaya oluşturabilirsiniz. Hizmetinizdeki bir dizi istemci birlikte çalışabilirlik gerektiriyorsa, her birinin ilgili istemcilerin etkinleştirildiği uygun taşıma ve kodlama seçeneklerine sahip olan paralel uç noktaları kullanıma sunuyorsanız önerilir.  
  
### <a name="enabling-mtom"></a>MTOM etkinleştiriliyor  
 Birlikte çalışabilirlik bir gereksinimle ve büyük ikili verilerin gönderilmesi gerektiğinde, MTOM ileti kodlaması ilgili `MessageEncoding` özelliğini <xref:System.ServiceModel.WSMessageEncoding.Mtom> olarak ayarlayarak veya <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> bir <xref:System.ServiceModel.Channels.CustomBinding>oluşturarak, standart <xref:System.ServiceModel.BasicHttpBinding> veya <xref:System.ServiceModel.WSHttpBinding> bağlamalarda etkinleştirebileceğiniz alternatif kodlama stratejisidir. [MTOM kodlama](../../../../docs/framework/wcf/samples/mtom-encoding.md) örneğinden ayıklanan aşağıdaki örnek kod, yapılandırmada MTOM 'i nasıl etkinleştireceğinizi gösterir.  
  
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
  
 Daha önce belirtildiği gibi, MTOM kodlamasını kullanma kararı, gönderdiğiniz veri hacmine bağlıdır. Ayrıca, MTOM bağlama düzeyinde etkinleştirildiğinden, MTOM 'in etkinleştirilmesi belirli bir uç noktasındaki tüm işlemleri etkiler.  
  
 MTOM Kodlayıcısı, ikili verilerin externalized olup olmamasına bakılmaksızın her zaman MTOM kodlamalı bir MIME/çok parçalı ileti yayar, genellikle yalnızca 1 KB 'den fazla ikili veri içeren iletileri değiş tokuş eden uç noktalar için MTOM 'yi etkinleştirmelisiniz. Ayrıca, MTOM özellikli uç noktalarla kullanılmak üzere tasarlanan hizmet sözleşmeleri, mümkün olduğunda, bu tür veri aktarımı işlemleri belirtilerek sınırlandırılmalıdır. İlgili denetim işlevleri ayrı bir sözleşmede bulunmalıdır. Bu "yalnızca MTOM" kuralı yalnızca MTOM özellikli bir uç nokta aracılığıyla gönderilen iletiler için geçerlidir; MTOM-Encoder, gelen MTOM olmayan iletileri de çözebilir ve ayrıştırılabilir.  
  
 MTOM Encoder 'ın kullanılması diğer tüm WCF özellikleriyle uyumludur. Bu kuralın, oturum desteğinin gerekli olduğu durumlar gibi her durumda gözlemlenebilir olabileceğini unutmayın.  
  
### <a name="programming-model"></a>Programlama Modeli  
 Uygulamanızda kullandığınız üç yerleşik kodlayıcıdan hangisi olursa olsun, programlama deneyimi ikili verileri aktarmaya benzer şekilde aynıdır. Fark, WCF 'nin verileri veri türlerine göre işleme biçimi.  
  
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
  
 MTOM kullanılırken, önceki veri sözleşmesi aşağıdaki kurallara göre serileştirilir:  
  
- `binaryBuffer` `null` değilse ve tek başına, MTOM dışsallaştırılması ek yükünü (MIME üst bilgileri, vb.) iki farklı veri içeriyorsa, veri externalized olur ve bir ikili MIME parçası olarak iletiyle birlikte taşınır. Eşik aşılırsa, veriler Base64 olarak kodlanır.  
  
- Dize (ve ikili olmayan tüm diğer türler), boyutu ne olursa olsun ileti gövdesinin içinde her zaman bir dize olarak temsil edilir.  
  
 MTOM Encoding üzerindeki etkisi, yukarıdaki örnekte gösterildiği gibi, bir işlemdeki parametre listesini kullanma, iç içe geçmiş veri sözleşmeleri kullanma veya bir koleksiyon içinde veri sözleşme nesnesi aktarma gibi açık bir veri sözleşmesi kullanmanıza bakılmaksızın aynıdır. Bayt dizileri her zaman iyileştirme için adaylardır ve iyileştirme eşikleri karşılanıyorsa en iyi duruma getirilir.  
  
> [!NOTE]
> Veri sözleşmeleri içinde <xref:System.IO.Stream?displayProperty=nameWithType> türetilmiş türler kullanmıyor olmanız gerekir. Akış verileri aşağıdaki "akış verileri" bölümünde açıklanan akış modeli kullanılarak iletilmelidir.  
  
## <a name="streaming-data"></a>Veri akışı  
 Aktarılacak büyük miktarda veriniz olduğunda, WCF 'deki akış aktarım modu, iletilerin arabelleğe alınması ve işlenmesi için varsayılan davranış için uygun bir alternatiftir.  
  
 Daha önce bahsedildiği gibi, verilerin bölünmediği durumlarda yalnızca büyük iletiler (metin veya ikili içerikle) için akışı etkinleştirin. iletinin zamanında teslim edilmesi gerekiyorsa veya aktarım başlatıldığında veriler henüz tam olarak kullanılamıyorsa.  
  
### <a name="restrictions"></a>{1&gt;Kısıtlamalar&lt;1}  
 Akış etkinleştirildiğinde önemli sayıda WCF özelliği kullanamazsınız:  
  
- İleti gövdesi için dijital imzalar, tüm ileti içerikleri için bir karma bilgi işlem gerektirdiğinden gerçekleştirilemiyor. Akış ile, ileti üst bilgileri oluşturulduğunda ve gönderildiğinde içerik tam olarak kullanılabilir değildir ve bu nedenle, dijital imza hesaplanamıyor.  
  
- Şifreleme, verilerin doğru şekilde yeniden yapılandırıldığını doğrulamak için dijital imzalara bağımlıdır.  
  
- Bir ileti aktarım sırasında kaybedilirse ve iletiler teslim edildiğinde ileti sırasını korumak üzere hizmet uygulamasına teslim etmeden önce, güvenilir oturumların istemciye yeniden teslim için gönderilen iletileri arabelleğe alması gerekir sıra dışı.  
  
 Bu işlevsel kısıtlamalar nedeniyle, akış için yalnızca aktarım düzeyi güvenlik seçeneklerini kullanabilirsiniz ve güvenilir oturumları açık duruma getirebilirsiniz. Akış yalnızca aşağıdaki sistem tanımlı bağlamalarla kullanılabilir:  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> temel aktarımları, HTTP 'nin aksine, güvenilir teslim ve bağlantı tabanlı oturum desteğine sahip olduğundan, bu iki bağlama yalnızca bu kısıtlamalara göre en düşük düzeyde etkilenir.  
  
 Message Queuing (MSMQ) aktarımında akış kullanılamaz ve bu nedenle <xref:System.ServiceModel.NetMsmqBinding> veya <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfıyla birlikte kullanılamaz. Message Queuing taşıması yalnızca kısıtlanmış bir ileti boyutuyla arabellekli veri aktarımlarını destekler, ancak diğer tüm taşımalar senaryoların çoğunluğu için hiçbir pratik ileti boyutu sınırına sahip değildir.  
  
 Eş kanal taşıması kullanılırken akış de kullanılamaz, bu nedenle <xref:System.ServiceModel.NetPeerTcpBinding>kullanılamaz.  
  
#### <a name="streaming-and-sessions"></a>Akış ve oturumlar  
 Oturum tabanlı bağlama ile çağrı akışı yaparken beklenmedik bir davranış alabilirsiniz. Kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, tüm akış çağrıları, oturumları desteklemeyen tek bir kanal (Datagram kanalı) aracılığıyla yapılır. Birden çok istemci, oturum tabanlı bir bağlama üzerinden aynı hizmet nesnesine akış çağrıları yapar ve hizmet nesnesinin eşzamanlılık modu tek olarak ayarlanır ve örnek bağlam modu PerSession olarak ayarlanır, tüm çağrılar veri birimi kanalında gelmelidir ve bu nedenle yalnızca bir çağrı bir seferde işlenir. Daha sonra bir veya daha fazla istemci zaman aşımına uğrar. Hizmet nesnesinin örnek bağlam modunu PerCall veya eşzamanlılık olarak birden çok olarak ayarlayarak bu soruna geçici bir çözüm bulabilirsiniz.  
  
> [!NOTE]
> Yalnızca bir "oturum" var olduğundan, MaxConcurrentSessions bu durumda hiçbir etkiye sahip değildir.  
  
### <a name="enabling-streaming"></a>Akışı etkinleştirme  
 Akışı aşağıdaki yollarla etkinleştirebilirsiniz:  
  
- İstekleri akış modunda gönderin ve kabul edin ve yanıtları, arabelleğe alınmış modda (<xref:System.ServiceModel.TransferMode.StreamedRequest>) kabul edin ve geri döndürün.  
  
- İstekleri arabelleğe alınmış modda gönderin ve kabul edin ve yanıtları (<xref:System.ServiceModel.TransferMode.StreamedResponse>) kabul edin ve geri döndürün.  
  
- İstekleri ve yanıtları her iki yönde de akışlı modda gönderin ve alın. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Aktarım modunu, tüm bağlamalarda varsayılan ayar olan <xref:System.ServiceModel.TransferMode.Buffered>olarak ayarlayarak akışı devre dışı bırakabilirsiniz. Aşağıdaki kod, yapılandırma içinde aktarım modunun nasıl ayarlanacağını gösterir.  
  
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
  
 Kod içinde bağlamalarınızı örneklediğinizde, daha önce bahsedilen değerlerden birine bağlamanın ilgili `TransferMode` özelliğini (veya özel bir bağlama oluşturuyorsanız taşıma bağlama öğesini) ayarlamanız gerekir.  
  
 İşlevselliği etkilemeden, istek ve yanıtlar için akışı veya iletişim tarafların her iki tarafında bağımsız olarak her iki yönü de etkinleştirebilirsiniz. Bununla birlikte, aktarılan veri boyutunun her zaman bir iletişim bağlantısının her iki uç noktasında akış kullanılmasına olanak tanıyan önemli olduğunu varsaymalısınız. Uç noktalardan birinin WCF ile uygulanmadığı platformlar arası iletişim için, akış kullanma özelliği platformun akış özelliklerine bağlıdır. Başka bir nadir özel durum, bir istemci veya hizmetin çalışma kümesini en aza indirecek ve yalnızca küçük arabellek boyutlarına uygun olması gereken bellek tüketimi temelli bir senaryo olabilir.  
  
### <a name="enabling-asynchronous-streaming"></a>Zaman uyumsuz akışı etkinleştirme  
 Zaman uyumsuz akışı etkinleştirmek için, hizmet ana bilgisayarına <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> uç noktası davranışını ekleyin ve <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğini `true`olarak ayarlayın. Ayrıca gönderme tarafına doğru zaman uyumsuz akış özelliği ekledik. Bu, hizmetin, büyük olasılıkla ağ tıkanıklığı nedeniyle veya hiç okunmayan çok sayıda istemciye ileti akışı yaptığı senaryolarda hizmetin ölçeklenebilirliğini geliştirir. Bu senaryolarda, artık istemci başına hizmette tek tek iş parçacıklarını engelliyoruz. Bu, hizmetin daha fazla istemciyi işleyebilmesini sağlar ve bu sayede hizmetin ölçeklenebilirliğini geliştirir.  
  
### <a name="programming-model-for-streamed-transfers"></a>Akışlı aktarımlar için programlama modeli  
 Akışa yönelik programlama modeli basittir. Akışlı verileri almak için, tek bir <xref:System.IO.Stream> yazılmış giriş parametresine sahip olan bir işlem sözleşmesi belirtin. Akan verileri döndürmek için <xref:System.IO.Stream> bir başvuru döndürün.  
  
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
  
 Önceki örnekteki `Echo` işlem bir akış alır ve döndürür ve bu nedenle <xref:System.ServiceModel.TransferMode.Streamed>bir bağlamada kullanılması gerekir. `RequestInfo`işlemi için, yalnızca bir <xref:System.IO.Stream>döndürdüğünden <xref:System.ServiceModel.TransferMode.StreamedResponse> en uygun seçenektir. Tek yönlü işlem <xref:System.ServiceModel.TransferMode.StreamedRequest>için idealdir.  
  
 Aşağıdaki `Echo` veya `ProvideInfo` işlemlerine ikinci bir parametre eklemenin, hizmet modelinin arabelleğe alınmış bir stratejiye geri dönmesi ve akışın çalışma zamanı serileştirme gösterimini kullanması neden olur. Yalnızca tek bir giriş akışı parametresine sahip işlemler uçtan uca istek akışı ile uyumludur.  
  
 Benzer şekilde, bu kural ileti sözleşmeleri için geçerlidir. Aşağıdaki ileti sözleşmesinde gösterildiği gibi, ileti sözleşmeniz için akış olan tek bir gövde üyesine sahip olabilirsiniz. Akışa ek bilgi iletmek istiyorsanız, bu bilgilerin bir taşınan ileti üstbilgileri olması gerekir. İleti gövdesi, akış içeriği için özel olarak ayrılmıştır.  
  
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
  
 Akış, dosyanın sonuna ulaştığında (EOF) ileti kapatılır. İleti gönderilirken (bir değer döndüren veya bir işlemi çağırma) geçirebilirsiniz bir <xref:System.IO.FileStream> ve akış tamamen okunan ve EOF sınırına kadar WCF altyapısı tüm veriler daha sonra bu akıştan çeker. Kaynak için, önceden oluşturulmuş <xref:System.IO.Stream> türetilmiş bir sınıf mevcut olmayan akışlı verileri aktarmak için, böyle bir sınıf oluşturun, akış kaynağınız üzerinde bu sınıfın bir üst öğesini kullanın ve bunu bağımsız değişken veya dönüş değeri olarak kullanın.  
  
 Bir ileti alınırken WCF, Base64 kodlamalı ileti gövdesi içeriği (veya MTOM kullanılıyorsa ilgili MIME bölümü) üzerinden bir akış oluşturur ve içerik okunarak akış EOF 'a ulaşırsa.  
  
 Aktarım düzeyi akış, diğer herhangi bir ileti sözleşme türü (parametre listeleri, veri sözleşmesi bağımsız değişkenleri ve açık ileti sözleşmesi) ile de birlikte çalışarak, ancak bu tür iletilerin serileştirilmesi ve seri hale getiricisi tarafından arabelleğe alınması gerekir Bu tür sözleşme varyantları kullanılması önerilmez.  
  
### <a name="special-security-considerations-for-large-data"></a>Büyük veriler için özel güvenlik konuları  
 Tüm bağlamalar, hizmet reddi saldırılarını önlemeye yönelik gelen ileti boyutunu sınırlandırmaya olanak tanır. Örneğin <xref:System.ServiceModel.BasicHttpBinding>, gelen iletinin boyutunu izleyen bir [System. ServiceModel. BasicHttpBinding. MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) özelliği sunar ve bu nedenle iletiyi işlerken erişilen maksimum bellek miktarını da sınırlar. Bu birim, varsayılan değer olan 65.536 baytlık bir bayt olarak ayarlanır.  
  
 Büyük veri akışı senaryosuna özgü bir güvenlik tehdidi, alıcı akışının akışını beklediği zaman verilerin arabelleğe yazılmasına neden olarak bir hizmet reddi sağlar. Örneğin, WCF her zaman bir iletinin SOAP üstbilgilerini arabelleğe alır ve bu nedenle bir saldırgan, verilerin arabelleğe alınmasını zorlamak için tamamen üst bilgilerden oluşan büyük bir kötü amaçlı ileti oluşturabilir. Akış etkinleştirildiğinde `MaxReceivedMessageSize` çok büyük bir değere ayarlanabilir, çünkü alıcı tüm iletiyi bellekte aynı anda arabelleğe almak için hiçbir zaman beklemiyor. WCF, iletiyi arabelleğe almak için zorlanırsa, bir bellek taşması oluşur.  
  
 Bu nedenle, en büyük gelen ileti boyutunu kısıtlamak bu durumda yeterli değildir. WCF arabelleklerinin belleğini kısıtlamak için `MaxBufferSize` özelliği gereklidir. Akış sırasında bunu güvenli bir değere ayarlamanız (veya varsayılan değerde tutmanız) önemlidir. Örneğin, hizmetinizin Boyutu 4 GB 'a kadar dosyaları alması ve bunları yerel diskte depolaması gerektiğini varsayalım. Ayrıca, aynı anda yalnızca 64 KB 'lık verileri arabelleğe almanız için belleğinizin kısıtlı olduğunu varsayalım. Daha sonra `MaxReceivedMessageSize` 4 GB ve `MaxBufferSize` 64 KB olarak ayarlayın. Ayrıca, hizmet uygulamanızda, 64 KB 'lık öbeklerdeki gelen akıştan okuduğunuzdan ve önceki bir disk diske yazılmadan ve bellekten atılmadan önce bir sonraki öbeği okuduğunuzdan emin olmalısınız.  
  
 Bu kotanın, yalnızca WCF tarafından yapılan arabelleğe alma işleminin sınırlandırdığından ve kendi hizmette veya istemci uygulamanızda yaptığınız herhangi bir arabelleğe karşı sizi koruyamadığı anlaşılması de önemlidir. Ek güvenlik konuları hakkında daha fazla bilgi için bkz. [veriler Için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
> Ara belleğe alınmış veya akış aktarımları kullanma kararı, uç noktanın yerel bir karardır. HTTP aktarımları için, aktarım modu bir bağlantı veya proxy sunucuları ile diğer aracılar arasında yayılmaz. Aktarım modunun ayarlanması, hizmet arabiriminin açıklamasına yansıtılmaz. Bir hizmet için WCF istemcisi oluşturduktan sonra, modu ayarlamak için akışlı aktarımlarla kullanılması amaçlanan hizmetler için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış kanal aktarımları için, aktarım modu bir ilke onaylama işlemi olarak dağıtılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
