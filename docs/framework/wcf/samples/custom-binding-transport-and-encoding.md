---
title: Özel Bağlama Taşıma ve Kodlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145170"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="24853-102">Özel Bağlama Taşıma ve Kodlama</span><span class="sxs-lookup"><span data-stu-id="24853-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="24853-103">Özel bir bağlama, ayrık bağlama öğelerinin sıralı bir listesi yle tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24853-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="24853-104">Bu örnek, çeşitli aktarım ve ileti kodlama öğeleriyle özel bir bağlamanın nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="24853-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24853-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="24853-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="24853-106">Bu örnek [Self-Host'a](../../../../docs/framework/wcf/samples/self-host.md)dayanır ve http, TCP ve NamedPipe aktarımlarını özel bağlamalarla desteklemek için üç uç noktayı yapılandırmak üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="24853-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="24853-107">İstemci yapılandırması benzer şekilde değiştirildi ve istemci kodu üç uç noktanın her biriyle iletişim kurmak için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="24853-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="24853-108">Örnek, belirli bir aktarım ve ileti kodlamasını destekleyen özel bir bağlamanın nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="24853-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="24853-109">Bu, `binding` öğe için bir aktarım ve ileti kodlaması yapılandırılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="24853-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="24853-110">Bağlama öğelerinin sıralanması, özel bir bağlama tanımlamada önemlidir, çünkü her biri kanal yığınındaki bir katmanı temsil eder (bkz. [Özel Bağlamalar).](../../../../docs/framework/wcf/extending/custom-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="24853-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="24853-111">Bu örnek üç özel bağlamayı yapılandırır: metin kodlaması içeren bir HTTP aktarım, metin kodlaması içeren bir TCP aktarım ve ikili kodlama içeren bir NamedPipe aktarım.</span><span class="sxs-lookup"><span data-stu-id="24853-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="24853-112">Hizmet yapılandırması özel bağlamaları aşağıdaki gibi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="24853-112">The service configuration defines the custom bindings as follows:</span></span>  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="24853-113">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24853-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="24853-114">İstemci üç uç noktanın her biriyle iletişim kurar ve önce HTTP, sonra TCP ve son olarak NamedPipe'a erişir.</span><span class="sxs-lookup"><span data-stu-id="24853-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="24853-115">Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="24853-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="24853-116">`namedPipeTransport` Bağlama, makineden makineye işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="24853-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="24853-117">Yalnızca aynı makinede iletişim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24853-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="24853-118">Bu nedenle, örneği makineler arası bir senaryoda çalıştırırken, istemci kodu dosyasında aşağıdaki satırları yorumlayın:</span><span class="sxs-lookup"><span data-stu-id="24853-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> <span data-ttu-id="24853-119">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="24853-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="24853-120">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="24853-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="24853-121">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="24853-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="24853-122">Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="24853-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="24853-123">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="24853-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="24853-124">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="24853-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24853-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="24853-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="24853-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="24853-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24853-127">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="24853-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
