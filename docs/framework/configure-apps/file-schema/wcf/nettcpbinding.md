---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: cbe2ae5923e4cd46abadc7103655dea410a97b60
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258051"
---
# <a name="nettcpbinding"></a>\<netTcpBinding>

Çapraz makine haberleşmesi için güvenli, güvenilir ve iyileştirilmiş bağlama belirtir. Varsayılan olarak, bir çalışma zamanı iletişim yığını Windows güvenliği ile ileti güvenliği ve kimlik doğrulaması, ileti teslimi ve ikili ileti kodlama için TCP oluşturur.

\<system.ServiceModel>  
\<bağlamaları >  
\<netTcpBinding>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
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
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`hostnameComparisonMode`|URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer `StrongWildcard`, ana bilgisayar adı eşleşme yok sayar.|  
|`listenBacklog`|En fazla kabul edilmesi için Dinleyicide bekleyen kanal sayısını belirten pozitif bir tamsayı. Bu sınırı aşan bağlantılar, sınırın altına alan kullanılabilir duruma gelene kadar kuyruğa alınır. `connectionTimeout` Öznitelik, bir istemci, bağlantı özel durumuyla atamadan önce bağlanması için bekleyeceği süre sınırlar. Varsayılan değer 10'dur.|  
|`maxBufferPoolSize`|Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı. Varsayılan değer 512 * 1024 bayt'tır. Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|  
|`maxBufferSize`|Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.<br /><br /> Varsa `transferMode` özniteliği eşittir için `Buffered`, bu öznitelik eşit olmalıdır `maxReceivedMessageSize` öznitelik değeri.<br /><br /> Varsa `transferMode` özniteliği eşittir için `Streamed`, bu öznitelik birden fazla `maxReceivedMessageSize` öznitelik değeri ve üst bilgilerin boyutu en az olmalıdır.<br /><br /> 65536 varsayılandır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|`maxConnections`|En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet oluşturma/kabul eder. Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınırına göre sayılır.<br /><br /> Sınırı aşan bir gelen bağlantı sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.<br /><br /> Sınırı aşan giden bağlantılar sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.<br /><br /> Varsayılan değer 10'dur.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır.|  
|`name`|Bağlama yapılandırma adını içeren bir dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`portSharingEnabled`|Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri. Bu ise `false`, her bir bağlaması, kendi özel bağlantı noktasını kullanır. Bu ayar yalnızca hizmetler için ilgili çünkü istemciler etkilenmez.|  
|`receiveTimeout`|A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10:00 ' dir.|  
|`sendTimeout`|A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`transactionFlow`|WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`transactionProtocol`|Bu bağlama ile kullanılacak işlem protokolünü belirler. Geçerli değerler:<br /><br /> -OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> OleTransactions varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.|  
|`transferMode`|A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.|  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Güvenilir oturumlar bir kanal uç noktaları arasında yapıldığını belirtir.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](bindings.md)|Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.|  
  
## <a name="remarks"></a>Açıklamalar

Bu bağlama, aktarım güvenliği, ileti teslimi için TCP ve bir ikili ileti kodlama kullanan varsayılan olarak, bir çalışma zamanı iletişim yığını oluşturur. Bu bağlama Intranet üzerinden iletişim için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanan seçimdir.  
  
 İçin varsayılan yapılandırma `netTcpBinding` tarafından sağlanan yapılandırma daha hızlıdır `wsHttpBinding`, ancak yalnızca WCF iletişim için tasarlanmıştır. Güvenlik davranıştır isteğe bağlı kullanılarak yapılandırılabilir `securityMode` özniteliği. İsteğe bağlı kullanılarak yapılandırılabilir WS-ReliableMessaging kullanımını `reliableSessionEnabled` özniteliği. Ancak, güvenilir Mesajlaşma varsayılan olarak kapalıdır. Daha genel HTTP sistem tarafından sağlanan bağlamalar gibi `wsHttpBinding` ve `basicHttpBinding` öğeleri varsayılan olarak, açmak için ise yapılandırılmış `netTcpBinding` bağlama kapanmadan öğeleri varsayılan olarak biri için destek, örneğin, alma katılımı sahip WS-* belirtimleri. Bu, TCP için varsayılan yapılandırma varsayılan olarak HTTP bağlantıları için yapılandırılan daha uç noktalar arasında mesaj alışverişleri sırasında daha hızlı olduğunu gösterir.  
  
## <a name="example"></a>Örnek

İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi. Bağlama türü belirtilen `binding` özniteliği `<endpoint>` öğesi. NetTcpBinding yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırmasını tanımlamak gereklidir. Uç nokta ile bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği. Aşağıdaki örnekte, bir bağlama yapılandırmasını tanımlanır.  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
