---
title: İleti Güvenliği Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: f46eb12078082614cd6cdc75b7bc7eedb7c94de9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930441"
---
# <a name="message-security-windows"></a><span data-ttu-id="50a1b-102">İleti Güvenliği Windows</span><span class="sxs-lookup"><span data-stu-id="50a1b-102">Message Security Windows</span></span>
<span data-ttu-id="50a1b-103">Bu örnek, Windows kimlik doğrulamasıyla ileti <xref:System.ServiceModel.WSHttpBinding> düzeyi güvenliği kullanmak için bir bağlamanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50a1b-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="50a1b-104">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="50a1b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="50a1b-105">Bu örnekte, hizmet Internet Information Services (IIS) içinde barındırılır ve istemci bir konsol uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="50a1b-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50a1b-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="50a1b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="50a1b-107">[ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) için varsayılan güvenlik, Windows kimlik doğrulaması kullanan ileti güvenliği olur.</span><span class="sxs-lookup"><span data-stu-id="50a1b-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="50a1b-108">Bu örnekteki yapılandırma dosyaları, `mode` [ \<güvenlik](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Message` >özniteliğini`clientCredentialType` ve özniteliğini açıkça olarak ayarlar. `Windows`</span><span class="sxs-lookup"><span data-stu-id="50a1b-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="50a1b-109">Bu değerler, bu bağlamanın varsayılan değerleridir, ancak kullanımları göstermek için aşağıdaki örnek yapılandırmada gösterildiği gibi açıkça yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="50a1b-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="50a1b-110">İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="50a1b-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="50a1b-111">İstemci bağlama, uygun `securityMode` ve `authenticationMode`ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="50a1b-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
  
 <span data-ttu-id="50a1b-112">Hizmet kaynak kodu, <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> çağıranın kimliğine erişmek için nasıl kullanılabileceğini göstermek üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="50a1b-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="50a1b-113">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="50a1b-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="50a1b-114">İlk yöntem- `GetCallerIdentity` ---, çağıran kimliğin adını istemciye geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="50a1b-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="50a1b-115">İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="50a1b-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="50a1b-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="50a1b-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="50a1b-117">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="50a1b-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="50a1b-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="50a1b-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="50a1b-119">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="50a1b-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
