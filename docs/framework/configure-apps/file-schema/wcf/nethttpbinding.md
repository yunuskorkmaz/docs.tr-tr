---
title: <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: b717dc76d6226395e9e0345ead750901bb874e03
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738862"
---
# <a name="nethttpbinding"></a>\<netHttpBinding >
Bir Windows Communication Foundation (WCF) hizmetinin HTTP üzerinden iletişim kurabilen uç noktaları yapılandırmak ve göstermek için kullanabileceği bir bağlamayı temsil eder. Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web yuvaları kullanılır, aksi takdirde HTTP kullanılır.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHttpBinding >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpBinding>
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowCookies`|İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.|  
|`bypassProxyOnLocal`|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bir Internet kaynağı, yerel bir adresi varsa yereldir. Yerel bir adres, aynı bilgisayarda, yerel LAN veya intranette bulunan ve sözdizimi, sözdizimi, "http://webserver/" ve "http://localhost/" URI 'Lerinde olduğu gibi bir nokta (.) tarafından tanımlanır.<br /><br /> Bu özniteliğin ayarlanması, BasicHttpBinding ile yapılandırılan uç noktaların yerel kaynaklara erişirken proxy sunucusunu kullanıp kullanmadığını belirler. Bu öznitelik `true`, yerel Internet kaynaklarına yönelik istekler proxy sunucusunu kullanmaz. İstemcilerin, bu öznitelik `true`olarak ayarlandığında aynı makinede hizmetlerle görüşülürken bir proxy üzerinden gitmesini isterseniz ana bilgisayar adını (localhost yerine) kullanın.<br /><br /> Bu öznitelik `false`olduğunda, tüm Internet istekleri proxy sunucu aracılığıyla yapılır.|  
|`closeTimeout`|Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`hostNameComparisonMode`|URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.|  
|`maxBufferPoolSize`|Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri. Varsayılan değer 524288 (0X80000) bayttır.<br /><br /> Arabellek Yöneticisi, arabellek havuzu kullanarak arabellek kullanma maliyetini en aza indirir. Arabellekleri, kanalın dışına geldiklerinde hizmete göre işlemek için gereklidir. Arabellek havuzunda ileti yükünü işlemek için yeterli bellek yoksa, arabellek yöneticisinin CLR yığınından ek bellek ayırması gerekir ve bu da çöp toplama yükünü artırır. CLR atık yığınından kapsamlı ayırma, arabellek havuzu boyutunun çok küçük olduğunu ve bu öznitelik tarafından belirtilen sınırı artırarak performansın daha büyük bir ayırma ile iyileşebileceğinin göstergesidir.|  
|`maxBufferSize`|Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri. Varsayılan değer 65.536 bayttır.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı. İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65.536 bayttır.|  
|`messageEncoding`|SOAP iletisini kodlamak için kullanılan kodlayıcıyı tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metin: bir metin mesajı Kodlayıcısı kullanın.<br />-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.<br /><br /> Varsayılan değer metindir. Bu öznitelik <xref:System.ServiceModel.WSMessageEncoding>türündedir.|  
|`name`|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. Her bağlamada bir `name` ve `namespace` özniteliği, hizmetin meta verilerinde benzersiz bir şekilde tanımlanır. Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`namespace`|Bağlamanın XML ad alanını belirtir. Varsayılan değer "http://tempuri.org/Bindings" değeridir. Her bağlamada bir `name` ve `namespace` özniteliği, hizmetin meta verilerinde benzersiz bir şekilde tanımlanır.|  
|`openTimeout`|Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`proxyAddress`|HTTP proxy adresini içeren bir URI. `useSystemWebProxy` `true`olarak ayarlanırsa, bu ayar `null`olmalıdır. Varsayılan, `null` değeridir.|  
|`receiveTimeout`|Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:10:00 ' dir.|  
|`sendTimeout`|Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`textEncoding`|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -Bigendianunıcode: Unicode Bigenyen kodlaması.<br />-UNICODE: 16 bit kodlama.<br />-UTF8:8 bit kodlama<br /><br /> Varsayılan değer UTF8 ' dir. Bu öznitelik <xref:System.Text.Encoding>türündedir.|  
|`transferMode`|İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt üzerinde akış yapılıp yapılmayacağını belirten geçerli bir <xref:System.ServiceModel.TransferMode> değeri.|  
|`useDefaultWebProxy`|Varsa, sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|||  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-basichttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>türündedir.|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings >](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 NetHttpBinding ileti göndermek için taşıma olarak HTTP kullanır. Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web Yuvaları kullanılacaktır.  Bir istek ile kullanıldığında, yanıt sözleşmesi NetHttpBinding bir ikili kodlayıcı ile bir BasicHttpBinding gibi davranır.  
  
 Güvenlik varsayılan olarak kapalıdır, ancak [\<security >](security-of-basichttpbinding.md) alt öğesinin mode özniteliği `None`dışında bir değere ayarlanarak eklenebilir. Varsayılan olarak bir "metin" ileti kodlaması ve UTF-8 metin kodlaması kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ilk ve ikinci nesil Web Hizmetleri ile HTTP iletişimi ve en fazla birlikte çalışabilirlik sağlayan <xref:System.ServiceModel.NetHttpBinding> kullanımını gösterir. Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü, `<endpoint>` öğesinin `binding` özniteliği kullanılarak belirtilir. Temel bağlamayı yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir. Uç noktanın, hizmet için aşağıdaki yapılandırma kodunda gösterildiği gibi `<endpoint>` öğesinin `bindingConfiguration` özniteliğini kullanarak, bağlama yapılandırmasına ad ile başvurması gerekir.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir. Önceki örnekteki işlevsellik, bindingConfiguration bitiş noktası adresinden ve bağlamadan adından kaldırılarak gerçekleştirilebilir.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\< bağlama >](bindings.md)
