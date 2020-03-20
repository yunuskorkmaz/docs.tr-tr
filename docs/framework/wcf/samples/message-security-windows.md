---
title: İleti Güvenliği Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 8706eee341dd1a5852efae0aad5195e09f62fec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183490"
---
# <a name="message-security-windows"></a>İleti Güvenliği Windows
Bu örnek, Windows kimlik <xref:System.ServiceModel.WSHttpBinding> doğrulaması ile ileti düzeyinde güvenlik kullanmak için bir bağlama yapılandırmak için nasıl gösterir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Bu örnekte, hizmet Internet Information Services (IIS) barındırılır ve istemci bir konsol uygulamasıdır (.exe).  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 wsHttpBinding>için varsayılan güvenlik, Windows kimlik doğrulamasını kullanarak ileti güvenliğidir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) Bu örnekteki yapılandırma dosyaları, `mode` [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) özniteliğini `Message` ve `clientCredentialType` ''ye' `Windows`özniteliğini açıkça ayarlar. Bu değerler bu bağlama için varsayılan değerlerdir, ancak bunların kullanımını göstermek için aşağıdaki örnek yapılandırmada gösterildiği gibi açıkça yapılandırılmıştır.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 İstemci bitiş noktası yapılandırması, hizmet bitiş noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. İstemci bağlama uygun `securityMode` ve `authenticationMode`.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"
            binding="wsHttpBinding"
            bindingConfiguration="Binding1"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Hizmet kaynak kodu, arayanın kimliğine erişmek için nasıl <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> kullanılabileceğini göstermek için değiştirildi.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Çağrılan ilk yöntem `GetCallerIdentity` - - arayan kimliğinin adını istemciye geri döndürür. İstemciyi kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
