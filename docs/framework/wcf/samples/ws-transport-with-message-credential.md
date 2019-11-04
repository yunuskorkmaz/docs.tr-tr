---
title: İleti Kimlik Bilgileri ile WS Aktarma
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: cc452ade4ef7d0d2d197f058d74ca0c3d0e0230d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423070"
---
# <a name="ws-transport-with-message-credential"></a>İleti Kimlik Bilgileri ile WS Aktarma
Bu örnek, iletide yürütülen istemci kimlik bilgileri ile birlikte SSL Aktarım güvenliği kullanımını gösterir. Bu örnek `wsHttpBinding` bağlamasını kullanır.  
  
 `wsHttpBinding` bağlama, varsayılan olarak HTTP iletişimi sağlar. Aktarım güvenliği için yapılandırıldığında bağlama, HTTPS iletişimini destekler. HTTPS, tel üzerinden iletilen iletiler için Gizlilik ve bütünlük koruması sağlar. Ancak, hizmette istemcinin kimliğini doğrulamak için kullanılabilen kimlik doğrulama mekanizmaları kümesi, HTTPS aktarımının desteklediği ile sınırlıdır. Windows Communication Foundation (WCF), bu sınırlamanın üstesinden gelmek için tasarlanan bir `TransportWithMessageCredential` güvenlik modu sağlar. Bu güvenlik modu yapılandırıldığında, aktarım güvenliği, iletilen iletiler için Gizlilik ve bütünlük sağlamak ve hizmet kimlik doğrulamasını gerçekleştirmek için kullanılır. Ancak istemci kimlik doğrulaması, istemci kimlik bilgisi doğrudan iletiye yerleştirilerek gerçekleştirilir. Bu, aktarım güvenliği modunun performans avantajını korurken istemci kimlik doğrulaması için ileti güvenliği modu tarafından desteklenen herhangi bir kimlik bilgisi türünü kullanmanıza olanak sağlar.  
  
 Bu örnekte, istemcinin kimliğini doğrulamak için `UserName` bir kimlik bilgisi türü kullanılır.  
  
 Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır. `wsHttpBinding` bağlama belirtilir ve istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnekteki program kodu, [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) başlama hizmetindekilerle neredeyse aynıdır. Hizmet sözleşmesi tarafından sağlanmış bir ek işlem vardır `GetCallerIdentity`. Bu işlem, arayanın kimliğinin adını çağırana döndürür.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Örneği oluşturmadan önce bir sertifika oluşturmalı ve Web sunucusu Sertifika sihirbazını kullanarak atamanız gerekir. Yapılandırma dosyası ayarlarındaki uç nokta tanımı ve bağlama tanımı, istemcinin aşağıdaki örnek yapılandırmasında gösterildiği gibi `TransportWithMessageCredential` güvenlik modunu etkinleştirir.  
  
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
  
 Belirtilen adres https://düzenini kullanır. Bağlama yapılandırması güvenlik modunu `TransportWithMessageCredential`olarak ayarlar. Hizmetin Web. config dosyasında aynı güvenlik modu belirtilmelidir.  
  
 Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikası olduğundan, `https://localhost/servicemodelsamples/service.svc`gibi bir https: adresine erişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir. WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir. Üretim sertifikaları kullanılırken bu kod ve eşlik eden sınıf gerekli değildir.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. [Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
