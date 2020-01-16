---
title: Bağlamalar ve Güvenlik
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 63d3888df364d033b17972a5fd3ba3b851e00c42
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964434"
---
# <a name="bindings-and-security"></a>Bağlamalar ve Güvenlik

Windows Communication Foundation (WCF) ile birlikte bulunan sistem tarafından sağlanan bağlamalar, WCF uygulamalarının programlanma için hızlı bir yol sunar. Tek bir istisna ile, tüm bağlamaların varsayılan bir güvenlik şeması etkinleştirilmiştir. Bu konu, güvenlik gereksinimleriniz için doğru bağlamayı seçmenize yardımcı olur.

WCF güvenliğine genel bakış için bkz. [Güvenliğe genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). Bağlamaları kullanarak WCF programlama hakkında daha fazla bilgi için bkz. [programlama WCF güvenliği](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).

Zaten bir bağlama seçtiyseniz, güvenlik [davranışlarıyla](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)ilişkili çalışma zamanı davranışları hakkında daha fazla bilgi edinebilirsiniz.

Bazı güvenlik işlevleri, sistem tarafından belirtilen bağlamalar kullanılarak programlanabilir değildir. Özel bağlama kullanarak daha fazla denetim için bkz. [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).

## <a name="security-functions-of-bindings"></a>Bağlamaların güvenlik Işlevleri

WCF, çoğu ihtiyacı karşılayan sistem tarafından sağlanmış birçok bağlama içerir. Belirli bir bağlama yeterli değilse, özel bir bağlama da oluşturabilirsiniz. Sistem tarafından sunulan bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md). Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).

WCF 'deki her bağlamanın iki formu vardır: bir API ve bir yapılandırma dosyasında kullanılan XML öğesi olarak. Örneğin, `WSHttpBinding` (API) [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)karşılık gelen bir karşıdır.

Aşağıdaki bölümde her bağlama için her iki form listelenir ve güvenlik özellikleri özetlenmektedir.

### <a name="basichttp"></a>BasicHttp

Kod içinde <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanın; yapılandırma bölümünde [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)kullanın.

Bu bağlama, aşağıdakiler dahil olmak üzere var olan teknolojiler ile kullanılmak üzere tasarlanmıştır:

- ASP.NET Web Services (ASMX), sürüm 1.

- Web hizmeti geliştirmeleri (WVAS) uygulamaları.

- Web Hizmetleri birlikte çalışabilirlik (WS-ı) belirtiminde tanımlanan temel profil (<https://go.microsoft.com/fwlink/?LinkId=38955>).

- WS-ı ' de tanımlanan temel güvenlik profili.

Varsayılan olarak, bu bağlama güvenli değildir. ASMX Hizmetleri ile birlikte çalışmak için tasarlanmıştır. Güvenlik etkinleştirildiğinde bağlama, temel kimlik doğrulaması, Özet ve tümleşik Windows güvenliği gibi Internet Information Services (IIS) güvenlik mekanizmalarıyla sorunsuz birlikte çalışma için tasarlanmıştır. Daha fazla bilgi için bkz. [Aktarım güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Bu bağlama aşağıdakileri destekler:

- HTTPS aktarım güvenliği.

- HTTP temel kimlik doğrulaması.

- WS-Security.

Daha fazla bilgi için, bkz. <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType> ve <xref:System.ServiceModel.BasicHttpSecurityMode>.

### <a name="wshttpbinding"></a>WSHttpBinding

Kod içinde <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanın; yapılandırma bölümünde [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanın.

Varsayılan olarak, bu bağlama WS-Security belirtimini uygular ve WS-* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik sağlar. Şunları destekler:

- HTTPS aktarım güvenliği.

- WS-Security.

- Arayanın kimliğini doğrulamak için SOAP iletisi kimlik bilgileri güvenliği ile HTTPS aktarım koruması.

Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>ve <xref:System.ServiceModel.HttpProxyCredentialType>.

### <a name="wsdualhttpbinding"></a>WSDualHttpBinding

Kod içinde <xref:System.ServiceModel.WSDualHttpBinding> sınıfını kullanın; yapılandırma bölümünde [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)kullanın.

Bu bağlama, çift yönlü hizmet uygulamalarını etkinleştirmek için tasarlanmıştır. Bu bağlama, ileti tabanlı Aktarım güvenliği için WS-güvenlik belirtimini uygular. Aktarım güvenliği yok. Varsayılan olarak, aşağıdaki özellikleri sağlar:

- Güvenilirlik için WS-güvenilir mesajlaşma uygular.

- Aktarım güvenliği ve kimlik doğrulaması için WS-Security uygular.

- İleti teslimi için HTTP kullanır.

- Text/XML ileti kodlamasını kullanır.

 WS-Security (ileti katmanı güvenliği) kullanılarak bağlama, aşağıdaki parametreleri yapılandırmanıza olanak sağlar:

- Şifreleme algoritmasını belirleyecek güvenlik algoritması paketi.

- Aşağıdakiler için bağlama seçenekleri:

  - Hizmet kimlik bilgileri, istemcide bant dışı kullanılabilir.

  - Kanal kurulumunun bir parçası olarak hizmetten anlaşılırken hizmet kimlik bilgileri sağlama.

Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSDualHttpSecurity> ve <xref:System.ServiceModel.WSDualHttpSecurityMode>.

### <a name="nettcpbinding"></a>NetTcpBinding

Kod içinde <xref:System.ServiceModel.NetTcpBinding> sınıfını kullanın; yapılandırma bölümünde [netTcpBinding >\<](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)kullanın.

Bu bağlama, makineler arası iletişim için iyileştirilmiştir. Varsayılan olarak, aşağıdaki özelliklere sahiptir:

- Aktarım katmanı güvenliğini uygular.

- Aktarım güvenliği ve kimlik doğrulaması için Windows güvenliği 'ni kullanır.

- Taşıma için TCP kullanır.

- İkili ileti kodlamasını uygular.

- WS-güvenilir mesajlaşma uygular.

Seçenekler aşağıdakileri içerir:

- İleti katmanı güvenliği (WS-Security kullanarak).

- İleti kimlik bilgileri ile aktarım güvenliği: TCP üzerinden Aktarım Katmanı Güvenliği (TLS) tarafından belirtilen Gizlilik ve bütünlük ve WS-Security tarafından sağlanmış yetkilendirme için kimlik bilgileri.

Daha fazla bilgi için bkz. <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>ve <xref:System.ServiceModel.MessageCredentialType>.

### <a name="netnamedpipebinding"></a>NetNamedPipeBinding

Kod içinde <xref:System.ServiceModel.NetNamedPipeBinding> sınıfını kullanın; yapılandırma bölümünde [netNamedPipeBinding >\<](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)kullanın.

Bu bağlama, işlemler arası iletişim (genellikle aynı makinede) için iyileştirilmiştir. Varsayılan olarak, bu bağlama aşağıdaki özelliklere sahiptir:

- İleti aktarımı ve kimlik doğrulaması için taşıma güvenliği kullanır.

- İleti teslimi için adlandırılmış kanalları kullanır.

- İkili ileti kodlamasını uygular.

- Şifreleme ve ileti imzalama.

Seçenekler aşağıdakileri içerir:

- Windows güvenliğini kullanarak kimlik doğrulaması.

Daha fazla bilgi için bkz. <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode> ve <xref:System.ServiceModel.NamedPipeTransportSecurity>.

### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding

Kod içinde <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıfını kullanın; yapılandırma bölümünde [MsmqIntegrationBinding >\<](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)kullanın.

Bu bağlama, WCF olmayan Microsoft Message Queuing (MSMQ) uç noktaları ile birlikte çalışan WCF istemcileri ve hizmetleri oluşturmak için iyileştirilmiştir.

Varsayılan olarak, bu bağlama aktarım güvenliği kullanır ve aşağıdaki güvenlik özelliklerini sağlar:

- Güvenlik devre dışı bırakılabilir (yok).

- MSMQ taşıma güvenliği (taşıma).

Daha fazla bilgi için bkz. <xref:System.ServiceModel.NetMsmqSecurity> ve <xref:System.ServiceModel.NetMsmqSecurityMode>.

### <a name="netmsmqbinding"></a>NetMsmqBinding

Kod içinde <xref:System.ServiceModel.NetMsmqBinding> sınıfını kullanın; yapılandırma bölümünde [netMsmqBinding >\<](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)kullanın.

Bu bağlama, MSMQ sıraya alınmış ileti desteği gerektiren WCF Hizmetleri oluşturulurken kullanılmak üzere tasarlanmıştır.

Varsayılan olarak, bu bağlama aktarım güvenliği kullanır ve aşağıdaki güvenlik özelliklerini sağlar:

- Güvenlik devre dışı bırakılabilir (yok).

- MSMQ taşıma güvenliği (taşıma).

- SOAP tabanlı ileti güvenliği (Ileti).

- Eşzamanlı aktarım ve Ileti güvenliği (her Ikisi).

- Desteklenen istemci kimlik bilgileri türleri: None, Windows, UserName, Certificate, IssuedToken.

<xref:System.ServiceModel.MessageCredentialType.Certificate> kimlik bilgileri yalnızca güvenlik modu <xref:System.ServiceModel.NetMsmqSecurityMode.Both> veya <xref:System.ServiceModel.NetMsmqSecurityMode.Message>olarak ayarlandığında desteklenir.

Daha fazla bilgi için bkz. <xref:System.ServiceModel.MessageSecurityOverMsmq> ve <xref:System.ServiceModel.MsmqTransportSecurity>.

### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding

Kod içinde <xref:System.ServiceModel.WSFederationHttpBinding> sınıfını kullanın; yapılandırma bölümünde [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)kullanın.

Varsayılan olarak, bu bağlama WS-Security (ileti katmanı güvenliği) kullanır.

Daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>ve <xref:System.ServiceModel.WSFederationHttpSecurityMode>.

## <a name="custom-bindings"></a>Özel Bağlamalar

Sistem tarafından sağlanmayan bağlamalardan hiçbiri gereksinimlerinizi karşılamıyorsa, özel bir güvenlik bağlama öğesi ile özel bir bağlama oluşturabilirsiniz. Daha fazla bilgi için bkz. [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).

## <a name="binding-choices"></a>Bağlama seçimleri

Aşağıdaki tablo güvenlik modu ayarında sunulan özellikleri özetler, yani güvenlik modu `Transport`, `Message`veya `TransportWithMessageCredential`olarak ayarlandığında kullanılabilir özellikleri listeler. Uygulamanızın gerektirdiği güvenlik özelliklerini bulmanıza yardımcı olması için bu tabloyu kullanın.

|Ayar|Özellikler|
|-------------|--------------|
|Aktarma|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Noktadan noktaya güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Donanım hızlandırma<br /><br /> Yüksek işleme düzeyi<br /><br /> Güvenli güvenlik duvarı<br /><br /> Yüksek gecikmeli uygulamalar<br /><br /> Birden çok atlama genelinde yeniden şifreleme|
|İleti|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Uçtan uca güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Zengin talepler<br /><br /> Federasyon<br /><br /> Çok faktörlü kimlik doğrulaması<br /><br /> {1&gt;Özel belirteçler&lt;1}<br /><br /> Önemli/zaman damgası hizmeti<br /><br /> Yüksek gecikmeli uygulamalar<br /><br /> İleti imzalarının kalıcılığı|
|TransportWithMessageCredential|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Noktadan noktaya güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Donanım hızlandırma<br /><br /> Yüksek işleme düzeyi<br /><br /> Zengin istemci talepleri<br /><br /> Federasyon<br /><br /> Çok faktörlü kimlik doğrulaması<br /><br /> {1&gt;Özel belirteçler&lt;1}<br /><br /> Güvenli güvenlik duvarı<br /><br /> Yüksek gecikmeli uygulamalar<br /><br /> Birden çok atlama genelinde yeniden şifreleme|

Aşağıdaki tabloda, çeşitli mod ayarlarını destekleyen bağlamalar listelenmektedir. Hizmet uç noktanızı oluşturmak için kullanılacak tablodan bir bağlama seçin.

|Bağlama|Aktarım modu desteği|İleti modu desteği|TransportWithMessageCredential desteği|
|-------------|----------------------------|--------------------------|--------------------------------------------|
|`BasicHttpBinding`|Evet|Evet|Evet|
|`WSHttpBinding`|Evet|Evet|Evet|
|`WSDualHttpBinding`|Hayır|Evet|Hayır|
|`NetTcpBinding`|Evet|Evet|Evet|
|`NetNamedPipeBinding`|Evet|Hayır|Hayır|
|`NetMsmqBinding`|Evet|Evet|Hayır|
|`MsmqIntegrationBinding`|Evet|Hayır|Hayır|
|`wsFederationHttpBinding`|Hayır|Evet|Evet|

## <a name="transport-credentials-in-bindings"></a>Bağlamalarda aktarım kimlik bilgileri

Aşağıdaki tabloda, aktarım güvenliği modunda `BasicHttpBinding` veya `WSHttpBinding` kullanılırken kullanılabilen istemci kimlik bilgisi türleri listelenmektedir.

|Tür|Açıklama|
|----------|-----------------|
|Yok.|İstemcinin herhangi bir kimlik bilgisi sunması gerekmediğini belirtir. Bu, anonim bir istemciyi dönüştürür.|
|Temel|Temel kimlik doğrulaması. Daha fazla bilgi için, bkz. RFC 2617 – HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması, <https://go.microsoft.com/fwlink/?LinkId=84023>.|
|Bilgisi|Özet kimlik doğrulaması. Daha fazla bilgi için, bkz. RFC 2617 – HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması, <https://go.microsoft.com/fwlink/?LinkId=84023>.|
|NTLM|NT LAN Manager (NTLM) kimlik doğrulaması.|
|Windows|Windows kimlik doğrulaması.|
|Sertifika|Kimlik doğrulaması bir sertifika kullanılarak gerçekleştirildi.|
|IssuedToken|Hizmetin, bir güvenlik belirteci hizmeti veya CardSpace tarafından verilen bir belirteç kullanılarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|

### <a name="message-client-credentials-in-bindings"></a>Bağlamalarda ileti Istemci kimlik bilgileri

Aşağıdaki tabloda, Ileti güvenliği modunda bir bağlama kullanılırken kullanılabilen istemci kimlik bilgileri türleri listelenmektedir.

|Tür|Açıklama|
|----------|-----------------|
|Yok.|Hizmetin anonim istemcilerle etkileşime geçmesini sağlar.|
|Windows|Bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında SOAP ileti değişimlerinin yapılmasına izin verir.|
|UserName|Hizmetin, bir Kullanıcı adı kimlik bilgisi kullanılarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. Güvenlik modu `TransportWithMessageCredential`olarak ayarlandığında, WCF parola özetinin gönderilmesini veya parolayı kullanarak anahtar türemesini veya Ileti modu güvenliği için bu anahtarları kullanmayı desteklemediğini unutmayın. Bu nedenle, WCF Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli hale getirilme işlemi uygular.|
|Sertifika|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar.|
|IssuedToken|Hizmetin özel bir belirteç sağlamak için bir güvenlik belirteci hizmeti kullanmasına izin verir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Bilgisi Türü Seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Güvenlik Davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
