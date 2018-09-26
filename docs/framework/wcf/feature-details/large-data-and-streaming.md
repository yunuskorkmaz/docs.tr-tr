---
title: Büyük Veriler ve Akış Yapma
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: f381df2acdb370c6e84d3a00079578f8fceb69f3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192580"
---
# <a name="large-data-and-streaming"></a>Büyük Veriler ve Akış Yapma
Windows Communication Foundation (WCF) iletişimleri XML tabanlı bir altyapıdır. XML veri yaygın olarak tanımlanan standart metin biçiminde kodlanmış çünkü [XML 1.0 belirtimi](https://go.microsoft.com/fwlink/?LinkId=94838), bağlı sistemleri geliştiricilere ve mimarlara genellikle açısından gönderilen iletileri kablo ayak izini (veya boyut) hakkında arasında Ağ ve metin tabanlı XML kodlama verimli ikili veri aktarımı için özel zorlukları doğurur.  
  
## <a name="basic-considerations"></a>Temel konuları  
 WCF için aşağıdaki bilgileri hakkında bilgiler sağlamak için bu bölümde bazı genel endişelerinizi ve konuları için Kodlamalar, ikili veri vurgular ve, genellikle akışı bağlantılı sistemlerde altyapıları için geçerlidir.  
  
### <a name="encoding-data-text-vs-binary"></a>Kodlama verileri: Metni vs. İkili  
 Yaygın olarak ifade edilen Geliştirici sorunları önemli ölçüde daha büyük olacak şekilde kodlama sayısal değerleri değerlendirilir XML etiketleri başlangıç ve bitiş etiketleri, yinelenen niteliği nedeniyle İkili biçimler karşılaştırıldığında önemli ölçüde olduğunu markanızın içerir çünkü metin değerleri ifade edilir ve bir metin biçiminde eklemek için özel kodlanmalı çünkü bu ikili verileri verimli bir şekilde ifade.  
  
 Ortamı genellikle çoğu bu ve benzer ilgiliyse sırada geçerli olduğundan, bir XML Web Hizmetleri ortamda kodlanmış XML metin iletileri ve eski uzak yordam çağrısı (RPC) ikili kodlanmış iletileri gerçek birbirinden çok daha az önemli. ilk göz önünde bulundurarak önerebilir.  
  
 XML-text kodlanmış iletileri saydam ve "insan tarafından okunabilir", ikili ileti genellikle oldukça karşılaştırmaya belirsiz ve araçları kod çözme daha zor. Bu fark Okunaklılık bir ikili iletileri çoğunlukla satır içi meta veri XML metin iletileri gibi olduğu yükü ekler yükünde gerçekleştirmeniz kolayca gözden kaçabilir yol açar. İkili dosya biçimleri için bu özellikle doğrudur kaybetmiş bağlantısından ve dinamik çağırma özellikler sağlamak için hedeflenir.  
  
 Ancak, ikili biçimler genellikle gibi açıklayıcı meta veri bilgileri "veri düzeni aşağıdaki veri kayıtları için de bildiren bir başlık" içinde taşır. Yük, ardından bu daha az yük ile ortak meta veri blok bildirim izler. Buna karşılık, kapsayan meta veriler her bir seri hale getirilmiş yükü nesne için art arda dahildir böylece bir öğe veya öznitelik XML her veri öğesini alır. Tek bir seri hale getirilmiş yükü nesnenin boyutu hem de paylaşılan meta veri açıklamasını her ikili biçimi avantajlarından ancak bazı açıklayıcı meta verileri ifade edilmelidir gibi ikili değer ifadelerinden mi metne karşılaştırılırken sonuç olarak, benzer ek daha düşük toplam yükü nedeniyle aktarılan yükü nesnesi.  
  
 Yine de sayı gibi veri türleri için belirli bir sabit boyutlu, ikili sayısal gösterimleri kullanılarak dezavantajı olabilir, 128 bit ondalık gibi bir türü yerine düz metin, düz metin olarak gösterimi birkaç bayt daha küçük olabilir. Metin veri seçenekleri, kodlama, bazı ikili biçimler .NET ikili XML biçimi geçerli değil, 16 bit veya 32 bit bile Unicode varsayılan ancak genellikle daha esnek XML metin boyutu avantajından da olabilir.  
  
 Sonuç olarak, metin veya ikili arasında karar ikili ileti her zaman XML metin iletileri küçük olduğunu varsayarak olarak oldukça kolay değil.  
  
 XML metin iletileri Temizle bir avantajı, standartlara dayalı ve seçenek yelpazesinden birlikte çalışabilirlik seçenekleri ve platform desteği sunan sağlamasıdır. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Kodlamalar" bölümüne bakın.  
  
### <a name="binary-content"></a>İkili içerik  
 İkili Kodlamalar nerede elde edilen ileti boyutu bakımından metin tabanlı kodlamaları için üstün bir alan olan resim, video, ses klipleri veya herhangi bir biçimde hizmetleri arasında alınıp opak, ikili veri gibi büyük ikili veri öğeleri ve bunların Tüketici. Bu tür verilerin XML metin sığdırmak için yaygın Base64 kodlaması kullanarak bunları kodlanacak yaklaşımdır.  
  
 Base64 ile kodlanmış bir dize içinde 6 bitlik kuralı tarafından yaygın olarak eklenen ek biçimlendirme karakterleri (satır başı/satır besleme) sayılmaz 4:3 kodlama yükü oranı, Base64 için sonuçlanır özgün 8 bitlik veri her bir karakteri temsil eder. Birden fazla 33 500 MB veri iletirken % boyutu kazanç önemi XML ve ikili Kodlamalar arasındaki farklar, genellikle senaryoya bağlıdır, ancak genellikle kabul edilebilir değil.  
  
 Bu ek yükü, ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlama önlemek için standart bir iletideki büyük veri öğeleri harici hale getirerek ve bunları iletinin tüm özel kodlamadan ikili veri taşıyan sağlar. MTOM ile ilgili iletiler ve Basit Posta Aktarım Protokolü (SMTP) e-posta iletilerini ekler veya katıştırılmış içeriği (Resimler ve diğer eklenen içeriği); ile benzer bir biçimde değiştirilir MTOM iletileri multipart/related MIME dizileri gerçek SOAP iletisi olan bir kök bölümü ile paketlenmiştir.  
  
 Böylece ilgili MIME bölümü başvuran özel öğesi etiketleri ikili veri içeren bir ileti özgün öğeleri gerçekleşmesi MTOM SOAP iletisi, hazırlanmamış kodlanmış sürümünden değiştirildi. Bunun sonucunda, SOAP iletisi ile gönderilen MIME bölümü işaret ederek ikili içerik başvuruyor, ancak Aksi durumda yalnızca XML metin verileri taşır. Bu model tanınmış bir SMTP modeliyle yakından hizalanır olduğundan geniş kodlama ve son derece birlikte çalışabilen bir seçim getiren birçok platformda MTOM iletileri kodunu çözme için araç desteği.  
  
 Böylece MTOM kullanmanın avantajları, yalnızca bir ikili veri öğesi boyutu yaklaşık 1 KB aştığında görüldüğünde yine de, Base64 olarak MTOM da MIME için gereken bazı ek yükü ile birlikte gönderilir. Ek yükü nedeniyle, iletileri MTOM kodlu ikili yük olarak bu eşiğin altında kalırsa ikili veriler için Base64 kodlaması kullanan iletileri büyük olabilir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Kodlamalar" bölümüne bakın.  
  
### <a name="large-data-content"></a>Büyük veri içeriği  
 Kablo Ayak izi CPU'nun, daha önce bahsedilen 500 MB'lık yükü de hizmet ve istemci için en büyük yerel zor doğurur. Varsayılan olarak, WCF iletileri işleyen *arabellekli modu*. Bu, bir iletinin tüm içeriği mevcut bellekte gönderilmeden önce veya alındıktan sonra olduğu anlamına gelir. Çoğu senaryo için iyi bir stratejisi ve dijital imzalar ve güvenilir teslim gibi Mesajlaşma özellikleri için gerekli olmakla birlikte, büyük iletiler bir sistem kaynaklarının tüketebileceği.  
  
 Büyük yükleriyle başa çıkmak için strateji akış. Hata iletileri, özellikle XML biçiminde, ifade yaygın olarak düşünülebilir nispeten küçük veri paketleri olacak şekilde, bir ileti birden çok gigabayt boyutunda olması ve bir veri paketi birden çok sürekli veri akışı benzer. Veri akış modunda arabellekli modu yerine aktarıldığında gönderen ileti gövdesi içeriğini bir akış şeklinde alıcı kullandırır ve bu duruma ileti altyapısı sürekli olarak veri gönderenden alıcıya iletir kullanılabilir.  
  
 Aktarımları oluşan büyük veriler içeriklerin ikili veri aktarımları olduğu en yaygın senaryo nesneler:  
  
-   Kolayca bir ileti sırasına bölünmesi olamaz.  
  
-   Zamanında teslim edilmelidir.  
  
-   Aktarım başlatıldığında, tamamen kullanılamaz.  
  
 Bu kısıtlamaları olmayan veriler için daha büyük bir ileti bir oturuma kapsamında dizileri ileti göndermek genellikle daha iyi. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Veri akışı" bölümüne bakın.  
  
 Büyük miktarlarda veri gönderilirken kurmanız gerekecektir `maxAllowedContentLength` IIS ayarını (daha fazla bilgi için [yapılandırma IIS istek sınırları](https://go.microsoft.com/fwlink/?LinkId=253165)) ve `maxReceivedMessageSize` ayarı bağlama (örneğin [ System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) veya <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` 28.6 M özelliği varsayılan olarak ve `maxReceivedMessageSize` özelliği varsayılan olarak 64 KB.  
  
## <a name="encodings"></a>Kodlamalar  
 Bir *kodlama* kablo iletileri sunmak nasıl hakkında kurallar kümesi tanımlar. Bir *Kodlayıcı* böyle bir kodlama uygular ve açma için Gönderen tarafında sorumlu olduğu bir <xref:System.ServiceModel.Channels.Message> bellek içi iletisine bayt akışı veya ağ üzerinden gönderilen bayt arabelleği. Alıcı tarafında Kodlayıcı bir bellek içi iletisi Bayt dizisine dönüştürür.  
  
 WCF üç kodlayıcılar içerir ve gerekirse, yazma ve kendi kodlayıcılara takın olanak tanır.  
  
 Her standart bağlamaları bağlamaları Net * önekiyle ikili Kodlayıcı yapabildiği kullanın, önceden yapılandırılmış bir kodlayıcı içerir (ekleyerek <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> sınıfı) sırada <xref:System.ServiceModel.BasicHttpBinding> ve <xref:System.ServiceModel.WSHttpBinding> sınıfları kullanın (, metin ileti kodlayıcı <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> sınıfı) varsayılan olarak.  
  
|Kodlayıcı bağlama öğesi|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Metin iletisi Kodlayıcı, birlikte çalışabilirlik en önemli olduğu tüm HTTP tabanlı bağlantılar için varsayılan kodlayıcı ve tüm özel bağlamalar için uygun seçim işliyor. Bu Kodlayıcı okur ve standart SOAP 1.1/SOAP 1.2 kısa mesaj ile ikili veriler için hiçbir özel işlem yazar. Varsa <xref:System.ServiceModel.Channels.MessageVersion> bir ileti kümesine `None`, SOAP Zarfı sarmalayıcı çıktısı atlanır ve yalnızca ileti gövdesi içeriği seri hale.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|MTOM ileti Kodlayıcı ikili veriler için özel işleme uygular ve kesinlikle bir olay iyileştirme yardımcı olduğundan varsayılan herhangi bir standart bağlamalar tarafından kullanılmadığından bir metin Kodlayıcı olur. İletinin nerede MTOM kodlama avantaj verir bir eşiği aştığında ikili veri içeriyorsa, verileri bir MIME bölümü aşağıdaki ileti zarfı içinde te dış. Bu bölümün sonraki kısımlarında etkinleştirme MTOM bakın.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|WCF iletişim kuran iki taraf dayalı ne zaman ikili ileti Kodlayıcısı Net * bağlamaları ve uygun seçeneği için varsayılan kodlayıcı açıktır. İkili ileti Kodlayıcısı .NET ikili XML biçimi, Microsoft'a özgü ikili temsili, genellikle bir daha küçük kaplama alanı eşdeğer XML 1.0 gösterimi daha verir ve ikili verileri bir bayt olarak kodlar XML bilgi kümesi (Infosets) kullanır. Akış.|  
  
 Metin iletisi kodlaması genellikle en iyi birlikte çalışabilirlik, ikili ileti kodlama başka bir iletişim yol için en iyi seçenek olduğu sürece gerektiren herhangi bir iletişim yolu için seçenektir. İkili ileti kodlama, genellikle daha küçük ileti boyutları bir tek ileti ve hatta aşamalı olarak daha küçük ileti metni boyutları iletişim oturum süresi boyunca karşılaştırıldığında verir. Metin kodlaması, aksine ikili kodlama gibi Base64 kullanarak ikili veriler için özel işlem kullanmak zorunda değildir ancak bayt bayt olarak temsil eder.  
  
 Çözümünüzü birlikte çalışabilirlik, gerekli değildir ancak yine de HTTP aktarımı kullanmak istiyorsanız, oluşturabileceğiniz <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> kullanan özel bir bağlama içine <xref:System.ServiceModel.Channels.HttpTransportBindingElement> taşıma için sınıf. Birlikte çalışabilirlik hizmetinizdeki istemciler ihtiyacınız varsa, her etkin ilgili istemciler için uygun bir taşıma ve kodlama seçenekleri vardır paralel uç noktalarını kullanıma önerilir.  
  
### <a name="enabling-mtom"></a>MTOM etkinleştirme  
 Ne zaman birlikte çalışabilirlik bir gereksinimdir ve büyük ikili veri gönderilmelidir sonra standart etkinleştirebilirsiniz stratejisi kodlama alternatif olan ileti MTOM kodlama <xref:System.ServiceModel.BasicHttpBinding> veya <xref:System.ServiceModel.WSHttpBinding> ilgili ayarlayarak bağlamaları `MessageEncoding` özelliğini <xref:System.ServiceModel.WSMessageEncoding.Mtom> veya oluşturma <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> içine bir <xref:System.ServiceModel.Channels.CustomBinding>. Aşağıdaki örnek kod, ayıklanan [MTOM kodlama](../../../../docs/framework/wcf/samples/mtom-encoding.md) örnek yapılandırmada MTOM etkinleştirme gösterir.  
  
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
  
 Daha önce bahsedildiği gibi karar MTOM kodlama gönderdiğiniz veri hacmine bağlıdır. Ayrıca, MTOM etkinleştirme MTOM bağlama düzeyinde etkinleştirilmiş olduğundan, belirli bir noktadaki tüm işlemleri etkiler.  
  
 MTOM Kodlayıcısı her zaman ikili veri olup olmadığını te dış yukarı sona erer bağımsız olarak bir MTOM kodlu MIME/çok-part iletiyi yayar olduğundan, genellikle yalnızca MTOM iletileri ile 1 KB'tan ikili veri değişimi uç noktalar için etkinleştirmeniz gerekir. Ayrıca, MTOM etkin uç noktaları ile kullanılmak üzere tasarlanmış hizmet sözleşmelerini mümkün olduğunda, bu tür veri aktarımı işlemleri belirtmek için kısıtlı olabilir gerekir. İlgili denetim işlevselliği, ayrı bir sözleşme bulunmalıdır. "Yalnızca MTOM" Bu kuralı yalnızca MTOM etkin uç nokta gönderilen iletiler için geçerlidir; MTOM Kodlayıcısı, kod çözme ve gelen MTOM olmayan iletileri de ayrıştırılamıyor.  
  
 MTOM Kodlayıcısı kullanarak diğer tüm WCF özelliklerle uyumludur. Bu oturum desteği gerekli olduğunda gibi tüm durumlarda, bu kural gözlemlemek mümkün olmayabilir olduğunu unutmayın.  
  
### <a name="programming-model"></a>Programlama Modeli  
 Uygulamanızda kullandığınız üç yerleşik kodlayıcılarda bağımsız olarak, bir programlama deneyimi ikili veri aktarımı bakımından aynı olduğu. WCF veri türlerini verileri nasıl işlediğini içinde farktır.  
  
```  
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}   
```  
  
 MTOM kullanırken, önceki veri anlaşması aşağıdaki kurallara göre sıralanır:  
  
-   Varsa `binaryBuffer` değil `null` ve ayrı ayrı MTOM externalization Yükü (MIME üst bilgileri ve benzeri) yaslamak için yeterli veri içeren Base64 karşılaştırıldığında kodlama, veriler te dış ve ikili bir MIME bölümü olarak iletiyi içeren bir denetim. Eşik, verileri Base64 kodlanmış.  
  
-   Dize (ve ikili olmayan diğer tüm türleri) her zaman boyutundan bağımsız olarak, ileti gövdesi içindeki bir dizeyle gösterilir.  
  
 MTOM kodlama aynı önceki örnekte gösterilen şekilde bir açık veri anlaşması kullanıp bir işlemde bir parametre listesini kullanın, iç içe veri sözleşmelerine sahiptir veya bir veri anlaşması nesnesi bir koleksiyon içine aktarmak etkisidir. Bayt dizileri her zaman en iyi duruma getirme için aday olduğunu ve en iyi duruma getirme eşikleri karşılandığında iyileştirilmiştir.  
  
> [!NOTE]
>  Değil kullanması gerektiğini <xref:System.IO.Stream?displayProperty=nameWithType> türetilmiş türleri veri sözleşmeleri içinde. Aşağıdaki "Veri akışı" bölümünde açıklandığı gibi akış modelini kullanarak Stream veri bildirilmesi.  
  
## <a name="streaming-data"></a>Akış verileri  
 Büyük miktarda veri aktarmak için akış aktarım WCF arabelleğe alma ve iletilerini tamamen belleğindeki işleme varsayılan davranışına uygun bir alternatif modundadır.  
  
 Daha önce bahsedildiği gibi ileti vakitli şekilde teslim edilmelidir, verileri, kesimlere olamaz veya aktarım başlatıldığında verileri henüz tam olarak kullanılabilir değil (metin veya ikili içerik ile) büyük iletiler için yalnızca akış etkinleştirin.  
  
### <a name="restrictions"></a>Kısıtlamalar  
 Akış etkinleştirildiğinde WCF özellikleri önemli sayıda kullanamazsınız:  
  
-   Tüm ileti içeriği üzerinde karma hesaplaması gerektirdiğinden ileti gövdesi için dijital imzalar gerçekleştirilemiyor. Akış ile içerik ileti üstbilgilerini oluşturulan ve gönderilen ve bu nedenle, bir dijital imza hesaplanamıyor, tam olarak kullanılamaz.  
  
-   Şifreleme verileri doğru şekilde reconstructed olduğunu doğrulamak için dijital imzalar bağlıdır.  
  
-   Güvenilir oturum aktarımı bir ileti kaybedildiğinde gönderilen iletiler yeniden teslim istemcide arabellek gerekir ve iletileri hizmette mesajları durumunda ileti sırası korumak için hizmet uygulaması için teslim etmeden önce saklamak gerekir Çıkış dizi.  
  
 Bu işlev kısıtlamaları nedeniyle yalnızca aktarım düzeyi güvenlik seçenekleri akış ve güvenilir oturumları kapatamıyor kullanabilirsiniz. Akış yalnızca aşağıdaki sistem tanımlı bağlamalarla kullanılabilir:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
 Çünkü, temel alınan taşımalarına <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> devralınan güvenilir teslim ve bağlantı tabanlı oturum desteği HTTP, bu iki bağlamaları yalnızca en düşük düzeyde uygulamada bu kısıtlamaları etkilenir.  
  
 Akış ile Message Queuing (MSMQ) aktarma kullanılamıyor ve bu nedenle kullanılamaz <xref:System.ServiceModel.NetMsmqBinding> veya <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfı. Diğer tüm aktarımları senaryoları büyük çoğunluğu için herhangi bir pratik ileti boyutu sınır yoktur ancak Message Queuing taşıma arabelleğe alınan veri aktarımları kısıtlanmış ileti boyutu, yalnızca destekler.  
  
 Akış kullanılamıyor ayrıca eş kanal taşımasını kullanarak bu nedenle olmadığında kullanılabilen <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
#### <a name="streaming-and-sessions"></a>Akış ve oturumlar  
 Oturum tabanlı bir bağlamayla çağrıları akışı yapılırken beklenmeyen davranışı elde edebilirsiniz. Tüm akış çağrılar kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, oturumları desteklemiyor tek kanalı (veri birimi kanal) yapılır. Birden çok istemci aynı hizmet nesnesi akış çağrıları üzerinden oturum tabanlı bir bağlama yapın ve hizmet nesnenin eşzamanlılık modu ayarlamak tek ve kendi örnek bağlamı modu değeri PerSession olarak ayarlandığında, tüm çağrıları, veri birimi kanal ve bu nedenle yalnızca biri aracılığıyla gitmeniz gerekir Çağrı teker teker işlenir. Bir veya daha fazla istemciler daha sonra zaman aşımına uğrayabilir. Her iki hizmet nesnenin örnek bağlamı modu PerCall ya da birden fazla eşzamanlılık ayarlayarak bu sorunu geçici olarak çalışabilir.  
  
> [!NOTE]
>  Kullanılabilir tek bir "oturum" olduğundan MaxConcurrentSessions bu durumda hiçbir etkisi olmaz.  
  
### <a name="enabling-streaming"></a>Akış'ı etkinleştirme  
 Aşağıdaki yollarla akış etkinleştirebilirsiniz:  
  
-   Gönder ve akış modunda isteklerini kabul etmek okuyup kabul edin ve yanıtların arabelleğe alınan modunda döndürür (<xref:System.ServiceModel.TransferMode.StreamedRequest>).  
  
-   Gönder ve arabelleğe alınan modda isteklerini kabul etmek okuyup kabul edin ve akış modunda yanıtlarını döndürmek (<xref:System.ServiceModel.TransferMode.StreamedResponse>).  
  
-   Gönderin ve her iki yönde de akış modunda isteklerini ve yanıtlarını alın. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Aktarım modunu ayarlayarak akış devre dışı bırakabilir <xref:System.ServiceModel.TransferMode.Buffered>, tüm bağlamaları varsayılan ayarı olduğu. Aşağıdaki kod, aktarım modunun yapılandırmada ayarlamak gösterilmektedir.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streaming"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Kod bağlamanızda başlattığınızda, ilgili ayarlamalısınız `TransferMode` özelliği bağlama (veya özel bir bağlama oluşturuyorsanız aktarım bağlama öğesinin) yukarıda belirtilen değerlerden biri olarak.  
  
 İstekleri ve yanıtları veya her iki tarafındaki bağımsız olarak her iki yönde iletişim kuran tarafların işlevselliğini etkilemeden akışını kapatabilirsiniz. Ancak, aktarılan veri boyutunun akış etkinleştirme iletişim bağlantının her iki bitiş noktasında karardır kadar önemli olduğunu her zaman varsaymanız gerekir. Uç noktalardan biri burada WCF ile uygulanmadı, platformlar arası iletişim için akış kullanma olanağı platformun akış özelliklerine bağlıdır. Nadir başka bir özel durum burada bir istemci veya hizmet çalışma kümesi en aza indirmeniz gerekir ve yalnızca küçük bir arabellek boyutları gücünüze senaryo odaklı bir bellek tüketimi olabilir.  
  
### <a name="enabling-asynchronous-streaming"></a>Zaman uyumsuz akış'ı etkinleştirme  
 Zaman uyumsuz akış etkinleştirmek için eklemeniz <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> kümesini ve hizmet ana bilgisayarı için uç nokta davranışı, <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğini `true`. Doğru zaman uyumsuz gönderme tarafında akış özelliği de ekledik. Bu senaryolarda bazıları nedeni Ağ Tıkanıklığı okuma yavaşsa veya hiç okunmuyor birden çok istemciye iletileri burada akış hizmetinin ölçeklenebilirliği artırır. Bu senaryolarda biz artık istemci başına hizmetine tek tek iş parçacıklarını engellemez. Bu, hizmet birden çok daha fazla istemci böylece hizmetinin ölçeklenebilirliği artırma işleminin olmasını sağlar.  
  
### <a name="programming-model-for-streamed-transfers"></a>Akış aktarımları programlama modeli  
 Akış için programlama modeli oldukça basittir. Akış veri almak için tek bir sahip bir işlem anlaşması belirtin <xref:System.IO.Stream> giriş parametresi türü belirtilmiş. Akış veri döndürmek için dönüş bir <xref:System.IO.Stream> başvuru.  
  
```  
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
  
 İşlemi `Echo` önceki örnekte alır ve bir akışı döndürür ve bir bağlamayla üzerinde kullanılmalıdır <xref:System.ServiceModel.TransferMode.Streamed>. İşlem için `RequestInfo`, <xref:System.ServiceModel.TransferMode.StreamedResponse> yalnızca döndürdüğü için en uygun olan bir <xref:System.IO.Stream>. Tek yönlü işlem için en uygun <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Unutmayın, ikinci parametresinin aşağıdaki ekleme `Echo` veya `ProvideInfo` işlemleri için arabelleğe alınan bir strateji geri dönmek ve akışı çalışma zamanı serileştirme gösterimini kullanmak hizmet modeli neden olur. Yalnızca tek bir giriş akışı parametre işlemleriyle akış uçtan uca istekle uyumlu değildir.  
  
 Bu kural için ileti sözleşmeleri benzer şekilde uygular. Aşağıdaki ileti anlaşması gösterildiği gibi bir akışı, ileti anlaşması yalnızca tek bir gövde üyesi olabilir. Ek bilgi stream ile iletişim kurmak istiyorsanız, bu bilgileri bir taşınan ileti üst bilgilerinde olması gerekir. İleti gövdesi, içerik akışı için özel olarak ayrılmıştır.  
  
```  
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}   
```  
  
 Akış dosya sonu (EOF) ulaştığında akış aktarımları uç ve ileti kapatılır. İleti gönderilirken (bir değer döndüren veya bir işlemi çağırma) geçirebilirsiniz bir <xref:System.IO.FileStream> ve akış tamamen okunan ve EOF sınırına kadar WCF altyapısı tüm veriler daha sonra bu akıştan çeker. Akış veri kaynağı için aktarmak için hiçbir gibi önceden oluşturulmuş <xref:System.IO.Stream> türetilmiş sınıf mevcut, bu tür bir sınıf oluşturmak, akış kaynağınızı o sınıfın kaplama ve, bağımsız değişken ya da dönüş değeri kullanın.  
  
 Bir ileti alındığında, WCF bir akış Base64 ile kodlanmış ileti gövdesi içeriğini (veya MTOM kullanıyorsanız ilgili MIME bölümü) oluşturur ve içeriği okurken akışın EOF ulaşır.  
  
 Aktarım düzeyi akış aynı zamanda tüm diğer ileti anlaşması türü (parametre listeleri, veri sözleşme bağımsız değişkenleri ve açık bir ileti anlaşması) çalışır, ancak serileştirme ve seri durumundan çıkarma Bu tür iletileri yazdığınız için seri hale getirici tarafından arabelleğe almayı gerektirir , böyle bir sözleşme çeşitleri kullanılması önerilebilir değildir.  
  
### <a name="special-security-considerations-for-large-data"></a>Büyük veriler için özel güvenlik konuları  
 Tüm bağlamalar, hizmet reddi saldırılarını önlemek için gelen iletiler boyutunu sınırlamak sağlar. <xref:System.ServiceModel.BasicHttpBinding>, Örneğin, bir [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) gelen iletilerin boyutu için sınır ve bu nedenle de en çok erişilen bellek miktarını sınırların özelliği iletiyi işlerken. Bu birimi, varsayılan değeri 65.536 bayt bayt cinsinden ayarlanır.  
  
 Büyük verileri akış senaryosuna özgü bir güvenlik tehdidi alıcı akışını beklerken arabelleğe alınan verilerin eskimesine yol tarafından hizmet reddine neden. Örneğin, WCF her zaman bir iletinin SOAP üstbilgileri arabelleğe alır ve bu nedenle bir saldırganın arabelleğe alınan verileri zorlamak için tamamen üst bilgilerini içeren büyük bir kötü amaçlı iletisi oluşturabilir. Akış etkinleştirildiğinde `MaxReceivedMessageSize` alıcı asla bellekte aynı anda arabelleğe alınan iletinin tamamı beklediği için son derece büyük bir değere ayarlanabilir. WCF ileti arabellek zorlanır bellek taşması ortaya çıkar.  
  
 Bu nedenle, en büyük gelen ileti boyutu sınırlama, bu durumda yeterli değildir. `MaxBufferSize` Özelliği, bellek, WCF arabellekler sınırlamak için gereklidir. Bu güvenli bir değere ayarlayın (veya varsayılan değerinde tutmak) önemli olduğunu akış olduğunda. Örneğin, hizmetiniz alması gerekir varsayalım. en fazla 4 GB boyutundaki dosyaları ve bunları yerel diskte depolar. Ayrıca, bellek, yalnızca 64 KB veri teker teker arabellek şekilde sınırlıdır varsayalım. Ayarlarsınız sonra `MaxReceivedMessageSize` 4 GB ve `MaxBufferSize` 64 KB. Ayrıca, hizmet uygulamanızda, yalnızca 64 KB'lık parçalar halinde gelen akış okuma ve önceki kaldırıldı önce İleri öbek okunmaz emin olmalısınız diske yazılan ve bellek atıldı.  
  
 Bu aynı zamanda WCF tarafından yapılan arabelleğe alma Bu kota yalnızca sınırlar anlamak önemlidir ve tüm kendi hizmet veya istemci uygulamasında yaptığınız arabelleğe karşı koruyamaz. Ek güvenlik konuları hakkında daha fazla bilgi için bkz: [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
>  Arabelleğe alınan ya da akış aktarımları karar, uç noktanın yerel bir karardır. HTTP taşımaları için bir bağlantı üzerinden veya proxy sunucuları ve diğer aracılar için aktarım modunu dağıtılmaz. Hizmet arabirimi açıklamasında aktarım modunu ayarlama yansıtılmaz. Bir hizmeti bir WCF istemcisi oluşturduktan sonra akış aktarımları ile modu ayarlamak için kullanılması hedeflenen hizmetler için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış kanal aktarımlar, aktarım modu İlkesi onaylama olarak yayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
