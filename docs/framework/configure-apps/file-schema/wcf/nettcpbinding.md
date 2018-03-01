---
title: '&lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 057baf6d18cba61c0ceeb7d5152edcf082392310
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltnettcpbindinggt"></a>&lt;netTcpBinding&gt;
Güvenli, güvenilir ve en iyi duruma getirilmiş bağlama makineler arası iletişim için uygun belirtir. Varsayılan olarak, bir çalışma zamanı iletişim yığını Windows güvenliği ile ileti güvenliği ve kimlik doğrulama, ileti teslimi ve ikili ileti kodlama için TCP oluşturur.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netTcpBinding>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
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
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|hostnameComparisonMode|URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir. Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer `StrongWildcard`, eşleşme ana bilgisayar adı yok sayar.|  
|listenBacklog|Bir pozitif tamsayı kabul edilmesi için dinleyici bekleyen kanalları en fazla sayısını belirtir. Bu sınırı aşan bağlantılar, sınırın altındaki alan kullanılabilir duruma gelinceye kadar kuyruğa alınır. `connectionTimeout` Öznitelik, bir istemci bağlantı özel durumuyla atmadan önce bağlanması için bekleyeceği süreyi sınırlar. Varsayılan değer 10'dur.|  
|maxBufferPoolSize|Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı. Varsayılan 512 * 1024 bayt'tır. Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın. Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır. Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez. Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.|  
|maxBufferSize|Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirtir pozitif bir tamsayı.<br /><br /> Varsa `transferMode` özniteliği eşittir için `Buffered`, bu öznitelik eşit olmalıdır `maxReceivedMessageSize` öznitelik değeri.<br /><br /> Varsa `transferMode` özniteliği eşittir için `Streamed`, bu öznitelik olamaz birden fazla `maxReceivedMessageSize` öznitelik değeri ve üst bilgilerin boyutu en az olmalıdır.<br /><br /> 65536 varsayılandır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet Oluştur/kabul eder. Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınır karşı sayılır.<br /><br /> Sınırı aşan gelen bağlantıları sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.<br /><br /> Sınırı aşan giden bağlantılar sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.<br /><br /> Varsayılan değer 10'dur.|  
|maxReceivedMessageSize|Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır.|  
|name|Bağlama yapılandırma adını içeren dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|portSharingEnabled|TCP bağlantı noktası paylaşma Bu bağlantı için etkin olup olmadığını belirten bir Boole değeri. Bu ise `false`, her bağlama kendi özel bağlantı noktasını kullanır. Bu ayar yalnızca hizmetler için ilgili nedeni istemcileri etkilenmez.|  
|receiveTimeout|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10: 00'dır.|  
|sendTimeout|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|transactionFlow|Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|transactionProtocol|Bu bağlama ile kullanılmak üzere işlem protokolü belirtir. Geçerli değerler:<br /><br /> -   OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> OleTransactions varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.|  
|transferMode|A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten değeri veya yanıt.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Güvenilir oturumlar kanal uç noktaları arasında kurulan olmadığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bağlama taşıma güvenliği, ileti teslimi için TCP ve ikili ileti kodlama kullanan varsayılan olarak, bir çalışma zamanı iletişim yığını oluşturur. Bu bağlamanın uygun olduğu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Intranet üzerinden iletişim kurmak için sistem tarafından sağlanan seçimdir.  
  
 İçin varsayılan yapılandırmayı `netTcpBinding` tarafından sağlanan yapılandırma daha hızlıdır `wsHttpBinding`, ancak yalnızca için hazırlanmıştır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]- için -[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] iletişim. Güvenlik davranıştır isteğe bağlı kullanılarak yapılandırılabilir `securityMode` özniteliği. WS-ReliableMessaging kullanımını isteğe bağlı kullanılarak yapılandırılabilir `reliableSessionEnabled` özniteliği. Ancak güvenilir Mesajlaşma varsayılan olarak kapalıdır. Daha fazla genel olarak, HTTP sistem tarafından sağlanan bağlamalar gibi `wsHttpBinding` ve `basicHttpBinding` varsayılan olarak, öğeleri açmak için kullanılabilirken yapılandırılmış olan `netTcpBinding` bağlama kapanmadan şeyler varsayılan olarak, destek, örneğin, aşağıdakilerden birini alınacak katılımı gerekir böylece WS-* belirtimleri. Bu, TCP için varsayılan yapılandırmayı varsayılan olarak HTTP bağlantıları için yapılandırılan olandan uç noktalar arasında ileti değiş tokuşu en hızlı olduğu anlamına gelir.  
  
## <a name="example"></a>Örnek  
 Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü belirtilen `binding` özniteliği `<endpoint>` öğesi. NetTcpBinding bağını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamak gereklidir. Uç nokta ile bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği. Aşağıdaki örnekte, bir bağlama yapılandırması tanımlanır.  
  
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
    <binding   
             closeTimeout="00:01:00"  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
