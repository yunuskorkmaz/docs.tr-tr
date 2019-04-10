---
title: İleti Güvenliği Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: eed16f6231717119b30003451cef5eb54016678c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318318"
---
# <a name="message-security-windows"></a>İleti Güvenliği Windows
Bu örnek nasıl yapılandırılacağını gösteren bir <xref:System.ServiceModel.WSHttpBinding> ileti düzeyi güvenliği Windows kimlik doğrulaması ile kullanılacak bağlama. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Bu örnekte, Internet Information Services (IIS) barındırılan hizmetin ve bir konsol uygulaması (.exe) istemcidir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Varsayılan güvenlik [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) olduğundan ileti güvenliği Windows kimlik doğrulaması kullanarak. Bu örnek yapılandırma dosyalarında açıkça ayarlanmış `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) için `Message` ve `clientCredentialType` özniteliğini `Windows`. Bu değerleri bu bağlama için varsayılan değerler, ancak bunlar açıkça, bunların kullanımını göstermek için aşağıdaki örnek yapılandırmada gösterildiği şekilde yapılandırıldı.  
  
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
  
 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin oluşur. Bağlama istemcinin uygun olarak yapılandırıldığı `securityMode` ve `authenticationMode`.  
  
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
  
 Hizmet kaynak kodu göstermek için değiştirilmiş nasıl <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> arayan kimliğini erişmek için kullanılabilir.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İlk yöntem çağrıldı - `GetCallerIdentity` -istemciye arayan kimliğini adını döndürür. Konsol penceresinde istemci kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
