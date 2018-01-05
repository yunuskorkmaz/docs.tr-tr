---
title: "Büyük Veriler ve Akış Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 187927a9e75348454f5832c2a34bf780e48e4358
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="large-data-and-streaming"></a>Büyük Veriler ve Akış Yapma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir XML tabanlı iletişim altyapısıdır. XML verilerini yaygın olarak tanımlanan standart metin biçiminde kodlanmış çünkü [XML 1.0 belirtimi](http://go.microsoft.com/fwlink/?LinkId=94838), bağlı sistemler geliştiricileri ve mimarlar genellikle açısından gönderilen iletiler kablo ayak izini (veya boyut) hakkında arasında Ağ ve metin tabanlı XML kodlaması, ikili veri verimli aktarımı için özel zorluklar doğurur.  
  
## <a name="basic-considerations"></a>Temel konuları  
 İçin aşağıdaki bilgileri hakkında bilgiler sağlamak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu bölümde bazı genel sorunları ve Kodlamalar, ikili veri değerlendirmeleri vurgular ve, genellikle akış bağlı sistemler altyapıları için geçerlidir.  
  
### <a name="encoding-data-text-vs-binary"></a>Kodlama verileri: Metin vs. İkili  
 XML kodlama sayısal değerleri önemli ölçüde daha büyük olarak değerlendirilir, yinelenen niteliği başlangıç etiketleri ve bitiş etiketleri nedeniyle ikili biçimlerine kıyasla önemli yüke sahiptir algısına yaygın olarak ifade edilen Geliştirici sorunları içerir metin değerleri ifade edilir ve bir metin biçiminde katıştırmak için özel kodlanmalı çünkü bu ikili verileri verimli bir şekilde açıklanamayan çünkü.  
  
 Çoğu bu ve benzer ilgiliyse sırasında geçerli olan, bir XML Web Hizmetleri ortamında kodlanmış XML metin iletileri ve eski uzak yordam çağrısı (RPC) ikili olarak kodlanmış iletilerinde gerçek birbirinden genellikle daha az önemli ortamıdır ilk göz önünde bulundurarak önerebilir.  
  
 XML metin kodlanmış iletileri saydam ve "okunabilir", ikili iletiler genellikle oldukça karşılaştırmaya belirsiz ve Araçlar olmadan çözecek zordur. Bu fark okunabilirliği ikili iletileri de genellikle satır içi meta veri XML metin iletileri gibi olduğu yükü ekler yükünde taşımak, overlook birine yol açar. İkili dosya biçimleri için bu özellikle doğrudur kaybetmiş bağ ve dinamik çağırma özellikleri sağlamak üzere hedeflenir.  
  
 Ancak, ikili biçimler genellikle gibi açıklayıcı meta veri bilgileri "de aşağıdaki veri kayıtları için veri düzeni bildiren bir üst bilgisinde," taşır. Yükü, ardından bu ortak meta veri bloğu bildirim az ek yük ile izler. Buna karşılık, böylece kapsayan meta verileri her bir seri hale getirilmiş yükü nesne için art arda gelen XML her bir veri öğesi bir öğe veya öznitelik barındırır. Sonuç olarak, tek serileştirilmiş yük nesnenin boyutu her paylaşılan meta verileri açıklamasından ikili biçimi avantajları ancak her ikisi için bazı açıklayıcı meta verileri ifade edilmesi gerekir gibi ikili Beyanları metne karşılaştırılırken benzer ek daha az genel yükü nedeniyle aktarılan yükü nesnesi.  
  
 Yine de, belirli veri türleri, numaraları gibi bir dezavantajı, sabit boyutlu, ikili sayısal Beyanları kullanmanın olabilir, birkaç bayt daha küçük bir 128-bit decimal türü gibi düz metin yerine, düz metin olarak gösterimi olabilir. Metin verileri ayrıca bazı ikili biçimleri .NET ikili XML biçimine uygulanmaz, 16 bit veya 32 bit bile Unicode varsayılan ancak seçimleri, kodlama genellikle daha esnek XML metinden boyutu yararları olabilir.  
  
 Sonuç olarak, metin veya ikili arasında karar ikili iletileri her zaman XML metin iletileri küçük olduğunu varsayarak olarak oldukça olarak kolay değildir.  
  
 XML metin iletileri Temizle avantajlarından standartlara dayalı ve birlikte çalışabilirlik seçeneklerini ve platform desteği İlkler seçimi teklif ' dir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]Bu konunun devamındaki "Kodlamalar" bölümü.  
  
### <a name="binary-content"></a>İkili içerik  
 Bir alan ikili kodlamaları nerede metin tabanlı Kodlamalar elde edilen ileti boyutu açısından üstün olan resim, video, ses klipleri veya başka bir form hizmetleri arasında alınıp opak, ikili veri gibi büyük ikili veri öğeleri ve bunların Tüketiciler. Bu veri türlerini XML metni sığması için ortak Base64 kodlaması kullanarak bunları kodlanacak yaklaşımdır.  
  
 Base64 ile kodlanmış bir dize, 6-kural tarafından yaygın olarak eklenen ek biçimlendirme karakterlerini (satır başı/satır besleme) saymaz 4:3 kodlama yükünü oranı Base64 için sonuçlanır özgün 8 bit veri bitleri her bir karakteri temsil eder. Birden fazla 33 500 MB yükü iletirken % boyutu kazanç XML ve ikili kodlamaları arasındaki farklar önemini genellikle senaryoya bağlıdır, ancak genellikle kabul edilebilir değil.  
  
 Bu ek yükü, ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama önlemek için standart bir iletideki büyük veri öğeleri harici hale getirerek ve bunları iletiyle herhangi özel kodlamadan ikili veri olarak gerçekleştirmesini sağlar. MTOM ile Basit Posta Aktarım Protokolü (SMTP) e-posta iletilerini ekler veya katıştırılmış içerik (Resimler ve diğer katıştırılmış içerik); ile benzer bir şekilde arasında alınıp verilen iletileri MTOM iletileri gerçek SOAP iletisi olan kök bölümüyle multipart/related MIME sıraları olarak paketlenir.  
  
 Böylece ilgili MIME bölümlerine bakın özel öğesi etiketleri ikili veri içerdiği ileti özgün öğeleri gerçekleşmesi MTOM SOAP iletisi beklemediğiniz kodlanmış sürümünden değiştirilir. Sonuç olarak, SOAP iletisi ile gönderilen MIME bölümleri göstererek ikili içerik başvuruyor, ancak Aksi durumda yalnızca XML metin veri taşır. Bu model yakından tanınmış SMTP modeliyle hizalanır çünkü yoktur araç kodlamak ve son derece birlikte çalışabilir bir seçim hangi kolaylaştırır MTOM iletileri birçok platformda kod çözme için desteği geniş.  
  
 Böylece MTOM kullanmanın yararları, yalnızca bir ikili veri öğesi boyutu yaklaşık 1 KB aştığında görülür yine de, Base64 olarak MTOM ayrıca MIME biçimi için gereken bazı ek ile birlikte gönderilir. Ek yükü nedeniyle, iletileri MTOM kodlu ikili yükü bu eşiğin altında kalırsa ikili veriler için Base64 kodlaması kullanan iletileri daha büyük olabilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]Bu konunun devamındaki "Kodlamalar" bölümü.  
  
### <a name="large-data-content"></a>Büyük veri içeriği  
 Kablo Ayak izi kenara, yukarıda açıklanan 500 MB yükü konumundaki bir harika yerel zorluk hizmet ve istemci için de oluşturur. Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletileri işleyen *arabellekli modu*. Bu, bir iletinin tüm içeriği bellekte mevcut gönderilmeden önce veya alındıktan sonra olduğu anlamına gelir. Çoğu senaryo için iyi bir stratejisi ve dijital imzalar ve güvenilir teslim gibi Mesajlaşma özellikleri için gerekli olmakla birlikte, büyük iletileri bir sistem kaynaklarının tüketebileceği.  
  
 Büyük yükleri ile mücadele etmek için stratejisi akış. Hata iletileri, özellikle XML'de, ifade yaygın olarak zorlayıcı nispeten küçük veri paketleri olacak şekilde, bir ileti birden çok gigabayta olmalı ve bir veri paketi birden çok sürekli veri akışı benzer. Veri akış modunda arabellekli modu yerine aktarıldığında, gönderenin ileti gövdesi içeriğini bir akış şeklinde alıcıya kullanılabilmesini sağlar ve bu duruma ileti altyapısı sürekli veri gönderenden alıcıya iletir kullanılabilir.  
  
 En yaygın senaryo aktarımları ortaya tür büyük veri içeriği ikili veri aktarımlarını olan nesneler:  
  
-   Kolayca bir ileti dizisi bölünemez.  
  
-   Zamanında teslim edilmelidir.  
  
-   Aktarım başlatıldığında tamamen içinde kullanılamaz.  
  
 Bu kısıtlamaların yok verileri için daha büyük bir ileti bir oturumun kapsamı içinde iletilerinin dizileri göndermek genellikle daha iyi olur. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]Bu konunun devamındaki "Veri akışı" bölümü.  
  
 Büyük miktarlarda verinin gönderirken ayarlamanız gerekir `maxAllowedContentLength` IIS ayarını (daha fazla bilgi için bkz: [yapılandırma IIS istek sınırları](http://go.microsoft.com/fwlink/?LinkId=253165)) ve `maxReceivedMessageSize` ayarı bağlama (örneğin [ System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) veya <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` 28.6 M özelliği varsayılanlara ve `maxReceivedMessageSize` özellik varsayılanlarını 64 KB.  
  
## <a name="encodings"></a>Kodlamaları  
 Bir *kodlama* kablo iletileri sunmak nasıl hakkında kurallar kümesini tanımlar. Bir *Kodlayıcı* böyle bir kodlama uygulayan ve dönüş için Gönderen tarafında sorumlu olduğu bir <xref:System.ServiceModel.Channels.Message> bellek içi iletisine bayt akışı veya ağ üzerinden gönderilen bayt arabellek. Alıcı tarafında bir bayt dizisi bir bellek içi iletisine Kodlayıcı etkinleştirir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]üç kodlayıcılar içerir ve gerekirse, yazma ve kendi kodlayıcılara takın olanak sağlar.  
  
 Her standart bağlamaları yapabildiği Net * önek bağlamalarla kullanmak ikili kodlama önceden yapılandırılmış bir kodlayıcı içerir (ekleyerek <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> sınıfı) sırada <xref:System.ServiceModel.BasicHttpBinding> ve <xref:System.ServiceModel.WSHttpBinding> sınıflarını kullanın (tarafından metin ileti kodlayıcı <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> sınıfı) varsayılan olarak.  
  
|Kodlayıcı bağlama öğesi|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Metin ileti Kodlayıcı tüm HTTP tabanlı bağlamaları için varsayılan kodlayıcı ve tüm özel bağlamaları için uygun seçim birlikte çalışabilirlik yüksek önemli olduğu. Bu Kodlayıcı okur ve standart SOAP 1.1/SOAP 1.2 metin iletileri ikili veriler için hiçbir özel işleme ile yazar. Varsa <xref:System.ServiceModel.Channels.MessageVersion> bir ileti kümesine `None`, SOAP Zarfı sarmalayıcı çıktısını atlanır ve yalnızca ileti gövdesi içeriği seri.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|MTOM ileti Kodlayıcı ikili veriler için bir özel işleme uygulayan ve kesinlikle bir olay iyileştirme yardımcı olduğundan herhangi bir standart bağlamaları varsayılan olarak kullanılmayan bir metin Kodlayıcı ' dir. İletinin nerede MTOM kodlama bir avantajı verir bir eşiği aştığında ikili veri içeriyorsa, verileri ileti zarfı aşağıdaki MIME bölümüne externalized. Bu bölümde etkinleştirme MTOM bakın.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Her iki iletişim kuran tarafların dayalı zaman ikili ileti Kodlayıcı Net * bağlar ve uygun seçeneği için varsayılan kodlayıcı olduğuna [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. İkili ileti Kodlayıcı .NET ikili XML biçimi, genellikle eşdeğer XML 1.0 gösterimi daha küçük bir yer verir ve ikili veri bayt olarak kodlar XML bilgi kümeleri (Infosets) Microsoft'a özgü ikili temsili kullanır Akış.|  
  
 İleti metni kodlama genellikle en iyi birlikte çalışabilirlik, herhangi bir iletişim yolu için en iyi seçenek iken ikili ileti kodlama gerektiren herhangi bir iletişim yolu için seçimdir. İkili ileti kodlama genellikle boyutları tek iletiyi ve aşamalı olarak daha küçük ileti metni boyutları iletişim oturumu süresince karşılaştırıldığında daha küçük ileti verir. Metin kodlaması, aksine ikili kodlama Örneğin, Base64 kullanarak ikili veriler için özel olarak işlenmesi kullanmak zorunda kalmazsınız ancak bayt bayt olarak temsil eder.  
  
 Çözümünüzü birlikte çalışabilirlik, gerektirmez, ancak hala HTTP aktarımı kullanmak istediğiniz, oluşturmak <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> kullanan özel bağlama içine <xref:System.ServiceModel.Channels.HttpTransportBindingElement> taşıma için sınıf. Hizmetinizi istemcilerde çeşitli birlikte çalışabilirlik gerekiyorsa, her etkin ilgili istemciler için uygun bir taşıma ve kodlama seçimi sahip paralel uç noktalarını kullanıma önerilir.  
  
### <a name="enabling-mtom"></a>MTOM etkinleştirme  
 Ne zaman birlikte çalışabilirlik bir gereksinimdir ve büyük ikili veri gönderilmeyecek sonra ileti MTOM kodlama olduğundan üzerinde standart etkinleştirebilirsiniz stratejisi kodlama alternatif <xref:System.ServiceModel.BasicHttpBinding> veya <xref:System.ServiceModel.WSHttpBinding> ilgili ayarlayarak bağlamaları `MessageEncoding` özelliğine <xref:System.ServiceModel.WSMessageEncoding.Mtom> veya oluşturma <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> içine bir <xref:System.ServiceModel.Channels.CustomBinding>. Ayıklanan aşağıdaki kod örneği, [MTOM kodlama](../../../../docs/framework/wcf/samples/mtom-encoding.md) örnek yapılandırmada MTOM etkinleştirme gösterir.  
  
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
  
 Daha önce belirtildiği gibi MTOM kodlama kullanmaya karar göndermekte olduğunuz veri biriminde bağlıdır. Ayrıca, MTOM etkinleştirilmesi MTOM bağlama düzeyinde etkinleştirilmiş olduğundan, tüm işlemleri belirli bir noktadaki etkiler.  
  
 MTOM Kodlayıcısı her zaman ikili veri externalized yukarı olup sonlandırır bağımsız olarak MTOM kodlu MIME/çok-part iletisine yayar olduğundan, genellikle yalnızca MTOM birden çok 1 KB ikili veri iletilerle exchange uç noktalar için etkinleştirmeniz gerekir. Ayrıca, MTOM etkin uç noktaları ile kullanılmak üzere tasarlanmış Hizmet sözleşmeleri mümkün olduğunda, bu tür veri aktarım işlemleri belirtmek için kısıtlı gerekir. İlgili denetim işlevselliği ayrı bir sözleşmesinde yer almalıdır. Yalnızca bir MTOM etkin uç noktası aracılığıyla gönderilen iletiler bu "Yalnızca MTOM" kuralının uygulanacağı; MTOM Kodlayıcısı kod çözme ve gelen MTOM olmayan iletileri de ayrıştırılamadı.  
  
 MTOM Kodlayıcısı kullanarak, uygun diğer tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özellikleri. Bu kural oturum desteği gerekli olduğunda gibi tüm durumlarda izlemek mümkün olmayabilir olduğunu unutmayın.  
  
### <a name="programming-model"></a>Programlama Modeli  
 Uygulamanızda kullanmak üç yerleşik kodlayıcılar bağımsız olarak, bir programlama deneyimi ikili veri aktarma göre aynıdır. Nasıl farktır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kendi veri türlerine bağlı verileri işler.  
  
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
  
 MTOM kullanırken, önceki veri sözleşmesi aşağıdaki kurallara göre sıralanır:  
  
-   Varsa `binaryBuffer` değil `null` ve tek tek MTOM externalization yükünü (MIME Üstbilgileri vb.) iki yana yaslamak için yeterli veri içeren Base64 karşılaştırıldığında kodlama, veriler externalized ve ikili bir MIME parçası olarak iletiyle taşınan. Eşik aşılırsa değil, veriler Base64 kodlanmış.  
  
-   Dize (ve ikili olmayan tüm diğer türleri) her zaman boyutu ne olursa olsun ileti gövdesi içinde bir dize olarak gösterilir.  
  
 MTOM kodlama aynı önceki örnekte gösterildiği gibi bir açık veri sözleşmesi kullanıp bir işlemde bir parametre listesi kullanın, iç içe veri sözleşmeleri veya bir veri sözleşmesi nesnesi bir koleksiyon içinde aktarım etkisidir. Bayt dizileri her zaman en iyi duruma getirme adaylar ve en iyi duruma getirme eşikleri karşılanıyorsa en iyi duruma getirilir.  
  
> [!NOTE]
>  Değil kullanarak <xref:System.IO.Stream?displayProperty=nameWithType> türetilmiş tür veri sözleşmeleri içinde. Aşağıdaki "Veri akışı" bölümünde açıklanan akış modeli kullanarak veri akışı bildirilmesi.  
  
## <a name="streaming-data"></a>Veri akışı  
 Büyük miktarda veri aktarmak için akış aktarım modunda olduğunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arabelleğe alma ve tamamen bellekte iletileri işleme varsayılan davranışı için uygun bir alternatiftir.  
  
 Daha önce belirtildiği gibi yalnızca büyük iletiler (içerikle metin veya ikili) için ileti zamanında teslim edilmelidir, verileri, kesimlere olamaz veya aktarımı başlatıldığında verileri henüz tam olarak kullanılabilir değilse, akış etkinleştirin.  
  
### <a name="restrictions"></a>Kısıtlamalar  
 Çok sayıda kullanamazsınız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] akış etkinleştirildiğinde özellikleri:  
  
-   Dijital imzalar ileti gövdesi için bir karma tüm ileti içeriği bilgi işlem gerektirdiğinden gerçekleştirilemiyor. Akış ile içerik ileti üstbilgilerini oluşturulan ve gönderilen ve bu nedenle, bir dijital imza hesaplanamıyor, tam olarak kullanılabilir değil.  
  
-   Şifreleme, verileri yeniden doğru yapılandırılmış olduğunu doğrulamak için dijital imzaları bağlıdır.  
  
-   Güvenilir oturumlar bir ileti aktarımı kaybederseniz gönderilen ileti yeniden teslim için istemcisinde arabellek gerekir ve durumda iletileri alınan ileti sırası korumak için hizmet uygulaması için teslim etmeden önce hizmette iletileri tutun gerekir Çıkış sıra.  
  
 Bu işlev kısıtlamaları nedeniyle yalnızca aktarım düzeyinde güvenlik seçenekleri akış ve güvenilir oturumlar dışı bırakamazsınız kullanabilirsiniz. Akış yalnızca aşağıdaki sistem tarafından tanımlanan bağlamalarla kullanılabilir:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
 Çünkü, temel alınan taşımalarına <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> yapısında güvenilir teslim ve Destek, oturum bağlantısı tabanlı sahip HTTP, bu iki bağlamaları sağlamaları ile fazla ilgilenmez uygulamada bu kısıtlamaların etkilenir.  
  
 Akış ile Message Queuing (MSMQ) aktarma kullanılamıyor ve bu nedenle kullanılamaz <xref:System.ServiceModel.NetMsmqBinding> veya <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfı. Diğer tüm aktarımları çoğunluğu senaryoları için tüm pratik ileti boyut sınırı yoktur ancak Message Queuing aktarım yalnızca kısıtlı ileti boyutu ile arabelleğe alınan veri aktarımlarını destekler.  
  
 Akış değil de kullanılabilir eş kanal taşıma kullanan şekilde olmadığında bulunan <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
#### <a name="streaming-and-sessions"></a>Akış ve oturumlar  
 Oturum tabanlı bir bağlamayla çağrıları akış sırasında beklenmeyen bir davranış elde edebilirsiniz. Tüm akış çağrılar kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, oturumlar desteklemeyen bir tek kanalı (veri birimi kanalı) yapılır. Birden çok istemci aynı hizmet nesnesi akış çağrıları üzerinden oturum tabanlı bağlama yapmak ve hizmet nesnenin eşzamanlılık modu ayarlamak tek ve onun örnek bağlamı modu değeri PerSession olarak ayarlandığında, tüm çağrıları veri birimi kanalı ve bu nedenle yalnızca biri gitmeniz gerekir Çağrı aynı anda işlenir. Bir veya daha fazla istemciler daha sonra zaman aşımına olabilir. Bu sorunun geçici çözümü için ya da hizmet nesnenin örnek bağlamı modu PerCall veya birden çok eşzamanlılık ayarlayarak.  
  
> [!NOTE]
>  Kullanılabilir tek "oturumu" olduğundan MaxConcurrentSessions bu durumda etkisi yoktur.  
  
### <a name="enabling-streaming"></a>Akış etkinleştirme  
 Aşağıdaki yollarla akış etkinleştirebilirsiniz:  
  
-   Gönder ve akış modunda isteklerini kabul etmek ve kabul ve yanıtların arabelleğe alınan modunda dönmek (<xref:System.ServiceModel.TransferMode.StreamedRequest>).  
  
-   Gönderme ve arabelleğe alınan modunda isteklerini kabul etmek ve kabul etmek ve yanıtları akış modunda dönmek (<xref:System.ServiceModel.TransferMode.StreamedResponse>).  
  
-   Gönderir ve her iki yönde akış modunda isteklerini ve yanıtlarını alır. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Aktarım modunu ayarlayarak akış devre dışı bırakabilirsiniz <xref:System.ServiceModel.TransferMode.Buffered>, tüm bağlamaları varsayılan ayarı olduğu. Aşağıdaki kod, yapılandırmada aktarım modu ayarlamak gösterilmiştir.  
  
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
  
 Kodda, bağlamanın örneğini, ilgili ayarlamalısınız `TransferMode` bağlama (veya özel bağlama oluşturuyorsanız aktarım bağlama öğesi) özelliğini yukarıda açıklanan değerlerden birine.  
  
 Her iki yönünde bağımsız olarak her iki tarafında da iletişim kuran tarafların veya istekleri ve yanıtları için işlevselliği etkilemeden akışı kapatabilirsiniz. Ancak, her zaman aktarılan veri boyutu akış etkinleştirme iletişimi sağlayan bir bağlantı üzerindeki her iki uç noktaları düzeltilir kadar önemli olduğunu varsayın. Burada uç noktalardan biri uygulanmadı ile platformlar arası iletişim için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], akış kullanma yeteneğini platformun akış özelliklerine bağlıdır. Nadir başka bir özel durum, burada bir istemci veya hizmet kendi çalışma kümesinin en aza gerekir ve yalnızca küçük bir arabellek boyutu destekleyebilir senaryo tabanlı bir bellek tüketimi olabilir.  
  
### <a name="enabling-asynchronous-streaming"></a>Zaman uyumsuz akış etkinleştirme  
 Zaman uyumsuz akışını etkinleştirmek için ekleme <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> uç noktası davranışı hizmeti ana bilgisayarı ve kümesi için kendi <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğine `true`. Doğru zaman uyumsuz gönderme tarafında akış özelliği de ekledik. Bu, burada iletileri bazıları okumada Ağ Tıkanıklığı nedeni yavaş ya da hiç okuma olmayan birden çok istemciye akış senaryoları hizmetinde ölçeklenebilirliğini artırır. Bu senaryolarda biz şimdi istemci başına hizmet üzerinde tek tek iş parçacığı engellemez. Bu hizmet böylece hizmet ölçeklenebilirliğini geliştirmek çok daha fazla istemci işleyebilmesi olmasını sağlar.  
  
### <a name="programming-model-for-streamed-transfers"></a>Akış aktarımları için programlama modeli  
 Akış için programlama modelini basittir. Akış veri almak için tek bir sahip bir işlem sözleşmesi belirtin <xref:System.IO.Stream> giriş parametresi belirtilmiş. Akış veri döndürmek için dönüş bir <xref:System.IO.Stream> başvuru.  
  
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
  
 İşlemi `Echo` önceki örnekte alır ve bir akış döndürür ve bu nedenle sahip bir bağlama üzerinde kullanılmalıdır <xref:System.ServiceModel.TransferMode.Streamed>. İşlem için `RequestInfo`, <xref:System.ServiceModel.TransferMode.StreamedResponse> yalnızca döndürdüğünden en uygun olan bir <xref:System.IO.Stream>. Tek yönlü işlem için uygundur <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Bu ikinci bir parametresi şu şekilde ekleme Not `Echo` veya `ProvideInfo` işlemleri için arabelleğe alınan bir strateji geri dönmek ve akış çalışma zamanı serileştirme gösterimini kullanmak hizmet modeli neden olur. Yalnızca bir tek Giriş akışı parametresiyle işlemleri akış uçtan uca istekle uyumlu değildir.  
  
 Bu kural için ileti sözleşmeleri benzer şekilde uygular. Aşağıdaki ileti sözleşmede gösterildiği gibi bir akışı, ileti sözleşmesi yalnızca tek gövde üyesi olabilir. Ek bilgi akış ile iletişim kurmak istiyorsanız, bu bilgileri bir taşınan ileti üstbilgilerinde olması gerekir. İleti gövdesi akış içeriğini özel olarak ayrılmış.  
  
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
  
 Akış dosya sonuna (EOF) ulaştığında akış aktarımları uç ve ileti kapatılır. İleti gönderilirken (değer döndürme veya bir işlem çağırma) geçirebilirsiniz bir <xref:System.IO.FileStream> ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı sonradan çeker tüm veriler bu akıştan akış tamamen okunan ve EOF sınırına kadar. Akış veri kaynağı için aktarmak için hiçbir tür önceden derlenmiş <xref:System.IO.Stream> türetilmiş sınıf mevcut, bu tür bir sınıf oluşturun, o sınıfın akış kaynağınız kaplama ve bağımsız değişkeni ya da dönüş değeri olarak kullanın.  
  
 Bir ileti alırken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapıları Base64 ile kodlanmış ileti akışında bir gövde içerik (veya MTOM kullanıyorsanız ilgili MIME bölümü) ve akış içeriği okurken EOF eriştiğinde.  
  
 Aktarım düzeyinde akış ayrıca herhangi diğer ileti sözleşmesi türü (parametre listeleri, veri sözleşmesi bağımsız değişkenler ve açık ileti sözleşmesi) çalışır, ancak seri hale getirme ve seri durumdan çıkarma Bu tür iletileri yazdığınızdan seri hale getirici tarafından arabelleğe almayı gerektirir , bu tür sözleşme çeşitleri kullanarak önerilir değil.  
  
### <a name="special-security-considerations-for-large-data"></a>Büyük veriler için özel güvenlik konuları  
 Tüm bağlamaları, hizmet reddi saldırılarını önlemek için gelen ileti boyutunu sınırlamak izin verir. <xref:System.ServiceModel.BasicHttpBinding>, Örneğin, kullanıma sunan bir [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) gelen ileti boyutunu bounds ve bu nedenle de en çok erişilen bellek miktarını bounds özelliği ileti işleme sırasında. Bu birimi bayt 65,536 bayt varsayılan değerini ayarlayın.  
  
 Büyük veri akış senaryosu için özel bir güvenlik tehdidi alıcı akışını beklerken arabelleğe alınan verileri neden olan bir hizmet reddi provokes. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her zaman bir iletinin SOAP üstbilgileri arabelleğe alır ve bir saldırgan arabelleğe alınan verileri zorlamak için tamamen üstbilgilerinin oluşan büyük bir kötü amaçlı iletisi oluşturabilir. Akış etkinleştirildiğinde `MaxReceivedMessageSize` alıcı hiçbir zaman bellek aynı anda arabelleğe alınan iletinin tamamını beklediği son derece büyük bir değere ayarlanabilir. Varsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir bellek taşması oluşur ileti arabellek zorlanır.  
  
 Bu nedenle, en büyük gelen ileti boyutu sınırlama, bu durumda yeterli değil. `MaxBufferSize` Özelliği bellek sınırlamak için gereklidir, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arabellek. Bu güvenli bir değere ayarlayın (veya varsayılan değer olarak saklamak) önemlidir akış olduğunda. Örneğin, hizmetiniz alması gerekir varsayalım en fazla 4 GB boyutunda dosyaları ve bunları yerel diskte depolar. Ayrıca, bellek, yalnızca 64 KB veri aynı anda arabellek şekilde kısıtlıdır varsayalım. Sonra da ayarlamanız gerekir `MaxReceivedMessageSize` 4 GB ve `MaxBufferSize` 64 KB. Ayrıca, hizmet uygulamanızda 64 KB öbek gelen akışta yalnızca okuma ve önceki bırakıldı önce sonraki öbek okunmaz sağlamanız gerekir. diske yazılan ve bellekten atıldı.  
  
 Gerçekleştirilir arabelleğe alma Bu kota yalnızca sınırlar anlaşılması önemlidir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve tüm kendi hizmet veya istemci uygulamasında bunu arabelleğe karşı koruyamaz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ek güvenlik konuları Bkz [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
>  Arabelleğe alınan veya akış aktarımları kullanmaya karar, uç noktanın yerel bir karardır. HTTP taşımaları için bir bağlantı üzerinden veya proxy sunucuları ve diğer aracılar için aktarım modunu dağıtılmaz. Aktarım modunu ayarlama hizmet arabirimi açıklamasında yansıtılmaz. Oluşturma sonrasında bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci bir hizmet ile akış aktarımları modu ayarlamak için kullanılması hedeflenen Hizmetleri için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış kanal aktarımlar, aktarım modu İlkesi onaylama yayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
