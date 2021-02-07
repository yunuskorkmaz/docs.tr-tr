---
description: 'Daha fazla bilgi edinin: özel bağlama taşıma ve kodlama'
title: Özel Bağlama Taşıma ve Kodlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: d579414d77836abecc685b758e81d0775c3ca142
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732689"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="cb7fa-103">Özel Bağlama Taşıma ve Kodlama</span><span class="sxs-lookup"><span data-stu-id="cb7fa-103">Custom Binding Transport and Encoding</span></span>

<span data-ttu-id="cb7fa-104">Özel bağlama, farklı bağlama öğelerinin sıralı bir listesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-104">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="cb7fa-105">Bu örnek, çeşitli taşıma ve ileti kodlama öğeleriyle özel bağlamanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-105">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb7fa-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cb7fa-107">Bu örnek, [kendi kendine ana bilgisayar](self-host.md)tabanlıdır ve özel BAĞLAMALARLA http, TCP ve NamedPipe aktarımlarını desteklemek üzere üç uç nokta yapılandırmak üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-107">This sample is based on the [Self-Host](self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="cb7fa-108">İstemci yapılandırması benzer şekilde değiştirilmiştir ve istemci kodu üç uç noktanın her biriyle iletişim kuracak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-108">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="cb7fa-109">Örnek, belirli bir aktarımı ve ileti kodlamasını destekleyen bir özel bağlamanın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-109">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="cb7fa-110">Bu, bir taşıma ve öğe için ileti kodlaması yapılandırılarak gerçekleştirilir `binding` .</span><span class="sxs-lookup"><span data-stu-id="cb7fa-110">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="cb7fa-111">Bağlama öğelerinin sıralaması, her biri kanal yığınındaki bir katmanı temsil ettiğinden (bkz. [Özel Bağlamalar](../extending/custom-bindings.md)) özel bir bağlama tanımlamak açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-111">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="cb7fa-112">Bu örnek üç özel bağlamayı yapılandırır: metin kodlamalı HTTP taşıması, metin kodlamalı bir TCP taşıması ve ikili kodlamalı bir NamedPipe taşıması.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-112">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="cb7fa-113">Hizmet yapılandırması özel bağlamaları aşağıdaki gibi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="cb7fa-113">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="cb7fa-114">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsolu penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-114">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="cb7fa-115">İstemci, birinci HTTP, ardından TCP ve son olarak NamedPipe 'a erişerek üç uç noktanın her biriyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-115">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="cb7fa-116">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-116">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="cb7fa-117">`namedPipeTransport`Bağlama, makineden makineye işlemleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-117">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="cb7fa-118">Yalnızca aynı makine üzerindeki iletişim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-118">It is used only for communication on the same machine.</span></span> <span data-ttu-id="cb7fa-119">Bu nedenle, örneği bir çapraz makine senaryosunda çalıştırırken, istemci kod dosyasında aşağıdaki satırları açıklama olarak kodlayın:</span><span class="sxs-lookup"><span data-stu-id="cb7fa-119">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
> <span data-ttu-id="cb7fa-120">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-120">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb7fa-121">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cb7fa-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cb7fa-122">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cb7fa-123">Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-123">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cb7fa-124">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cb7fa-125">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb7fa-126">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cb7fa-127">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cb7fa-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb7fa-128">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cb7fa-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
