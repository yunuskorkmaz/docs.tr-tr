---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 3e32539900893297d2bac232138f9940a8ab100b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557651"
---
# \<wsDualHttpBinding>
Çift yönlü hizmet sözleşmeleri veya SOAP aracıları üzerinden iletişim için uygun olan güvenli, güvenilir ve birlikte çalışabilen bir bağlama tanımlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri. Varsayılan değer: `false`.|  
|clientBaseAddress|Hizmetten gelen yanıt iletileri için istemcinin dinlediği temel adresi ayarlayan bir URI. Belirtilmişse, bu adres (artı bir channelGUID) dinlemek için kullanılır. Değer belirtilmezse, istemci taban adresi, aktarıma özgü bir şekilde oluşturulur. Varsayılan değer: `null`.|  
|closeTimeout|<xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|hostnameComparisonMode|URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür. Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.|  
|maxBufferPoolSize|Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı. Varsayılan değer 524.288 bayttır (512 * 1024). Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır. Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.|  
|Değerini|Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir.|  
|messageEncoding|İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metin: bir metin mesajı Kodlayıcısı kullanın.<br />-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.<br />-Varsayılan metindir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .|  
|name|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|openTimeout|Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|proxyAddress|HTTP proxy adresini belirten bir URI. `useDefaultWebProxy`İse `true` , bu ayar olmalıdır `null` . Varsayılan değer: `null`.|  
|receiveTimeout|<xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|Binding üstündeki SendTimeout|<xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|  
|Kodkodu kodlama|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -Bigendianunıcode: Unicode Bigenyen kodlaması.<br />-UNICODE: 16 bit kodlama.<br />-UTF8:8 bit kodlama<br /><br /> Varsayılan değer UTF8 ' dir. Bu öznitelik türü <xref:System.Text.Encoding> .|  
|transactionFlow|Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan değer: `false`.|  
|useDefaultWebProxy|Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir Boole değeri. Bu öznitelik ise, ara sunucu adresi `null` (ayarlı değil) olmalıdır `true` . Varsayılan değer: `true`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement> .|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 , `WSDualHttpBinding` Web hizmeti protokolleri için aynı desteği, `WSHttpBinding` ancak çift yönlü sözleşmelerle birlikte kullanmak için sağlar. `WSDualHttpBinding` yalnızca SOAP güvenliğini destekler ve güvenilir mesajlaşma gerektirir. Bu bağlama, istemcinin hizmet için bir geri çağırma uç noktası sağlayan ortak bir URI 'ye sahip olmasını gerektirir. Bu, özniteliği tarafından sağlanır `clientBaseAddress` . İkili bağlama, istemcinin IP adresini hizmete gösterir. İstemci, yalnızca güvendiği hizmetlere bağlanmasını sağlamak için güvenliği kullanmalıdır.  
  
 Bu bağlama, bir veya daha fazla SOAP aracıları aracılığıyla güvenilir bir şekilde iletişim kurmak için kullanılabilir.  
  
 Bu bağlama, varsayılan olarak, güvenilirlik için WS-ReliableMessaging ile bir çalışma zamanı yığını, ileti güvenliği için WS-Security ve kimlik doğrulaması, ileti teslimi için HTTP ve metin/XML iletisi kodlaması oluşturur.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
