---
title: WCF Güvenliğini Programlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: d327605c084cd5fb1c65fbb786e871b421730b83
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313326"
---
# <a name="programming-wcf-security"></a>WCF Güvenliğini Programlama
Bu konu, güvenli bir Windows Communication Foundation (WCF) uygulaması oluşturmak için kullanılan temel programlama görevlerini açıklar. Bu konu, yalnızca kimlik doğrulaması, gizliliği ve bütünlük, toplu olarak bilinen içermektedir *aktarım güvenliği*. Bu konuda, yetkilendirme (kaynaklarına veya hizmetlerine erişim denetimi); içermez Yetkilendirme hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Değerli bir WCF, özellikle in regard to güvenlik kavramlarına giriş için MSDN'de desenler ve uygulamalar öğreticiler kümesini görmek [senaryoları, desenleri ve Uygulama Kılavuzu Web Services Enhancements (WSE) 3.0](https://go.microsoft.com/fwlink/?LinkID=88250).  
  
 WCF güvenliğini programlama aşağıdaki üç adımı üzerinde temel: güvenlik modu, bir istemci kimlik bilgileri türünü ve kimlik bilgisi değerleri. Kod veya yapılandırma adımları gerçekleştirebilirsiniz.  
  
## <a name="setting-the-security-mode"></a>Güvenlik modunu ayarlama  
 Wcf'de güvenlik modu'yla programlama için uygulamanız gereken genel adımlar açıklanmaktadır:  
  
1. Uygulama gereksinimlerinize uygun önceden tanımlanmış bağlamaları birini seçin. Bağlama seçeneklerin bir listesi için bkz. [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md). Varsayılan olarak, güvenliği etkinleştirilmiş neredeyse her bağlama yok. Bir özel durum <xref:System.ServiceModel.BasicHttpBinding> sınıfı (yapılandırmayı kullanarak [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Seçtiğiniz bağlama taşıma belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> aktarım olarak; HTTP kullanır <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.  
  
2. Bağlama için olan güvenlik modlarından birini seçin. Seçtiğiniz bağlama kullanılabilir modu seçenekleri belirler unutmayın. Örneğin, <xref:System.ServiceModel.WSDualHttpBinding> (Bu bir seçenek değil) aktarım güvenliği izin vermiyor. Benzer şekilde, hiçbiri <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ya da <xref:System.ServiceModel.NetNamedPipeBinding> ileti güvenliği sağlar.  
  
     Üç seçeneğiniz vardır:  
  
    1.  `Transport`  
  
         Aktarım güvenliği seçtiğiniz bağlama kullanan mekanizmasını bağlıdır. Örneğin, kullanıyorsanız `WSHttpBinding` güvenlik mekanizması Güvenli Yuva Katmanı (SSL) (aynı zamanda HTTPS protokolü için mekanizma) kaldırılır. Genel olarak bakıldığında, aktarım güvenliği ana avantajı, hangi aktarım ne olursa olsun, kullandığınız iyi aktarım hızı sunan olmanızdır. Ancak, iki sınırlamalara sahiptir: İlk aktarım mekanizması bir kullanıcının kimliğini doğrulamak için kullanılan kimlik bilgisi türünü belirleyen ' dir. Yalnızca hizmet kimlik bilgilerini farklı türde talep diğer hizmetleriyle gerekiyorsa bir dezavantajı budur. İkinci güvenlik ileti düzeyinde uygulanmadığından güvenlik bir atlama atlamalı şekilde uçtan uca yerine, uygulanmasıdır. Yalnızca istemci ile hizmet arasında ileti yolu aracılar içeriyorsa bu ikinci sınırlama bir sorundur. Hangi aktarım kullanılacak hakkında daha fazla bilgi için bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aktarım güvenliği kullanma hakkında daha fazla bilgi için bkz. [aktarım güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         İleti güvenliği her ileti gerekli üst bilgileri içerir ve ileti tutmak için verileri güvenli anlamına gelir. Üstbilgileri olarak değiştiğinden, herhangi bir sayıda kimlik bilgileri içerebilir. Bu, diğer hizmetlerle aktarım mekanizması sağlayamazsınız bir belirli kimlik bilgisi türü bu talebi birlikte veya iletinin her bir hizmet farklı bir kimlik bilgisi türü burada talepleri birden fazla hizmeti ile kullanılmalıdır bir etmen haline gelir.  
  
         Daha fazla bilgi için [ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Bu seçenek, güvenli ileti aktarım için Aktarım katmanı kullanır, her ileti Zengin kimlik bilgilerini içerirken diğer hizmetleri gerekir. Bu performans avantajı aktarım güvenliği ile ileti güvenliği zengin kimlik bilgilerinin avantajlarından birleştirir. Bu aşağıdaki bağlamalarla kullanılabilir: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, ve <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Aktarım güvenliği için HTTP (diğer bir deyişle, HTTPS) kullanmaya karar verirseniz, ayrıca bir SSL sertifikası ile ana bilgisayar yapılandırma ve SSL bağlantı noktası etkinleştirme gerekir. Daha fazla bilgi için [HTTP aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. Kullanıyorsanız <xref:System.ServiceModel.WSHttpBinding> gerekmez güvenli bir oturumu ayarlamak <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini `false`.  
  
     Hizmet ve istemci bir simetrik anahtar (istemci ve sunucu iletişim kapatılana kadar bir konuşma uzunluğu için aynı anahtar kullanılır) kullanarak bir kanal oluşturduğunuzda, güvenli bir oturum gerçekleşir.  
  
## <a name="setting-the-client-credential-type"></a>İstemci kimlik bilgileri türünü ayarlama  
 Bir istemci kimlik bilgileri türünü gerektiği gibi seçin. Daha fazla bilgi için [kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Aşağıdaki istemci kimlik bilgisi türleri kullanılabilir:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 Modu nasıl ayarladığına bağlı olarak, kimlik bilgisi türü ayarlamanız gerekir. Örneğin, seçtiğiniz `wsHttpBinding`ve ayrıca daha sonra "İleti" moduna `clientCredentialType` aşağıdaki değerlerden biri olarak ileti öğenin özniteliği: `None`, `Windows`, `UserName`, `Certificate` , ve `IssuedToken`yapılandırmasını aşağıda gösterildiği gibi.  
  
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
  
 Kod:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Hizmet kimlik bilgisi değerleri ayarlama  
 Bir istemci kimlik bilgileri türünü seçtikten sonra gerçek kimlik bilgilerini kullanmak için istemci ve hizmet için ayarlamanız gerekir. Hizmette kimlik bilgileri kullanılarak ayarlanan <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı ve tarafından döndürülen <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği <xref:System.ServiceModel.ServiceHostBase> sınıfı. Kullanımdaki bağlama hizmeti kimlik bilgisi türü, seçilen güvenlik modu ve istemci kimlik bilgisi türünü gösterir. Aşağıdaki kod, bir hizmeti kimlik bilgileri için bir sertifika ayarlar.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>İstemci kimlik bilgileri değerlerini ayarlama  
 İstemci kimlik bilgileri değerlerini kullanarak istemci üzerinde ayarlanmış <xref:System.ServiceModel.Description.ClientCredentials> sınıfı ve tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı. Aşağıdaki kod, TCP protokolünü kullanarak bir istemcide bir kimlik bilgisi olarak bir sertifika ayarlar.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
