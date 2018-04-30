---
title: WCF Güvenliğini Programlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: 25
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 63f5c2c61a374b92b018419c83c9429e6ad796d8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="programming-wcf-security"></a>WCF Güvenliğini Programlama
Bu konu güvenli oluşturmak için kullanılan temel programlama görevleri açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama. Bu konu, yalnızca kimlik doğrulaması, gizliliği ve bütünlük, topluca olarak bilinen kapsar *Aktarım güvenlik*. Bu konuda yetkilendirme (kaynaklarına veya hizmetlerine erişim denetimi); kapsamaz Yetkilendirme hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Özellikle de hesaba için güvenlik kavramları değerli bir giriş için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], MSDN'de bulunan desenleri ve uygulamalar öğreticileri kümesini görmek [senaryoları, desenleri ve uygulama kılavuzunu Web Services Enhancements (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki üç adımı üzerinde tabanlı güvenlik: güvenlik modu, bir istemci kimlik bilgisi türü ve kimlik bilgisi değerleri. Kod veya yapılandırma yoluyla bu adımları gerçekleştirebilir.  
  
## <a name="setting-the-security-mode"></a>Güvenlik modunu ayarlama  
 Aşağıdaki güvenlik modunda'yla programlama için genel adımlar açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
1.  Uygulama gereksinimlerinize uygun önceden tanımlanmış bağlamaları birini seçin. Bağlama tercih listesi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md). Varsayılan olarak etkin güvenlik neredeyse her bağlama yok. Bir özel durum <xref:System.ServiceModel.BasicHttpBinding> sınıfı (yapılandırmayı kullanarak [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Seçtiğiniz bağlama taşıma belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> HTTP taşıma; kullanır <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.  
  
2.  Bağlama için güvenlik modlarından birini seçin. Seçtiğiniz bağlama kullanılabilir modu seçenekleri belirlediğini unutmayın. Örneğin, <xref:System.ServiceModel.WSDualHttpBinding> (Bu bir seçenek değil) taşıma güvenliği izin vermiyor. Benzer şekilde, ne <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> veya <xref:System.ServiceModel.NetNamedPipeBinding> ileti güvenliği sağlar.  
  
     Üç seçeneğiniz vardır:  
  
    1.  `Transport`  
  
         Taşıma güvenliği seçmiş olduğunuz bağlama kullanan mekanizmasını bağlıdır. Örneğin, kullanıyorsanız `WSHttpBinding` güvenlik mekanizması Güvenli Yuva Katmanı (SSL) (aynı zamanda HTTPS protokolü için mekanizması) olur. Genel olarak bakıldığında, taşıma güvenliği ana avantajı, hangi aktarım olsun, kullanmakta olduğunuz iyi verimlilik sağlar ' dir. Ancak, iki sınırlamaları vardır: aktarım mekanizması bir kullanıcının kimliğini doğrulamak için kullanılan kimlik bilgisi türünü belirleyen ilk sunucudur. Yalnızca hizmet kimlik bilgilerini farklı türde talep diğer hizmetlerle birlikte çalışmak gerekiyorsa bir dezavantajı budur. İkinci güvenlik ileti düzeyinde uygulanmadığından güvenlik bir atlama atlamalı şekilde uçtan uca yerine, uygulanmasıdır. Yalnızca istemci ile hizmet arasında ileti yolu aracılar içeriyorsa bu ikinci sınırlama bir sorundur. Hangi aktarım kullanılacak hakkında daha fazla bilgi için bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Taşıma güvenliği kullanma hakkında daha fazla bilgi için bkz: [taşıma güvenliği genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         İleti güvenliği her ileti gerekli üst bilgileri içerir ve ileti tutmak için veri güvenli anlamına gelir. Üstbilgileri oluşumunu değiştiğinden, herhangi bir sayıda kimlik bilgileri içerebilir. Bu, diğer hizmetlerle birlikte bir aktarım mekanizması sağlayamıyor bir belirli kimlik bilgisi türü bu talebi birlikte veya ileti burada her bir hizmet farklı bir kimlik bilgisi türü talep birden fazla hizmet ile birlikte kullanılmalıdır bir etmen haline gelir.  
  
         Daha fazla bilgi için bkz: [ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         İleti aktarma güvenliğini sağlamak için Aktarım katmanı bu seçenek kullanır, her ileti Zengin kimlik bilgilerini içerir ancak diğer hizmetlerin gerekir. Bu, ileti güvenliği zengin kimlik bilgilerini avantajı ile taşıma güvenliği performans avantajı birleştirir. Bu aşağıdaki bağlamalarla kullanılabilir: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, ve <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Taşıma güvenliği için HTTP (diğer bir deyişle, HTTPS) kullanmaya karar verirseniz, aynı zamanda bir SSL sertifikası ile ana bilgisayar yapılandırma ve SSL bağlantı noktası etkinleştirme gerekir. Daha fazla bilgi için bkz: [HTTP taşıma güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4.  Kullanıyorsanız <xref:System.ServiceModel.WSHttpBinding> ve gerekmez güvenli bir oturumu ayarlamak <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğine `false`.  
  
     Simetrik anahtar (istemci ve sunucu iletişim kapatılana kadar bir konuşma uzunluğu için aynı anahtarı kullanan) kullanarak bir kanal istemci ve hizmet oluşturduğunuzda, güvenli bir oturum gerçekleşir.  
  
## <a name="setting-the-client-credential-type"></a>İstemci kimlik bilgisi türü ayarlama  
 Bir istemci kimlik bilgisi türü uygun şekilde seçin. Daha fazla bilgi için bkz: [bir kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Aşağıdaki istemci kimlik bilgisi türleri kullanılabilir:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 Mod nasıl ayarladığınıza bağlı olarak, kimlik bilgisi türü ayarlamanız gerekir. Örneğin, seçtiğiniz `wsHttpBinding`ve ayrıca ayarlayın, sonra da "İletisi," moda ayarladıysanız `clientCredentialType` özniteliği aşağıdaki değerlerden birine ileti öğesinin: `None`, `Windows`, `UserName`, `Certificate` , ve `IssuedToken`aşağıdaki yapılandırma örnekte gösterildiği gibi.  
  
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
 Bir istemci kimlik bilgisi türü seçtikten sonra hizmet ve kullanmak için istemci gerçek ilişkin kimlik bilgilerini ayarlamanız gerekir. Hizmette kimlik bilgileri kullanılarak ayarlanan <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı ve tarafından döndürülen <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği <xref:System.ServiceModel.ServiceHostBase> sınıfı. Kullanımdaki bağlama hizmet kimlik bilgisi türü, seçilen güvenlik modu ve istemci kimlik bilgileri türünü gösterir. Aşağıdaki kod, bir hizmeti kimlik bilgileri için bir sertifika ayarlar.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>İstemci kimlik bilgileri değerlerini ayarlama  
 İstemcide, istemci kimlik bilgisi değerleri kullanarak ayarlayın <xref:System.ServiceModel.Description.ClientCredentials> sınıfı ve tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı. Aşağıdaki kod, TCP protokolü kullanılarak bir istemcide bir kimlik bilgisi olarak bir sertifika ayarlar.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
