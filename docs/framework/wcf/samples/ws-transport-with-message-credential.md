---
title: İleti Kimlik Bilgileri ile WS Aktarma
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183138"
---
# <a name="ws-transport-with-message-credential"></a>İleti Kimlik Bilgileri ile WS Aktarma
Bu örnek, Iletide taşınan istemci kimlik bilgileriyle birlikte SSL aktarım güvenliğinin kullanımını göstermektedir. Bu örnek `wsHttpBinding` bağlama kullanır.  
  
 Varsayılan olarak, `wsHttpBinding` bağlama HTTP iletişim sağlar. Aktarım güvenliği için yapılandırıldığında, bağlama HTTPS iletişimini destekler. HTTPS, tel üzerinden iletilen iletiler için gizlilik ve bütünlük koruması sağlar. Ancak istemcinin hizmete kimliğini doğrulamak için kullanılabilecek kimlik doğrulama mekanizmaları kümesi, HTTPS aktarımının desteklediği yle sınırlıdır. Windows Communication Foundation (WCF), bu sınırlamayı aşmak için tasarlanmış bir `TransportWithMessageCredential` güvenlik modu sunar. Bu güvenlik modu yapılandırıldığında, aktarım güvenliği iletilen iletiler için gizlilik ve bütünlük sağlamak ve hizmet kimlik doğrulamasını gerçekleştirmek için kullanılır. Ancak, istemci kimlik doğrulaması doğrudan iletiye istemci kimlik bilgisi koyarak gerçekleştirilir. Bu, aktarım güvenlik modunun performans avantajını tutarken istemci kimlik doğrulaması için ileti güvenliği modu tarafından desteklenen herhangi bir kimlik bilgisi türünü kullanmanıza olanak tanır.  
  
 Bu örnekte, `UserName` istemcinin hizmete kimliğini doğrulamak için bir kimlik bilgisi türü kullanılır.  
  
 Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. Bağlama, `wsHttpBinding` istemci ve hizmet için uygulama yapılandırma dosyalarında belirtilir ve yapılandırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnekteki program kodu, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hizmetiyle hemen hemen aynıdır. Hizmet sözleşmesi tarafından sağlanan bir ek `GetCallerIdentity`işlem vardır - . Bu işlem, arayanın kimliğini arayana döndürür.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Örneği oluşturmadan ve çalıştırmadan önce Web Sunucusu Sertifika Sihirbazı'nı kullanarak bir sertifika oluşturmanız ve atamanız gerekir. Yapılandırma dosyası ayarlarındaki uç nokta tanımı `TransportWithMessageCredential` ve bağlama tanımı, istemci için aşağıdaki örnek yapılandırmada gösterildiği gibi güvenlik modunu etkinleştirin.  
  
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
  
 Belirtilen adres https:// düzenini kullanır. Bağlama yapılandırması güvenlik modunu `TransportWithMessageCredential`. Aynı güvenlik modu hizmetin Web.config dosyasında belirtilmelidir.  
  
 Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızdan bir https adresine `https://localhost/servicemodelsamples/service.svc`erişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir. WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, istemciye güvenlik uyarısını bastırmak için bazı ek kodlar eklendi. Üretim sertifikaları kullanırken bu kod ve beraberindeki sınıf gerekli değildir.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Internet Information Services [(IIS) Server Certificate Kurulum Yönergesi'ni](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizi belirtin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
