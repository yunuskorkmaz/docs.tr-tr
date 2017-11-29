---
title: "Özel Bağlama Taşıma ve Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b4c63a65c141046e833a9c1b0345fe9c029fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="6b77b-102">Özel Bağlama Taşıma ve Kodlama</span><span class="sxs-lookup"><span data-stu-id="6b77b-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="6b77b-103">Özel bağlama ayrık bağlama öğeleri sıralı bir listesi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6b77b-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="6b77b-104">Bu örnek özel bağlama çeşitli aktarım ve öğeleri kodlama ileti ile nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b77b-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b77b-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="6b77b-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6b77b-106">Bu örnek dayanır [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md)ve HTTP, TCP ve NamedPipe taşımaları özel bağlamalarla desteklemek için üç bitiş noktalarını yapılandırmak için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6b77b-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="6b77b-107">İstemci yapılandırması benzer şekilde değiştirilmiş ve her üç uç noktalar ile iletişim kurmak için istemci kodu değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="6b77b-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="6b77b-108">Örnek bir nasıl gösterir, belirli bir destekleyen özel bağlama ve ileti kodlama yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="6b77b-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="6b77b-109">Bu bir taşıma ve kodlama için bir ileti yapılandırarak gerçekleştirilir `binding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6b77b-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="6b77b-110">Bağlama öğeleri sıralama her bir katman kanal yığınında olabilmesinden dolayı bir özel bağlama, tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="6b77b-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="6b77b-111">Bu örnek üç özel bağlamalar yapılandırır: metin kodlaması ile bir HTTP taşıması, metin kodlama ile TCP taşıma ve bir ikili kodlama ile NamedPipe taşıma.</span><span class="sxs-lookup"><span data-stu-id="6b77b-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="6b77b-112">Özel bağlamalar hizmet yapılandırmasını tanımlar gibi:</span><span class="sxs-lookup"><span data-stu-id="6b77b-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="6b77b-113">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6b77b-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="6b77b-114">İstemci, her üç uç noktaları ile ilk HTTP sonra TCP ve son olarak NamedPipe erişme iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="6b77b-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="6b77b-115">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6b77b-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="6b77b-116">`namedPipeTransport` Bağlama makine makine işlemlerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="6b77b-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="6b77b-117">Yalnızca aynı makine üzerindeki iletişim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b77b-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="6b77b-118">Bu nedenle, istemci kodu dosyası aşağıdaki satırları çıkışı örnek makineler arası senaryoda çalıştırırken, Açıklama:</span><span class="sxs-lookup"><span data-stu-id="6b77b-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="6b77b-119">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6b77b-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6b77b-120">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6b77b-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6b77b-121">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b77b-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6b77b-122">C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b77b-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6b77b-123">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b77b-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b77b-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b77b-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6b77b-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6b77b-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6b77b-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6b77b-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b77b-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6b77b-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="6b77b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b77b-128">See Also</span></span>
