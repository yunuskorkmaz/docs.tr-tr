---
title: "İleti Kimlik Bilgileri ile WS Aktarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f782ac12c92755eb26eddd30c5d8c15168c35858
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transport-with-message-credential"></a>İleti Kimlik Bilgileri ile WS Aktarma
Bu örnek, iletide taşınmasına istemci kimlik bilgileri ile birlikte SSL taşıma güvenliği kullanımını göstermektedir. Bu örnekte `wsHttpBinding` bağlama.  
  
 Varsayılan olarak, `wsHttpBinding` bağlama HTTP iletişim sağlar. Taşıma güvenliği için yapılandırıldığında, bağlama HTTPS iletişimi destekler. HTTPS gizliliği ve bütünlük koruması kablo üzerinden gönderilen iletiler için sağlar. Ancak istemci hizmeti için kimlik doğrulaması için kullanılan kimlik doğrulama mekanizmaları HTTPS taşıma desteklediği için sınırlı kümesidir. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]sunan bir `TransportWithMessageCredential` bu sınırlamanın üstesinden gelmek için tasarlanmış güvenlik modu. Bu güvenlik modu yapılandırıldığında, taşıma güvenliği için iletilen iletileri gizliliği ve bütünlük sağlamak ve hizmet kimlik doğrulaması yapmak için kullanılır. Ancak, istemci kimlik doğrulama ileti doğrudan istemci kimlik bilgileri koyarak gerçekleştirilir. Bu ileti güvenlik modu aktarım güvenlik modu performans avantajı korurken istemci kimlik doğrulaması için tarafından desteklenen herhangi bir kimlik bilgisi türü kullanmanıza olanak sağlar.  
  
 Bu örnekte, bir `UserName` kimlik bilgisi türü hizmeti için istemci kimlik doğrulaması için kullanılır.  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular. `wsHttpBinding` Bağlama belirtilen ve uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnek program kodunda olarak neredeyse aynıdır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmet. Bir başka işlem tarafından hizmet sözleşmesini - sağlanan `GetCallerIdentity`. Bu işlem çağırana çağıranının kimliğini adını döndürür.  
  
```  
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```  
  
 Bir sertifika oluşturun ve oluşturmaya ve örnek çalıştırmaya önce Web Sunucusu Sertifika Sihirbazı'nı kullanarak atamanız gerekir. Uç nokta tanımı ve bağlama tanımı dosyası ayarlarını etkinleştir `TransportWithMessageCredential` istemci için aşağıdaki örnek yapılandırma gösterildiği gibi güvenlik modu.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Belirtilen adres https:// düzenini kullanır. Güvenlik modu bağlama yapılandırması ayarlar `TransportWithMessageCredential`. Aynı güvenlik modu hizmetin Web.config dosyasında belirtilmesi gerekir.  
  
 Bu örnekte kullanılan sertifikanın Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir https erişmeye çalıştığınızda bir güvenlik uyarısı görünür: tarayıcınızdan https://localhost/servicemodelsamples/service.svc gibi adresi. İzin vermek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, yerinde bir test sertifikası ile çalışmak için bazı ek kod güvenlik uyarıyı gizlemek için istemciye eklendi. Bu kod, eşlik eden sınıfı değil ve gerekli üretim sertifikalar kullanıldığında.  
  
```  
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Gerçekleştirmiş emin olun [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.
