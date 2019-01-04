---
title: İleti Güvenliği Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: e5bb27980f38237f69f77721578f30df3830ade2
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029651"
---
# <a name="message-security-windows"></a><span data-ttu-id="452c6-102">İleti Güvenliği Windows</span><span class="sxs-lookup"><span data-stu-id="452c6-102">Message Security Windows</span></span>
<span data-ttu-id="452c6-103">Bu örnek nasıl yapılandırılacağını gösteren bir <xref:System.ServiceModel.WSHttpBinding> ileti düzeyi güvenliği Windows kimlik doğrulaması ile kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="452c6-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="452c6-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="452c6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="452c6-105">Bu örnekte, Internet Information Services (IIS) barındırılan hizmetin ve bir konsol uygulaması (.exe) istemcidir.</span><span class="sxs-lookup"><span data-stu-id="452c6-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="452c6-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="452c6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="452c6-107">Varsayılan güvenlik [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) olduğundan ileti güvenliği Windows kimlik doğrulaması kullanarak.</span><span class="sxs-lookup"><span data-stu-id="452c6-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="452c6-108">Bu örnek yapılandırma dosyalarında açıkça ayarlanmış `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) için `Message` ve `clientCredentialType` özniteliğini `Windows`.</span><span class="sxs-lookup"><span data-stu-id="452c6-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="452c6-109">Bu değerleri bu bağlama için varsayılan değerler, ancak bunlar açıkça, bunların kullanımını göstermek için aşağıdaki örnek yapılandırmada gösterildiği şekilde yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="452c6-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="452c6-110">İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin oluşur.</span><span class="sxs-lookup"><span data-stu-id="452c6-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="452c6-111">Bağlama istemcinin uygun olarak yapılandırıldığı `securityMode` ve `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="452c6-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
  
 <span data-ttu-id="452c6-112">Hizmet kaynak kodu göstermek için değiştirilmiş nasıl <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> arayan kimliğini erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="452c6-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="452c6-113">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="452c6-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="452c6-114">İlk yöntem çağrıldı - `GetCallerIdentity` -istemciye arayan kimliğini adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="452c6-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="452c6-115">Konsol penceresinde istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="452c6-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="452c6-116">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="452c6-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="452c6-117">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="452c6-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="452c6-118">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="452c6-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="452c6-119">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="452c6-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452c6-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="452c6-120">See Also</span></span>
