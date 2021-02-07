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
# <a name="message-security-windows"></a><span data-ttu-id="3819e-103">İleti Güvenliği Windows</span><span class="sxs-lookup"><span data-stu-id="3819e-103">Message Security Windows</span></span>

<span data-ttu-id="3819e-104">Bu örnek <xref:System.ServiceModel.WSHttpBinding> , Windows kimlik doğrulamasıyla ileti düzeyi güvenliği kullanmak için bir bağlamanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3819e-104">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="3819e-105">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="3819e-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="3819e-106">Bu örnekte, hizmet Internet Information Services (IIS) içinde barındırılır ve istemci bir konsol uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="3819e-106">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3819e-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3819e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3819e-108">İçin varsayılan güvenlik, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) Windows kimlik doğrulaması kullanan ileti güvenliğine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="3819e-108">The default security for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="3819e-109">Bu örnekteki yapılandırma dosyaları, `mode` [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Message` ve özniteliğinin özniteliğini açıkça olarak ayarlar `clientCredentialType` `Windows` .</span><span class="sxs-lookup"><span data-stu-id="3819e-109">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="3819e-110">Bu değerler, bu bağlamanın varsayılan değerleridir, ancak kullanımları göstermek için aşağıdaki örnek yapılandırmada gösterildiği gibi açıkça yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3819e-110">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="3819e-111">İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="3819e-111">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="3819e-112">İstemci bağlama, uygun ve ile yapılandırılır `securityMode` `authenticationMode` .</span><span class="sxs-lookup"><span data-stu-id="3819e-112">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
  
 <span data-ttu-id="3819e-113">Hizmet kaynak kodu, <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> çağıranın kimliğine erişmek için nasıl kullanılabileceğini göstermek üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3819e-113">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="3819e-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3819e-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3819e-115">İlk yöntem- `GetCallerIdentity` ---, çağıran kimliğin adını istemciye geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3819e-115">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="3819e-116">İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3819e-116">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3819e-117">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3819e-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3819e-118">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3819e-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3819e-119">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3819e-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3819e-120">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3819e-120">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
