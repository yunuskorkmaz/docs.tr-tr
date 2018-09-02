---
title: Taşıma Güvenliği Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 9a04b8aaf9c6263a8935099963aaa1dc8d9100fd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418811"
---
# <a name="transport-security-overview"></a>Taşıma Güvenliği Genel Bakış
Aktarım güvenlik mekanizmaları Windows Communication Foundation (WCF) bağlaması ve kullanılan aktarım bağlıdır. Örneğin, kullanırken <xref:System.ServiceModel.WSHttpBinding> sınıfı taşıma HTTP ve taşıma güvenliğini sağlamak için birincil mekanizma Güvenli Yuva Katmanı (SSL) yaygın olarak HTTPS adlı HTTP üzerinden. Bu konu, WCF sistem tarafından sağlanan bağlamalar kullanılan ana Aktarım güvenlik mekanizmalarını açıklar.  
  
> [!NOTE]
>  SSL güvenlik .NET Framework 3.5 ve üzeri kullanıldığında bir WCF istemcisi hem Ara sertifikaları, sertifika deposunda kullanır ve hizmetin üzerinde sertifika zinciri doğrulamayı gerçekleştirmek için SSL anlaşması sırasında Ara sertifikaları alındı Sertifika. .NET framework 3.0, yalnızca yerel sertifika deposunda yüklü Ara sertifikaları kullanır.  
  
> [!WARNING]
>  Aktarım güvenliği kullanıldığında <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` özelliği yazılabilir. Bunun gerçekleşmesini kümesinden önlemek için <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` yok. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Hizmet açıklaması üzerinde ayarlanabilir bir hizmet davranıştır.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sınıfı, güvenlik sağlamaz. Bu bağlama, güvenlik uygulamayan Web hizmeti sağlayıcıları ile birlikte çalışabilirlik için tasarlanmıştır. Ancak, ayarlayarak güvenliği geçiş yapabilirsiniz <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> dışında bir değer özelliği <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Aktarım güvenliği etkinleştirmek için özelliği ayarlamak <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>IIS ile birlikte çalışma  
 <xref:System.ServiceModel.BasicHttpBinding> Sınıfı öncelikle var olan Web Hizmetleri ile çalışmak için kullanılır ve bu hizmetlerin çoğu Internet Information Services (IIS) tarafından barındırılır. Sonuç olarak, bu bağlama için Aktarım güvenliği, IIS siteleri ile sorunsuz bir birlikte çalışma için tasarlanmıştır. Bu güvenlik modunu ayarlayarak yapılır <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> ve ardından istemci ayar kimlik bilgisi türü. Kimlik bilgisi türü değerleri IIS dizin güvenlik mekanizmalarına karşılık gelir. Aşağıdaki kod ayarlanan modunu gösterir ve Windows için kimlik bilgisi türü ayarlayın. İstemci ve sunucu aynı Windows etki alanında olduğunda, bu yapılandırmayı kullanabilirsiniz.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Veya, yapılandırma:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Aşağıdaki bölümlerde, diğer istemci kimlik bilgisi türleri açıklanmaktadır.  
  
#### <a name="basic"></a>Temel  
 IIS temel kimlik doğrulaması yöntemine karşılık gelir. Bu modu kullanırken, IIS sunucusunun Windows kullanıcı hesapları ve uygun NTFS dosya sistemi izinleri ile yapılandırılması gerekir. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [temel kimlik doğrulamasını etkinleştirme ve bölge adını yapılandırma](https://go.microsoft.com/fwlink/?LinkId=88592). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: temel kimlik doğrulamasını yapılandırma](https://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>Sertifika  
 IIS gerektiren bir sertifika ile oturum açmak istemcileri seçeneği vardır. Özelliği, bir Windows hesabı için bir istemci sertifikası eşlemek IIS de sağlar. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [istemci sertifikalarını etkinleştirme IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88594). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Özet  
 Özet kimlik doğrulaması temel kimlik doğrulaması için benzer, ancak kimlik bilgileri gönderme düz metin olarak bir karma yerine avantajı sunar. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [Özet kimlik doğrulaması IIS 6.0](https://go.microsoft.com/fwlink/?LinkID=88443). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: Özet kimlik doğrulamasını yapılandırma](https://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Bu IIS tümleşik Windows kimlik doğrulaması karşılık gelir. Bu değer ayarlandığında, sunucunun da kendi etki alanı denetleyicisi olarak Kerberos protokolünü kullanan bir Windows etki alanında mevcut bekleniyor. Sunucu, Kerberos tarafından desteklenen bir etki alanı üzerinde değil veya Kerberos sistem başarısız olursa, sonraki bölümde açıklanan NT LAN Manager (NTLM) değeri kullanabilirsiniz. Hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [IIS 6. 0'tümleşik Windows kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88597). Hakkında daha fazla bilgi için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Bu, Kerberos protokolü başarısız olursa NTLM kimlik doğrulaması için kullanılacak sunucunun sağlar. IIS yapılandırma hakkında daha fazla bilgi için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [zorlama NTLM kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88598). İçin [!INCLUDE[iisver](../../../../includes/iisver-md.md)], NTLM kimlik doğrulaması Windows kimlik doğrulaması içerir. Daha fazla bilgi için [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](https://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> Sınıfı WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmıştır * belirtimleri. Bu bağlama için Aktarım güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) olan. SSL kullanan bir WCF uygulama oluşturmak için uygulamayı barındırmak için IIS kullanın. Şirket içinde barındırılan bir uygulama oluşturuyorsanız, alternatif olarak, bir bilgisayardaki belirli bir bağlantı noktası için bir X.509 sertifikası bağlamak için HttpCfg.exe Aracı'nı kullanın. Uç nokta adresi olarak WCF uygulaması bir parçası olarak belirtilen bir bağlantı noktası numarası. Çalışma zamanında bir özel durum oluşturulur veya aktarım modunu kullanırken, uç nokta adresini HTTPS protokolünü içermelidir. Daha fazla bilgi için [HTTP aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 İstemci kimlik doğrulaması için ayarlanmış <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.HttpTransportSecurity> sınıfı birine <xref:System.ServiceModel.HttpClientCredentialType> sabit listesi değerleri. Sabit listesi değerleri için istemci kimlik bilgisi türlerinin aynı <xref:System.ServiceModel.BasicHttpBinding> ve IIS hizmetleri ile barındırılması için tasarlanmıştır.  
  
 Aşağıdaki örnek, bir Windows istemci kimlik bilgisi türüyle kullanılan bağlama gösterir.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Bu bağlama, yalnızca ileti düzeyi güvenlik, aktarım düzeyinde güvenlik sağlar.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> Sınıfı, ileti aktarım için TCP kullanır. Aktarım modu için güvenlik, TCP üzerinden Aktarım Katmanı Güvenliği (TLS) uygulayarak sağlanır. TLS uygulaması, işletim sistemi tarafından sağlanır.  
  
 Ayarlayarak istemcinin kimlik bilgisi türü belirtebilirsiniz <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.TcpTransportSecurity> sınıfı birine <xref:System.ServiceModel.TcpClientCredentialType> , aşağıdaki kodda gösterildiği gibi değerleri.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>İstemci  
 İstemcide, bir sertifika kullanarak belirtmelisiniz <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.  
  
> [!NOTE]
>  Windows Güvenlik kullanıyorsanız, bir sertifika gerekli değildir.  
  
 Aşağıdaki kodu, benzersiz olarak tanımlayan sertifikanın parmak izini kullanır. Sertifikalar hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatif olarak, istemci yapılandırması'nda sertifika belirtin kullanarak bir [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) davranışları bölümünde öğesi.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding> Sınıf içi makine verimli iletişimi için tasarlanmıştır; diğer bir deyişle, işlemler için adlandırılmış kanal kanalları olsa da aynı bilgisayarda çalışan aynı ağda iki bilgisayar arasında oluşturulabilir. Bu bağlama yalnızca aktarım düzeyi güvenlik sağlar. Bu bağlamayı kullanan uygulamalar oluştururken, uç nokta adresleri uç nokta adresi protokol olarak "net.pipe" içermelidir.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Bu bağlama SSL Aktarım güvenliği kullanarak, HTTP, HTTPS verilen bir belirteç ile bilinen kullanır. (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Federasyon uygulamaları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> Eşler arası ağ özelliğini kullanarak verimli iletişimi için tasarlanan bir güvenli aktarım sınıftır. Bağlama ve sınıf adına göre gösterildiği gibi TCP protokolüdür. Güvenlik modu için aktarım olarak ayarlandığında, bağlama TLS TCP uygular. Eşler arası özelliği hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding ve NetMsmqBinding  
 Taşıma tam bir açıklaması için bkz: ileti sıraya alma (daha önce MSMQ olarak da bilinir) ile güvenlik [aktarım güvenliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
