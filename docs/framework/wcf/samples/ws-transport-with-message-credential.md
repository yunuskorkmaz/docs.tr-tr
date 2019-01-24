---
title: İleti Kimlik Bilgileri ile WS Aktarma
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 9495dea69e489321360b1f4e24fea7d1e84fa038
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690221"
---
# <a name="ws-transport-with-message-credential"></a>İleti Kimlik Bilgileri ile WS Aktarma
Bu örnek, iletide taşınmasına istemci kimlik bilgileri ile birlikte SSL Aktarım güvenliği kullanımını gösterir. Bu örnekte `wsHttpBinding` bağlama.  
  
 Varsayılan olarak, `wsHttpBinding` bağlama, HTTP iletişimi sağlar. Aktarım güvenliği için yapılandırıldığında, bağlama HTTPS iletişimini destekler. HTTPS, gizliliği ve bütünlük koruması kablo üzerinden gönderilen iletiler için sağlar. Ancak bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik doğrulama mekanizmaları kümesini destekleyen HTTPS aktarımı için sınırlıdır. Windows Communication Foundation (WCF) sunan bir `TransportWithMessageCredential` bu sınırlamanın üstesinden gelmek için tasarlanmış güvenlik modu. Bu güvenlik modu yapılandırıldığında, aktarım güvenliği, gizliliği ve bütünlüğü gönderilen iletileri sağlamak ve hizmet kimlik doğrulaması gerçekleştirmek için kullanılır. Ancak, istemci kimlik doğrulaması, istemci kimlik bilgilerini doğrudan iletisinde koyarak gerçekleştirilir. Bu ileti güvenlik modunu transport güvenlik modunu performans avantajı tutarken istemci kimlik doğrulaması için tarafından desteklenen herhangi bir kimlik bilgisi türü kullanmanıza olanak sağlar.  
  
 Bu örnekte, bir `UserName` kimlik bilgisi türü, bir hizmete istemcinin kimliğini doğrulamak için kullanılır.  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan. `wsHttpBinding` Bağlama belirtildi ve uygulama yapılandırma dosyalarında istemci ve hizmet için yapılandırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Program kodu içinde örnek olarak neredeyse aynı [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmeti. -Hizmet sözleşmesi tarafından sağlanan tek bir ek işlem yoktur `GetCallerIdentity`. Bu işlem, çağırana çağıranının kimliğini adını döndürür.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Bir sertifika oluşturun ve bunu oluşturmak ve bu örneği çalıştırmadan önce Web sunucusu sertifikası Sihirbazı'nı kullanarak atamanız gerekir. Uç nokta tanımı ve bağlama tanımı yapılandırmadaki ayarları dosya `TransportWithMessageCredential` istemci için aşağıdaki örnek yapılandırma gösterildiği gibi güvenlik modu.  
  
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
  
 Belirtilen adresi https:// şeması kullanır. Bağlama yapılandırması güvenlik modunu ayarlar `TransportWithMessageCredential`. Aynı güvenlik modu, hizmetin Web.config dosyasında belirtilmesi gerekir.  
  
 Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir https erişmeye çalıştığınızda bir güvenlik uyarısı görünür: adres gibi `https://localhost/servicemodelsamples/service.svc `, tarayıcınız üzerinden. Yerinde bir test sertifikası ile çalışmak için WCF istemcisini izin vermek için güvenlik uyarıyı gizlemek için istemci için bazı ek kod eklendi. Bu kod, eşlik eden sınıfı değil ve gerekli üretim sertifikalar kullanıldığında.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Gerçekleştirdiğinizden emin olmak [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
