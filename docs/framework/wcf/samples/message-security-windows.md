---
description: 'Daha fazla bilgi edinin: Ileti güvenliği pencereleri'
title: İleti Güvenliği Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 6b181e1bb835ea3129e99eb45baa6669bf8c09a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752281"
---
# <a name="message-security-windows"></a>İleti Güvenliği Windows

Bu örnek <xref:System.ServiceModel.WSHttpBinding> , Windows kimlik doğrulamasıyla ileti düzeyi güvenliği kullanmak için bir bağlamanın nasıl yapılandırılacağını gösterir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır. Bu örnekte, hizmet Internet Information Services (IIS) içinde barındırılır ve istemci bir konsol uygulaması (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 İçin varsayılan güvenlik, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) Windows kimlik doğrulaması kullanan ileti güvenliğine yöneliktir. Bu örnekteki yapılandırma dosyaları, `mode` [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Message` ve özniteliğinin özniteliğini açıkça olarak ayarlar `clientCredentialType` `Windows` . Bu değerler, bu bağlamanın varsayılan değerleridir, ancak kullanımları göstermek için aşağıdaki örnek yapılandırmada gösterildiği gibi açıkça yapılandırılmıştır.  
  
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
  
 İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. İstemci bağlama, uygun ve ile yapılandırılır `securityMode` `authenticationMode` .  
  
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
  
 Hizmet kaynak kodu, <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> çağıranın kimliğine erişmek için nasıl kullanılabileceğini göstermek üzere değiştirilmiştir.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İlk yöntem- `GetCallerIdentity` ---, çağıran kimliğin adını istemciye geri döndürür. İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
