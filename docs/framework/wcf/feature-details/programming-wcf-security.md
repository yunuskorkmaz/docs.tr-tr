---
title: WCF Güvenliğini Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 1e82fbb266d3789a8d34109c66d9ee1d8a93c70c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463816"
---
# <a name="programming-wcf-security"></a>WCF Güvenliğini Programlama
Bu konu, güvenli bir Windows Communication Foundation (WCF) uygulaması oluşturmak için kullanılan temel programlama görevlerini açıklar. Bu konu yalnızca kimlik doğrulama, gizlilik ve bütünlüğü kapsar, topluca *aktarım güvenliği*olarak bilinir. Bu konu yetkilendirmeyi (kaynaklara veya hizmetlere erişim denetimi) kapsamaz; yetkilendirme hakkında bilgi [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)için Yetkilendirme'ye bakın.  
  
> [!NOTE]
> Güvenlik kavramlarına değerli bir giriş için, özellikle WCF ile ilgili olarak, [Senaryolar, Desenler ve Web Hizmetleri Geliştirmeleri (WSE) 3.0 için Uygulama Kılavuzu'nda](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))MSDN'deki desen ve uygulama öğreticileri kümesine bakın.  
  
 WCF güvenliğini programlamak, aşağıdakileri ayarlayan üç adımı temel aşar: güvenlik modu, istemci kimlik bilgisi türü ve kimlik bilgileri değerleri. Bu adımları kod veya yapılandırma yoluyla gerçekleştirebilirsiniz.  
  
## <a name="setting-the-security-mode"></a>Güvenlik Modunu Ayarlama  
 WCF'de güvenlik moduile programlama için genel adımları aşağıda açıklar:  
  
1. Uygulama gereksinimlerinize uygun önceden tanımlanmış bağlamalardan birini seçin. Bağlama seçeneklerinin listesi [için, Sistem Tarafından Sağlanan Bağlamalar'a](../../../../docs/framework/wcf/system-provided-bindings.md)bakın. Varsayılan olarak, hemen hemen her bağlama güvenlik etkin. Bir özel durum <xref:System.ServiceModel.BasicHttpBinding> sınıf (yapılandırma kullanarak, [ \<temelHttpBinding>). ](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
  
     Seçtiğiniz bağlama aktarımını belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> aktarım olarak HTTP kullanır; <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.  
  
2. Bağlama için güvenlik modlarından birini seçin. Seçtiğiniz bağlamanın kullanılabilir mod seçeneklerini belirlediğini unutmayın. Örneğin, aktarım güvenliğine izin <xref:System.ServiceModel.WSDualHttpBinding> vermez (bu bir seçenek değildir). Benzer şekilde, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ne <xref:System.ServiceModel.NetNamedPipeBinding> mesaj güvenliğine izin verir.  
  
     Üç seçeneğiniz vardır:  
  
    1. `Transport`  
  
         Aktarım güvenliği, seçtiğiniz bağlamanın kullandığı mekanizmaya bağlıdır. Örneğin, kullanıyorsanız `WSHttpBinding` güvenlik mekanizması Güvenli Soketler Katmanı (SSL) (ayrıca HTTPS protokolü mekanizması). Genel olarak konuşursak, taşıma güvenliğinin en büyük avantajı, hangi taşımayı kullanıyor olursanız olun iyi bir iş elde etmektir. Ancak, iki sınırlaması vardır: Birincisi, aktarım mekanizmasının bir kullanıcıyı doğrulamak için kullanılan kimlik bilgisi türünü dikte etmesidir. Bu, yalnızca bir hizmetin farklı kimlik bilgileri gerektiren diğer hizmetlerle birlikte çalışması gerekiyorsa bir dezavantajdır. İkincisi, güvenlik ileti düzeyinde uygulanmadığından, güvenlik uçtan uca değil, hop-by-hop şekilde uygulanır. Bu ikinci sınırlama yalnızca istemci ve hizmet arasındaki ileti yolu aracılar içeriyorsa bir sorundur. Hangi taşımanın kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) Aktarım güvenliğini kullanma hakkında daha fazla bilgi için [Taşıma Güvenliğine Genel Bakış'a](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)bakın.  
  
    2. `Message`  
  
         İleti güvenliği, her iletinin iletiyi güvende tutmak için gerekli üstbilgileri ve verileri içerdiği anlamına gelir. Üstbilgilerin bileşimi değiştiğinden, istediğiniz sayıda kimlik bilgileri ekleyebilirsiniz. Bir aktarım mekanizmasının sağlayamadığı belirli bir kimlik bilgisi türünü talep eden diğer hizmetlerle birlikte çalışıyorsanız veya iletinin her hizmetin farklı bir kimlik bilgisi türü gerektirdiği birden fazla hizmetle kullanılması gerekiyorsa, bu bir faktör haline gelir.  
  
         Daha fazla bilgi için [İleti Güvenliği'ne](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)bakın.  
  
    3. `TransportWithMessageCredential`  
  
         Bu seçenek ileti aktarımını güvence altına almak için aktarım katmanını kullanırken, her ileti diğer hizmetlerin gereksinim duyduğu zengin kimlik bilgilerini içerir. Bu, aktarım güvenliğinin performans avantajını ileti güvenliğinin zengin kimlik bilgileri avantajıyla birleştirir. Bu aşağıdaki bağlamaları ile <xref:System.ServiceModel.BasicHttpBinding>kullanılabilir: <xref:System.ServiceModel.NetPeerTcpBinding>, <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, ve .  
  
3. HTTP için aktarım güvenliğini kullanmaya karar verirseniz (başka bir deyişle, HTTPS), ana bilgisayarı bir SSL sertifikasıyla yapılandırmanız ve bir bağlantı noktasında SSL'yi etkinleştirmeniz gerekir. Daha fazla bilgi için [HTTP Transport Security'ye](../../../../docs/framework/wcf/feature-details/http-transport-security.md)bakın.  
  
4. Kullanıyorsanız <xref:System.ServiceModel.WSHttpBinding> ve güvenli bir oturum oluşturmanız gerekmiyorsa, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> `false`özelliği .  
  
     Güvenli oturum, bir istemci ve hizmet simetrik anahtar kullanarak bir kanal oluşturduğunda oluşur (hem istemci hem de sunucu iletişim kapatılana kadar konuşma uzunluğu için aynı anahtarı kullanır).  
  
## <a name="setting-the-client-credential-type"></a>İstemci Kimlik Türünü Ayarlama  
 Uygun olarak bir istemci kimlik bilgisi türü seçin. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md) Aşağıdaki istemci kimlik bilgileri türleri kullanılabilir:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 Modu nasıl ayarladığınıza bağlı olarak, kimlik bilgisi türünü ayarlamanız gerekir. Örneğin, `wsHttpBinding`,, "İleti" modunu seçtiyseniz ve modu "İleti" `clientCredentialType` olarak ayarladıysanız, İleti öğesinin özniteliğini aşağıdaki değerlerden birine de ayarlayabilirsiniz: `None`, , `Windows` `UserName` `Certificate`ve `IssuedToken`, aşağıdaki yapılandırma örneğinde gösterildiği gibi.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 Veya kod olarak:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Hizmet Kimlik Bilgileri Değerlerini Ayarlama  
 İstemci kimlik bilgisi türünü seçtikten sonra, hizmetin ve istemcinin kullanacağı gerçek kimlik bilgilerini ayarlamanız gerekir. Hizmette kimlik bilgileri <xref:System.ServiceModel.Description.ServiceCredentials> sınıf kullanılarak ayarlanır ve <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> <xref:System.ServiceModel.ServiceHostBase> sınıfın özelliği tarafından döndürülür. Kullanılan bağlama, hizmet kimlik bilgisi türünü, seçilen güvenlik modunu ve istemci kimlik bilgisinin türünü ifade eder. Aşağıdaki kod, bir hizmet kimlik bilgisi için bir sertifika ayarlar.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>İstemci Kimlik Bilgileri Değerlerini Ayarlama  
 İstemci üzerinde, <xref:System.ServiceModel.Description.ClientCredentials> sınıfı kullanarak istemci kimlik bilgileri değerlerini <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> ayarlayın <xref:System.ServiceModel.ClientBase%601> ve sınıfın özelliği tarafından döndürülür. Aşağıdaki kod, TCP protokolünü kullanan bir istemcide bir kimlik bilgisi olarak sertifika ayarlar.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
