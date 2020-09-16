---
title: Taşıma Güvenliği Genel Bakış
description: WCF sistem tarafından belirtilen bağlamalarda önemli taşıma güvenlik mekanizmaları hakkında bilgi edinin. Bu güvenlik mekanizmaları, kullanılan bağlama ve aktarıma bağımlıdır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 8780b9c0fc06a49ddaf42166c292a41e9124f6e1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556804"
---
# <a name="transport-security-overview"></a>Taşıma Güvenliği Genel Bakış
Windows Communication Foundation (WCF) içindeki taşıma güvenliği mekanizmaları, kullanılan bağlama ve aktarıma bağlıdır. Örneğin, <xref:System.ServiceModel.WSHttpBinding> sınıfı kullanılırken aktarım http olur ve aktarımı güvenli hale getirmek için birincil MEKANIZMA http üzerinden genellıkle https olarak adlandırılır Güvenli Yuva Katmanı (SSL). Bu konuda, WCF sistem tarafından belirtilen bağlamalarda kullanılan önemli aktarım güvenliği mekanizmaları ele alınmaktadır.  
  
> [!NOTE]
> SSL güvenliği .NET Framework 3,5 ile kullanıldığında ve daha sonra bir WCF istemcisi, sertifika deposundaki ara sertifikaları ve hizmetin sertifikasında sertifika zinciri doğrulaması gerçekleştirmek için SSL anlaşması sırasında alınan ara sertifikaları kullanır. .NET Framework 3,0 yalnızca yerel sertifika deposunda yüklü olan ara sertifikaları kullanır.  
  
> [!WARNING]
> Taşıma güvenliği kullanıldığında, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliğin üzerine yazılabilir. Bunun oluşmasını engellemek için, öğesini <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> olarak ayarlayın <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType> . <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> , hizmet açıklamasında ayarlanabilir bir hizmet davranışıdır.  
  
## <a name="basichttpbinding"></a>Kullanmayı  
 Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sınıfı güvenlik sağlamaz. Bu bağlama, güvenlik uygulamayan Web hizmeti sağlayıcılarıyla birlikte çalışabilirlik için tasarlanmıştır. Ancak, <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> özelliği dışında herhangi bir değere ayarlayarak güvenlik üzerinde geçiş yapabilirsiniz <xref:System.ServiceModel.BasicHttpSecurityMode.None> . Aktarım güvenliğini etkinleştirmek için özelliğini olarak ayarlayın <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> .  
  
### <a name="interoperation-with-iis"></a>IIS ile birlikte çalışma  
 <xref:System.ServiceModel.BasicHttpBinding>Sınıf öncelikle mevcut Web hizmetleriyle birlikte çalışmak için kullanılır ve bu hizmetlerin birçoğu Internet Information Services (IIS) tarafından barındırılır. Sonuç olarak, bu bağlamanın aktarım güvenliği IIS siteleri ile sorunsuz birlikte çalışma için tasarlanmıştır. Bu, güvenlik modu olarak ayarlanarak <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> ve ardından istemci kimlik bilgisi türü ayarlanarak yapılır. Kimlik bilgisi türü değerleri IIS dizin güvenlik mekanizmalarına karşılık gelir. Aşağıdaki kod, ayarlanan modu ve kimlik bilgisi türü olarak Windows 'a ayarlı olduğunu gösterir. Hem istemci hem de sunucu aynı Windows etki alanında olduğunda bu yapılandırmayı kullanabilirsiniz.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)]
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Veya, yapılandırmada:  
  
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
  
 Aşağıdaki bölümlerde diğer istemci kimlik bilgileri türleri ele alınmaktadır.  
  
#### <a name="basic"></a>Temel  
 Bu, IIS 'deki temel kimlik doğrulama yöntemine karşılık gelir. Bu modu kullanırken, IIS sunucusunun Windows Kullanıcı hesaplarıyla ve uygun NTFS dosya sistemi izinleriyle yapılandırılması gerekir. IIS 6,0 hakkında daha fazla bilgi için bkz. [temel kimlik doğrulamasını etkinleştirme ve bölge adını yapılandırma](/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)). IIS 7,0 hakkında daha fazla bilgi için bkz. [temel kimlik doğrulamasını yapılandırma (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).  
  
#### <a name="certificate"></a>Sertifika  
 IIS 'de, istemcilerin bir sertifikayla oturum açmasını gerektirme seçeneği vardır. Özelliği, IIS 'nin bir istemci sertifikasını bir Windows hesabına eşlemesine de olanak sağlar. IIS 6,0 hakkında daha fazla bilgi için bkz. [ııs 6,0 ' de Istemci sertifikalarını etkinleştirme](/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)). IIS 7,0 hakkında daha fazla bilgi için bkz. [IIS 7 ' de sunucu sertifikalarını yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Bilgisi  
 Özet kimlik doğrulaması temel kimlik doğrulamasına benzerdir, ancak kimlik bilgilerini şifresiz metin yerine karma olarak göndermenin avantajlarından yararlanır. IIS 6,0 hakkında daha fazla bilgi için bkz. [ııs 6,0 ' de Özet kimlik doğrulaması](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)). IIS 7,0 hakkında daha fazla bilgi için bkz. [Özet kimlik doğrulamasını yapılandırma (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).  
  
#### <a name="windows"></a>Windows  
 Bu, IIS 'de tümleşik Windows kimlik doğrulamasına karşılık gelir. Bu değere ayarlandığında, sunucunun etki alanı denetleyicisi olarak Kerberos protokolünü kullanan bir Windows etki alanı üzerinde de bulunması beklenir. Sunucu Kerberos ile desteklenen bir etki alanında değilse veya Kerberos sistemi başarısız olursa, sonraki bölümde açıklanan NT LAN Manager (NTLM) değerini kullanabilirsiniz. IIS 6,0 hakkında daha fazla bilgi için bkz. [ııs 6,0 ' de tümleşik Windows kimlik doğrulaması](/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)). IIS 7,0 hakkında daha fazla bilgi için bkz. [IIS 7 ' de sunucu sertifikalarını yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 Bu, Kerberos Protokolü başarısız olursa sunucunun kimlik doğrulaması için NTLM kullanmasını sağlar. IIS 6,0 ' de IIS 'yi yapılandırma hakkında daha fazla bilgi için bkz. [NTLM kimlik doğrulamasını zorlama](/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)). IIS 7,0 için Windows kimlik doğrulaması, NTLM kimlik doğrulaması içerir. Daha fazla bilgi için bkz. [IIS 7 ' de sunucu sertifikalarını yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding>Sınıfı, WS-* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır. Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL). SSL kullanan bir WCF uygulaması oluşturmak için, uygulamayı barındırmak üzere IIS kullanın. Alternatif olarak, şirket içinde barındırılan bir uygulama oluşturuyorsanız, bir X. 509.440 sertifikasını bir bilgisayardaki belirli bir bağlantı noktasına bağlamak için HttpCfg.exe aracını kullanın. Bağlantı noktası numarası, WCF uygulamasının bir parçası olarak bir uç nokta adresi olarak belirtilir. Aktarım modunu kullanırken, uç nokta adresi HTTPS protokolünü içermeli veya çalışma zamanında bir özel durum oluşturulur. Daha fazla bilgi için bkz. [http aktarım güvenliği](http-transport-security.md).  
  
 İstemci kimlik doğrulaması için, <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> <xref:System.ServiceModel.HttpTransportSecurity> sınıfının özelliğini <xref:System.ServiceModel.HttpClientCredentialType> sabit listesi değerlerinden birine ayarlayın. Numaralandırma değerleri, için istemci kimlik bilgisi türleriyle aynıdır <xref:System.ServiceModel.BasicHttpBinding> ve IIS hizmetleriyle barındırılmak üzere tasarlanmıştır.  
  
 Aşağıdaki örnekte, Windows 'un istemci kimlik bilgisi türüyle kullanılan bağlama gösterilmektedir.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Bu bağlama, aktarım düzeyi güvenliği değil yalnızca ileti düzeyinde güvenlik sağlar.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding>Sınıfı ileti taşıması IÇIN TCP kullanır. Aktarım modunun güvenliği, TCP üzerinden Aktarım Katmanı Güvenliği (TLS) uygulayarak sağlanır. TLS uygulama, işletim sistemi tarafından sağlanır.  
  
 Ayrıca, <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> <xref:System.ServiceModel.TcpTransportSecurity> <xref:System.ServiceModel.TcpClientCredentialType> aşağıdaki kodda gösterildiği gibi, sınıfının özelliğini değerlerden birine ayarlayarak istemcinin kimlik bilgisi türünü belirtebilirsiniz.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>İstemci  
 İstemcisinde, sınıfının yöntemini kullanarak bir sertifika belirtmeniz gerekir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> .  
  
> [!NOTE]
> Windows güvenliği kullanıyorsanız, bir sertifika gerekli değildir.  
  
 Aşağıdaki kod, sertifikanın kendisini benzersiz bir şekilde tanımlayan parmak izini kullanır. Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternatif olarak, davranışlar bölümündeki bir öğeyi kullanarak istemcinin yapılandırmasındaki sertifikayı belirtin [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) .  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"
      storeLocation="LocalMachine" storeName="My"
      X509FindType="FindByThumbPrint">  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding>Sınıfı, etkin makine içi iletişim için tasarlanmıştır; diğer bir deyişle, aynı bilgisayarda çalışan süreçler için, adlandırılmış kanal kanalları aynı ağ üzerinde iki bilgisayar arasında oluşturulabilse de. Bu bağlama yalnızca aktarım düzeyi güvenlik sağlar. Bu bağlamayı kullanarak uygulamalar oluştururken, uç nokta adresleri, uç nokta adresinin protokolü olarak "net. pipe" içermelidir.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Aktarım güvenliği kullanılırken bu bağlama, HTTPS olarak bilinen ve verilen belirteç () ile HTTP üzerinden SSL kullanır <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential> . Federasyon uygulamaları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding>Sınıfı, eşler arası ağ özelliği kullanılarak verimli iletişim için tasarlanan güvenli bir aktarımdır. Sınıfın ve bağlamanın adı ile gösterildiği gibi, TCP de protokoldür. Güvenlik modu aktarım olarak ayarlandığında, bağlama TCP üzerinden TLS uygular. Eşler arası özelliği hakkında daha fazla bilgi için bkz. eşler [arası ağ oluşturma](peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding ve NetMsmqBinding  
 Message Queuing (daha önce MSMQ olarak adlandırılır) ile taşıma güvenliği hakkında ayrıntılı bir tartışma için bkz. [Transport Security kullanarak Iletileri güvenli hale getirme](securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Güvenliğini Programlama](programming-wcf-security.md)
