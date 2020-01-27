---
title: WCF Güvenliğini Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: e19f858818866f16b8af44abe462ddb826d43b69
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741474"
---
# <a name="programming-wcf-security"></a>WCF Güvenliğini Programlama
Bu konuda, güvenli bir Windows Communication Foundation (WCF) uygulaması oluşturmak için kullanılan temel programlama görevleri açıklanmaktadır. Bu konu, toplu olarak *Aktarım güvenliği*olarak bilinen kimlik doğrulama, gizlilik ve bütünlüğü içerir. Bu konu, yetkilendirmeyi kapsamaz (kaynaklara veya hizmetlere erişimin denetimi); Yetkilendirme hakkında bilgi için bkz. [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
> Özellikle WCF ile ilgili olarak güvenlik kavramlarına değerli bir giriş için, [Web Hizmetleri geliştirmeleri (WVAS) 3,0 Için senaryolar, desenler ve uygulama KıLAVUZLARıNDAKI](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))MSDN 'de bulunan desenler ve uygulamalar öğreticilerine bakın.  
  
 WCF güvenliğini programlama, aşağıdaki üç adımı temel alır: güvenlik modu, istemci kimlik bilgileri türü ve kimlik bilgisi değerleri. Bu adımları kod veya yapılandırma aracılığıyla yapabilirsiniz.  
  
## <a name="setting-the-security-mode"></a>Güvenlik modunu ayarlama  
 Aşağıda, WCF 'de güvenlik moduyla programlama için genel adımlar açıklanmıştır:  
  
1. Uygulama gereksinimlerinize uygun olan önceden tanımlanmış bağlamalardan birini seçin. Bağlama seçeneklerinin bir listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md). Varsayılan olarak, neredeyse her bağlamada Güvenlik etkindir. Tek istisna, <xref:System.ServiceModel.BasicHttpBinding> sınıfıdır (yapılandırma, [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Seçtiğiniz bağlama, taşımayı belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> taşıma olarak HTTP kullanır; <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.  
  
2. Bağlama için güvenlik modlarından birini seçin. Seçtiğiniz bağlamanın kullanılabilir mod seçimlerini belirlediğini unutmayın. Örneğin, <xref:System.ServiceModel.WSDualHttpBinding> aktarım güvenliğine izin vermez (bir seçenek değildir). Benzer şekilde, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ne de <xref:System.ServiceModel.NetNamedPipeBinding> ileti güvenliğine izin vermez.  
  
     Üç seçeneğiniz vardır:  
  
    1. `Transport`  
  
         Taşıma güvenliği, seçtiğiniz bağlamanın kullandığı mekanizmaya bağlıdır. Örneğin, `WSHttpBinding` kullanıyorsanız güvenlik mekanizması Güvenli Yuva Katmanı (SSL) (aynı zamanda HTTPS protokolü mekanizması) olur. Genel olarak, aktarım güvenliğinin temel avantajı, hangi taşımanın kullanıldığı önemli değildir. Ancak, bu iki sınırlamalara sahiptir: ilki, taşıma mekanizmasının bir kullanıcının kimliğini doğrulamak için kullanılan kimlik bilgisi türünü belirlemesi. Bu, yalnızca bir hizmetin farklı kimlik bilgilerini talep eden diğer hizmetlerle birlikte çalışması gerektiğinde bir dezavantajdır. İkincisi ise, güvenlik ileti düzeyinde uygulanmadığından, güvenlik, uçtan uca değil, atlama bir şekilde uygulanır. Bu ikinci sınırlama yalnızca istemci ve hizmet arasındaki ileti yolu aracılar içeriyorsa bir sorundur. Hangi taşımanın kullanılacağı hakkında daha fazla bilgi için bkz. [bir taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Taşıma güvenliğini kullanma hakkında daha fazla bilgi için bkz. [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2. `Message`  
  
         İleti güvenliği her iletinin, iletiyi güvenli tutmak için gerekli üst bilgileri ve verileri içerdiği anlamına gelir. Üst bilgilerin bileşimi değiştiğinden, istediğiniz sayıda kimlik bilgilerini ekleyebilirsiniz. Bu, bir taşıma mekanizmasının sağlayamediği belirli bir kimlik bilgisi türünü talep eden diğer hizmetlerle birlikte çalışıyorsanız veya ileti, her hizmetin farklı bir kimlik bilgisi türü talep ettiği birden fazla hizmetle birlikte kullanılması gerekiyorsa bir faktör haline gelir.  
  
         Daha fazla bilgi için bkz. [Ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Bu seçim, ileti aktarımını güvenli hale getirmek için aktarım katmanını kullanır, her ileti diğer hizmetlere gereken zengin kimlik bilgilerini içerir. Bu, aktarım güvenliğinin performans avantajlarından yararlanarak ileti güvenliğinin zengin kimlik bilgileri avantajını birleştirir. Bu, şu bağlamalarla kullanılabilir: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>ve <xref:System.ServiceModel.WSHttpBinding>.  
  
3. HTTP için Transport Security 'yi (diğer bir deyişle, HTTPS) kullanmaya karar verirseniz, ana bilgisayarı bir SSL sertifikası ile yapılandırmanız ve bir bağlantı noktasında SSL 'yi etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [http aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. <xref:System.ServiceModel.WSHttpBinding> kullanıyorsanız ve güvenli bir oturum oluşturmanız gerekmiyorsa, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini `false`olarak ayarlayın.  
  
     İstemci ve hizmet simetrik anahtar kullanarak bir kanal oluştururken güvenli bir oturum oluşur (iletişim kutusu kapatılıncaya kadar hem istemci hem de sunucu bir konuşma uzunluğu için aynı anahtarı kullanır).  
  
## <a name="setting-the-client-credential-type"></a>Istemci kimlik bilgisi türünü ayarlama  
 Uygun şekilde bir istemci kimlik bilgisi türü seçin. Daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Aşağıdaki istemci kimlik bilgisi türleri kullanılabilir:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 Modu nasıl ayarlayadığınıza bağlı olarak, kimlik bilgisi türünü ayarlamanız gerekir. Örneğin, `wsHttpBinding`seçtiyseniz ve modu "Ileti" olarak ayarladıysanız, aşağıdaki yapılandırma örneğinde gösterildiği gibi, Ileti öğesinin `clientCredentialType` özniteliğini de aşağıdaki değerlerden birine ayarlayabilirsiniz: `None`, `Windows`, `UserName`, `Certificate`ve `IssuedToken`.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 Veya kodda:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Hizmet kimlik bilgisi değerlerini ayarlama  
 Bir istemci kimlik bilgisi türünü seçtikten sonra, hizmet ve İstemcinin kullanacağı gerçek kimlik bilgilerini ayarlamanız gerekir. Hizmette, kimlik bilgileri <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı kullanılarak ayarlanır ve <xref:System.ServiceModel.ServiceHostBase> sınıfının <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği tarafından döndürülür. Kullanımdaki bağlama hizmet kimlik bilgisi türünü, seçilen güvenlik modunu ve istemci kimlik bilgisinin türünü gösterir. Aşağıdaki kod, bir hizmet kimlik bilgileri için bir sertifika ayarlar.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Istemci kimlik bilgisi değerlerini ayarlama  
 İstemcisinde <xref:System.ServiceModel.Description.ClientCredentials> sınıfını kullanarak istemci kimlik bilgisi değerlerini ayarlayın ve <xref:System.ServiceModel.ClientBase%601> sınıfının <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği tarafından döndürülen. Aşağıdaki kod, bir sertifikayı TCP protokolünü kullanarak bir istemci üzerinde kimlik bilgileri olarak ayarlar.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
