---
title: Taşıma Güvenliği Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: f30b2c587d7f9b21c1f19fa1c3943621fc2607cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184336"
---
# <a name="transport-security-overview"></a>Taşıma Güvenliği Genel Bakış
Windows Communication Foundation'daki (WCF) taşıma güvenlik mekanizmaları, kullanılan bağlama ve aktarıma bağlıdır. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfı kullanırken aktarım HTTP'dir ve aktarımgüvenliğini sağlamak için birincil mekanizma HTTP üzerinden Güvenli Soketler Katmanıdır (SSL), genellikle HTTPS olarak adlandırılır. Bu konu, WCF sistemi tarafından sağlanan bağlamalarda kullanılan başlıca taşıma güvenlik mekanizmalarını tartışır.  
  
> [!NOTE]
> SSL güvenliği .NET Framework 3.5 ile kullanıldığında ve daha sonra bir WCF istemcisi, hizmetin sertifikası üzerinde sertifika zinciri doğrulaması gerçekleştirmek için SSL anlaşması sırasında alınan ara sertifikaları hem de ara sertifikaları kullanır Sertifika. .NET Framework 3.0 yalnızca yerel sertifika deposuna yüklenen ara sertifikaları kullanır.  
  
> [!WARNING]
> Aktarım güvenliği kullanıldığında, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özellik üzerine yazılabilir. Bunun olmasını önlemek <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> için. <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>hizmet açıklamasında ayarlanabilen bir hizmet davranışıdır.  
  
## <a name="basichttpbinding"></a>Temel https://r  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sınıf güvenlik sağlamaz. Bu bağlama, güvenliği uygulamayan Web servis sağlayıcılarıyla birlikte çalışabilirlik için tasarlanmıştır. Ancak, <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> özelliği hariç <xref:System.ServiceModel.BasicHttpSecurityMode.None>herhangi bir değere ayarlayarak güvenliği açabilirsiniz. Aktarım güvenliğini etkinleştirmek için <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>özelliği ' ye göre ayarlayın.  
  
### <a name="interoperation-with-iis"></a>IIS ile Etkileşim  
 Sınıf <xref:System.ServiceModel.BasicHttpBinding> öncelikle varolan Web hizmetleriyle birlikte çalışmak için kullanılır ve bu hizmetlerin çoğu Internet Information Services (IIS) tarafından barındırılır. Sonuç olarak, bu bağlama için taşıma güvenliği IIS siteleri ile sorunsuz bir şekilde etkileşim için tasarlanmıştır. Bu, güvenlik modunu ayarlayarak <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> ve istemci kimlik bilgisi türünü ayarlayarak yapılır. Kimlik bilgisi türü değerleri IIS dizin güvenlik mekanizmalarına karşılık gelir. Aşağıdaki kod, ayarlanan modu ve Windows'a kimlik bilgisi türünü kümesini gösterir. Hem istemci hem de sunucu aynı Windows etki alanındayken bu yapılandırmayı kullanabilirsiniz.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)]
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Veya yapılandırmada:  
  
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
  
 Aşağıdaki bölümlerde diğer istemci kimlik bilgileri türleri tartışılır.  
  
#### <a name="basic"></a>Temel  
 Bu, IIS'deki Temel kimlik doğrulama yöntemine karşılık gelir. Bu modu kullanırken, IIS sunucusunun Windows kullanıcı hesapları ve uygun NTFS dosya sistemi izinleri ile yapılandırılması gerekir. IIS 6.0 hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)) IIS 7.0 hakkında daha fazla bilgi için [temel kimlik doğrulamayı yapılandırma (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10))'ye bakın.  
  
#### <a name="certificate"></a>Sertifika  
 IIS istemcilerin bir sertifika ile oturum açmalarını gerektiren bir seçenek vardır. Bu özellik, IIS'nin bir istemci sertifikasını bir Windows hesabına eşlemesini de sağlar. IIS 6.0 hakkında daha fazla bilgi için [IIS 6.0'daki İstemci Sertifikalarını Etkinleştirme'ye](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10))bakın. IIS 7.0 hakkında daha fazla bilgi için [IIS 7'deki Sunucu Sertifikalarını Yapılandırma'ya](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))bakın.  
  
#### <a name="digest"></a>Özet  
 Özet kimlik doğrulaması Temel kimlik doğrulamasına benzer, ancak kimlik bilgilerini açık metin yerine karma olarak gönderme avantajı sunar. IIS 6.0 hakkında daha fazla bilgi için [IIS 6.0'daki Özet Kimlik Doğrulama'ya](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))bakın. IIS 7.0 hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10))  
  
#### <a name="windows"></a>Windows  
 Bu, IIS'deki tümleşik Windows kimlik doğrulamasına karşılık gelir. Bu değere ayarlandığında, sunucunun etki alanı denetleyicisi olarak Kerberos protokolünü kullanan bir Windows etki alanında da bulunması beklenir. Sunucu Kerberos destekli bir etki alanında değilse veya Kerberos sistemi başarısız olursa, bir sonraki bölümde açıklanan NT LAN Yöneticisi (NTLM) değerini kullanabilirsiniz. IIS 6.0 hakkında daha fazla bilgi için [IIS 6.0'daki Tümleşik Windows Kimlik Doğrulaması'na](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10))bakın. IIS 7.0 hakkında daha fazla bilgi için [IIS 7'deki Sunucu Sertifikalarını Yapılandırma'ya](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))bakın.
  
#### <a name="ntlm"></a>NTLM  
 Bu, Kerberos protokolü başarısız olursa, sunucunun kimlik doğrulaması için NTLM kullanmasını sağlar. IIS 6.0'da IIS yapılandırma hakkında daha fazla bilgi için [Bkz. NTLM Kimlik Doğrulamayı Zorlama.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)) IIS 7.0 için Windows kimlik doğrulaması NTLM kimlik doğrulamasını içerir. Daha fazla bilgi için [IIS 7'deki Sunucu Sertifikalarını Yapılandırma'ya](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))bakın.
  
## <a name="wshttpbinding"></a>wshttpbinding  
 Sınıf, <xref:System.ServiceModel.WSHttpBinding> WS-* spesifikasyonlarını uygulayan hizmetlerle birlikte çalışma için tasarlanmıştır. Bu bağlama için aktarım güvenliği HTTP veya HTTPS üzerinden Secure Sockets Layer (SSL) olur. SSL kullanan bir WCF uygulaması oluşturmak için uygulamayı barındırmak için IIS'yi kullanın. Alternatif olarak, kendi kendine barındırılan bir uygulama oluşturuyorsanız, X.509 sertifikasını bilgisayardaki belirli bir bağlantı noktasına bağlamak için HttpCfg.exe aracını kullanın. Bağlantı noktası numarası, bitiş noktası adresi olarak WCF uygulamasının bir parçası olarak belirtilir. Aktarım modunu kullanırken, bitiş noktası adresi HTTPS protokolünü içermelidir veya çalışma zamanında bir özel durum atılır. Daha fazla bilgi için [HTTP Transport Security'ye](../../../../docs/framework/wcf/feature-details/http-transport-security.md)bakın.  
  
 İstemci kimlik doğrulaması için sınıfın <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliğini <xref:System.ServiceModel.HttpTransportSecurity> numaralandırma değerlerinden <xref:System.ServiceModel.HttpClientCredentialType> birine ayarlayın. Numaralandırma değerleri, istemci kimlik bilgileri türleri ile <xref:System.ServiceModel.BasicHttpBinding> aynıdır ve IIS hizmetleriyle barındırılmak üzere tasarlanmıştır.  
  
 Aşağıdaki örnek, istemci kimlik bilgisi türüyle kullanılan bağlamayı gösterir.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualhttpbinding  
 Bu bağlama yalnızca ileti düzeyinde güvenlik sağlar, aktarım düzeyinde güvenlik değil.  
  
## <a name="nettcpbinding"></a>NetTcpBağlama  
 Sınıf <xref:System.ServiceModel.NetTcpBinding> ileti aktarım için TCP kullanır. Aktarım moduiçin güvenlik, TCP üzerinden Aktarım Katmanı Güvenliği (TLS) uygulanarak sağlanır. TLS uygulaması işletim sistemi tarafından sağlanır.  
  
 Sınıfın <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> özelliğini <xref:System.ServiceModel.TcpTransportSecurity> aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.TcpClientCredentialType> değerlerden birine ayarlayarak istemcinin kimlik türünü de belirtebilirsiniz.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>İstemci  
 İstemci üzerinde, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfın yöntemini kullanarak bir sertifika belirtmeniz gerekir.  
  
> [!NOTE]
> Windows güvenlik kullanıyorsanız, bir sertifika gerekli değildir.  
  
 Aşağıdaki kod, sertifikayı benzersiz olarak tanımlayan sertifikanın parmak izini kullanır. Sertifikalar hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatif olarak, istemcinin yapılandırmasında davranışlar [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) bölümünde bir istemci kimlik bilgileri>öğesi kullanarak sertifikayı belirtin.  
  
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
 Sınıf <xref:System.ServiceModel.NetNamedPipeBinding> verimli makine içi iletişim için tasarlanmıştır; adlandırılmış boru kanalları aynı ağdaki iki bilgisayar arasında oluşturulabilir rağmen, aynı bilgisayarda çalışan işlemler için. Bu bağlama yalnızca aktarım düzeyinde güvenlik sağlar. Bu bağlama yı kullanarak uygulamalar oluştururken, uç nokta adresleri bitiş noktası adresinin protokolü olarak "net.pipe" içermelidir.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationhttpBinding  
 Aktarım güvenliğini kullanırken, bu bağlama, verilen bir belirteçle<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>HTTPS olarak bilinen HTTP üzerinden SSL kullanır. Federasyon uygulamaları hakkında daha fazla bilgi için [Federasyon ve İhraç Jetonları'na](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)bakın.  
  
## <a name="netpeertcpbinding"></a>Netpeertcpbinding  
 Sınıf, <xref:System.ServiceModel.NetPeerTcpBinding> eşler arası ağ özelliğini kullanarak verimli iletişim için tasarlanmış güvenli bir aktarımdır. Sınıfın adı ve bağlama ile gösterildiği gibi, TCP protokoldür. Güvenlik modu Aktarım olarak ayarlandığında, bağlama TCP üzerinden TLS uygular. Eşler arası özellik hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding ve NetMsmqBinding  
 İleti Sıralaması (daha önce MSMQ olarak adlandırılır) ile aktarım güvenliğinin tam bir tartışması için, [Aktarım Güvenliğini Kullanarak İletileri Güvence Altına Alma](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
