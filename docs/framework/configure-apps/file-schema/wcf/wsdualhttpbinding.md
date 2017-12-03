---
title: '&lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d7a6cd2d1a5028463d6d9b4b492c88707f08145
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsdualhttpbindinggt"></a>&lt;wsDualHttpBinding&gt;
Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli, güvenilir ve birlikte çalışabilir bağlama tanımlar.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<wsDualHttpBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
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
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.|  
|clientBaseAddress|İstemci yanıt iletileri hizmetinden dinler temel adresini ayarlar URI. Belirtilmişse, bu adres (artı bir başına-channelGUID) dinlemek için kullanılır. Değer belirtilmezse, istemci taban adresi aktarım özgü bir şekilde oluşturulur. Varsayılan, `null` değeridir.|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|hostnameComparisonMode|URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.|  
|maxBufferPoolSize|Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı. Varsayılan 524.288 (512 * 1024) bayttır. Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın. Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır. Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez. Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.|  
|MaxReceivedMessageSize|Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır.|  
|messageEncoding|İleti kodlanması için kullanılan Kodlayıcı tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metin: metin ileti Kodlayıcı kullanın.<br />-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.<br />-Varsayılan metindir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Bağlama yapılandırma adını içeren dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|proxyAddress|HTTP proxy adresini belirtir URI. Varsa `useDefaultWebProxy` olan `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|receiveTimeout|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|sendTimeout|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|textEncoding|Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar. Geçerli değerler şunlardır:<br /><br /> -BigEndianUnicode: Unicode BigEndian kodlama.<br />-Unicode: 16 bit kodlama.<br />-UTF8: 8 bit kodlama<br /><br /> UTF8 varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>.|  
|transactionFlow|Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|useDefaultWebProxy|Sistemin otomatik yapılandırılan HTTP Proxy'si kullanılıp kullanılmadığını gösteren bir Boole değeri. Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlanmamış) bu özniteliği ise `true`. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Güvenilir oturumlar kanal uç noktaları arasında kurulan olmadığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `WSDualHttpBinding` Web hizmeti protokolleri aynı destek sağlayan `WSHttpBinding`, ancak çift yönlü sözleşmeler ile kullanım için. `WSDualHttpBinding`yalnızca SOAP Güvenliği destekler ve güvenilir Mesajlaşma gerektirir. Bu bağlama istemci hizmeti için bir geri çağırma uç noktası sağlayan ortak bir URI sahip olması gerekir. Bu tarafından sağlanan `clientBaseAddress` özniteliği. Bir çift bağlama hizmeti istemcinin IP adresini gösterir. İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.  
  
 Bu bağlama, güvenilir bir şekilde bir veya daha fazla SOAP aracılar iletişim kurmak için kullanılabilir.  
  
 Varsayılan olarak, WS-ReliableMessaging çalışma zamanı yığın güvenilirlik, WS-güvenlik ileti güvenliği ve kimlik doğrulama, ileti teslimi, HTTP için bu bağlama oluşturur ve bir Text/XML ileti kodlama.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
