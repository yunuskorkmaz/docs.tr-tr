---
title: '&lt;netTcpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1d4715e1-5fff-4c3d-a226-18f21d0b30c4
ms.openlocfilehash: da769e57a44880d5050b06a8e2a3d317daff35d6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146075"
---
# <a name="ltnettcpcontextbindinggt"></a>&lt;netTcpContextBinding&gt;
İçin bir bağlam belirtir <xref:System.ServiceModel.NetTcpBinding> koruma düzeyi imzalanması gerektiren. ContextExchangeMechanism NetTcpContextBinding için SOAPHeader ' dir.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netTcpContextBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netTcpContextBinding>
  <binding closeTimeout="TimeSpan"
           contextProtectionLevel="EncryptAndSign/None/Sign"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="String"
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 defaultRealm="String" />
      <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpContextBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|contextProtectionLevel|Geçerli bir <xref:System.Net.Security.ProtectionLevel> istenen koruma düzeyi bilgileri yaymak için kullanılan SOAP üst bilgisi belirten bir değer.  Varsayılan değer `Sign` şeklindedir.|  
|hostnameComparisonMode|URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer `StrongWildcard`, ana bilgisayar adı eşleşme yok sayar.|  
|listenBacklog|En fazla kabul edilmesi için Dinleyicide bekleyen kanal sayısını belirten pozitif bir tamsayı. Bu sınırı aşan bağlantılar, sınırın altına alan kullanılabilir duruma gelene kadar kuyruğa alınır. `connectionTimeout` Öznitelik, bir istemci, bağlantı özel durumuyla atamadan önce bağlanması için bekleyeceği süre sınırlar. Varsayılan değer 10'dur.|  
|maxBufferPoolSize|Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı. Varsayılan değer 512 * 1024 bayt'tır. Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|  
|maxBufferSize|Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı. Arabelleği dolu ise, arabellek odası yeniden sahip oluncaya kadar fazlalık veri temel alınan yuvaya kalır. Bu değer olamaz küçüktür `maxReceivedMessageSize` özniteliği. 65536 varsayılandır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|MaxConnections|En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet oluşturma/kabul eder. Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınırına göre sayılır.<br /><br /> Sınırı aşan bir gelen bağlantı sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.<br /><br /> Sınırı aşan giden bağlantılar sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.<br /><br /> Varsayılan değer 10'dur.|  
|maxReceivedMessageSize|Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır.|  
|name|Bağlama yapılandırma adını içeren bir dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|opentimeout =|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|portSharingEnabled|Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri. Bu ise `false`, her bir bağlaması, kendi özel bağlantı noktasını kullanır. Bu ayar yalnızca hizmetler için ilgili çünkü istemciler etkilenmez.|  
|receiveTimeout|A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10:00 ' dir.|  
|SendTimeout|A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|transactionFlow|WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|transactionProtocol|Bu bağlama ile kullanılacak işlem protokolünü belirler. Geçerli değerler:<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> OleTransactions varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Güvenilir oturumlar bir kanal uç noktaları arasında yapıldığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.NetTcpContextBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
