---
title: WCF Güvenliğini Programlama
description: Kimlik doğrulama, gizlilik ve bütünlük gibi güvenli bir WCF uygulaması oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 8e77c667dd8904c10bbab88e1413690677cef53b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244991"
---
# <a name="programming-wcf-security"></a>WCF Güvenliğini Programlama
Bu konuda, güvenli bir Windows Communication Foundation (WCF) uygulaması oluşturmak için kullanılan temel programlama görevleri açıklanmaktadır. Bu konu, toplu olarak *Aktarım güvenliği*olarak bilinen kimlik doğrulama, gizlilik ve bütünlüğü içerir. Bu konu, yetkilendirmeyi kapsamaz (kaynaklara veya hizmetlere erişimin denetimi); Yetkilendirme hakkında bilgi için bkz. [Yetkilendirme](authorization-in-wcf.md).  
  
> [!NOTE]
> Özellikle WCF ile ilgili olarak güvenlik kavramlarına değerli bir giriş için, [Web Hizmetleri geliştirmeleri (WVAS) 3,0 Için senaryolar, desenler ve uygulama KıLAVUZLARıNDAKI](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))MSDN 'de bulunan desenler ve uygulamalar öğreticilerine bakın.  
  
 WCF güvenliğini programlama, aşağıdaki üç adımı temel alır: güvenlik modu, istemci kimlik bilgileri türü ve kimlik bilgisi değerleri. Bu adımları kod veya yapılandırma aracılığıyla yapabilirsiniz.  
  
## <a name="setting-the-security-mode"></a>Güvenlik modunu ayarlama  
 Aşağıda, WCF 'de güvenlik moduyla programlama için genel adımlar açıklanmıştır:  
  
1. Uygulama gereksinimlerinize uygun olan önceden tanımlanmış bağlamalardan birini seçin. Bağlama seçeneklerinin bir listesi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md). Varsayılan olarak, neredeyse her bağlamada Güvenlik etkindir. Tek istisna, <xref:System.ServiceModel.BasicHttpBinding> sınıftır (yapılandırma,, [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).  
  
     Seçtiğiniz bağlama, taşımayı belirler. Örneğin, <xref:System.ServiceModel.WSHttpBinding> taşıma olarak http 'yi kullanır; <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.  
  
2. Bağlama için güvenlik modlarından birini seçin. Seçtiğiniz bağlamanın kullanılabilir mod seçimlerini belirlediğini unutmayın. Örneğin, <xref:System.ServiceModel.WSDualHttpBinding> Aktarım güvenliğine izin vermez (bir seçenek değildir). Benzer şekilde, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ne ne de <xref:System.ServiceModel.NetNamedPipeBinding> ileti güvenliği izin vermez.  
  
     Üç seçeneğiniz vardır:  
  
    1. `Transport`  
  
         Taşıma güvenliği, seçtiğiniz bağlamanın kullandığı mekanizmaya bağlıdır. Örneğin, kullanıyorsanız, `WSHttpBinding` güvenlik mekanizması Güvenli Yuva Katmanı (SSL) (aynı zamanda https Protokolü mekanizması) olur. Genel olarak, aktarım güvenliğinin temel avantajı, hangi taşımanın kullanıldığı önemli değildir. Ancak, bu iki sınırlamalara sahiptir: ilki, taşıma mekanizmasının bir kullanıcının kimliğini doğrulamak için kullanılan kimlik bilgisi türünü belirlemesi. Bu, yalnızca bir hizmetin farklı kimlik bilgilerini talep eden diğer hizmetlerle birlikte çalışması gerektiğinde bir dezavantajdır. İkincisi ise, güvenlik ileti düzeyinde uygulanmadığından, güvenlik, uçtan uca değil, atlama bir şekilde uygulanır. Bu ikinci sınırlama yalnızca istemci ve hizmet arasındaki ileti yolu aracılar içeriyorsa bir sorundur. Hangi taşımanın kullanılacağı hakkında daha fazla bilgi için bkz. [bir taşıma seçme](choosing-a-transport.md). Taşıma güvenliğini kullanma hakkında daha fazla bilgi için bkz. [Transport Security Overview](transport-security-overview.md).  
  
    2. `Message`  
  
         İleti güvenliği her iletinin, iletiyi güvenli tutmak için gerekli üst bilgileri ve verileri içerdiği anlamına gelir. Üst bilgilerin bileşimi değiştiğinden, istediğiniz sayıda kimlik bilgilerini ekleyebilirsiniz. Bu, bir taşıma mekanizmasının sağlayamediği belirli bir kimlik bilgisi türünü talep eden diğer hizmetlerle birlikte çalışıyorsanız veya ileti, her hizmetin farklı bir kimlik bilgisi türü talep ettiği birden fazla hizmetle birlikte kullanılması gerekiyorsa bir faktör haline gelir.  
  
         Daha fazla bilgi için bkz. [Ileti güvenliği](message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Bu seçim, ileti aktarımını güvenli hale getirmek için aktarım katmanını kullanır, her ileti diğer hizmetlere gereken zengin kimlik bilgilerini içerir. Bu, aktarım güvenliğinin performans avantajlarından yararlanarak ileti güvenliğinin zengin kimlik bilgileri avantajını birleştirir. Bu, aşağıdaki bağlamalarla kullanılabilir: <xref:System.ServiceModel.BasicHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> , <xref:System.ServiceModel.NetPeerTcpBinding> ve <xref:System.ServiceModel.WSHttpBinding> .  
  
3. HTTP için Transport Security 'yi (diğer bir deyişle, HTTPS) kullanmaya karar verirseniz, ana bilgisayarı bir SSL sertifikası ile yapılandırmanız ve bir bağlantı noktasında SSL 'yi etkinleştirmeniz gerekir. Daha fazla bilgi için bkz. [http aktarım güvenliği](http-transport-security.md).  
  
4. Kullanıyorsanız <xref:System.ServiceModel.WSHttpBinding> ve güvenli bir oturum oluşturmanız gerekmiyorsa, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini olarak ayarlayın `false` .  
  
     İstemci ve hizmet simetrik anahtar kullanarak bir kanal oluştururken güvenli bir oturum oluşur (iletişim kutusu kapatılıncaya kadar hem istemci hem de sunucu bir konuşma uzunluğu için aynı anahtarı kullanır).  
  
## <a name="setting-the-client-credential-type"></a>Istemci kimlik bilgisi türünü ayarlama  
 Uygun şekilde bir istemci kimlik bilgisi türü seçin. Daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](selecting-a-credential-type.md). Aşağıdaki istemci kimlik bilgisi türleri kullanılabilir:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 Modu nasıl ayarlayadığınıza bağlı olarak, kimlik bilgisi türünü ayarlamanız gerekir. Örneğin, `wsHttpBinding` öğesini seçtiyseniz ve modunu "ileti" olarak ayarladıysanız, `clientCredentialType` `None` `Windows` `UserName` `Certificate` `IssuedToken` aşağıdaki yapılandırma örneğinde gösterildiği gibi ileti öğesinin özniteliğini aşağıdaki değerlerden birine de ayarlayabilirsiniz:,,,, ve.  
  
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
  
 Veya kodda:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Hizmet kimlik bilgisi değerlerini ayarlama  
 Bir istemci kimlik bilgisi türünü seçtikten sonra, hizmet ve İstemcinin kullanacağı gerçek kimlik bilgilerini ayarlamanız gerekir. Hizmette, kimlik bilgileri sınıfı kullanılarak ayarlanır <xref:System.ServiceModel.Description.ServiceCredentials> ve <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> sınıfının özelliği tarafından döndürülür <xref:System.ServiceModel.ServiceHostBase> . Kullanımdaki bağlama hizmet kimlik bilgisi türünü, seçilen güvenlik modunu ve istemci kimlik bilgisinin türünü gösterir. Aşağıdaki kod, bir hizmet kimlik bilgileri için bir sertifika ayarlar.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Istemci kimlik bilgisi değerlerini ayarlama  
 İstemcisinde, <xref:System.ServiceModel.Description.ClientCredentials> sınıfını kullanarak ve sınıfının özelliği tarafından döndürülen istemci kimlik bilgileri değerlerini ayarlayın <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> . Aşağıdaki kod, bir sertifikayı TCP protokolünü kullanarak bir istemci üzerinde kimlik bilgileri olarak ayarlar.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../basic-wcf-programming.md)
- [Ortak Güvenlik Senaryoları](common-security-scenarios.md)
