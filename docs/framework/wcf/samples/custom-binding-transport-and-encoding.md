---
title: Özel Bağlama Taşıma ve Kodlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: ee15fd37390f8bf4ca3bc287f9a3dbd5f8ebd935
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658996"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="1ab03-102">Özel Bağlama Taşıma ve Kodlama</span><span class="sxs-lookup"><span data-stu-id="1ab03-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="1ab03-103">Özel bağlama ayrık bağlama öğelerinin sıralı bir listesi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1ab03-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="1ab03-104">Bu örnek, çeşitli taşıma ve kodlama öğeleri ileti özel bağlama yapılandırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ab03-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ab03-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="1ab03-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1ab03-106">Bu örnek dayanır [barındırma](../../../../docs/framework/wcf/samples/self-host.md)ve özel bağlamalar HTTP, TCP ve NamedPipe taşımalar desteklemek için üç uç noktalarını yapılandırma değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="1ab03-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="1ab03-107">İstemci yapılandırması benzer şekilde değiştirildiği ve her biri üç uç noktaları ile iletişim kurmak için istemci kodu değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="1ab03-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="1ab03-108">Örnek gösterilmektedir, belirli taşıma destekleyen özel bağlama ve ileti kodlama yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="1ab03-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="1ab03-109">Bu bir taşıma ve kodlama için bir ileti yapılandırılarak gerçekleştirilir `binding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1ab03-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="1ab03-110">Bağlama öğelerinin sıralama her bir katman kanal yığınında temsil ettiği için bir özel bağlamayı tanımlamak önemlidir (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="1ab03-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="1ab03-111">Bu örnek, üç özel bağlamalar yapılandırır: metin kodlama ile bir HTTP aktarımı ve bir TCP taşıması metin kodlama ile ikili kodlama ile NamedPipe aktarım.</span><span class="sxs-lookup"><span data-stu-id="1ab03-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="1ab03-112">Özel bağlamalar hizmet yapılandırmasını tanımlar gibi:</span><span class="sxs-lookup"><span data-stu-id="1ab03-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="1ab03-113">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1ab03-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="1ab03-114">İstemci, her üç uç noktaları ile ilk HTTP daha sonra TCP ve son olarak NamedPipe erişim iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="1ab03-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="1ab03-115">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1ab03-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="1ab03-116">`namedPipeTransport` Bağlama makineden makineye işlemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1ab03-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="1ab03-117">Yalnızca aynı makinede iletişim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ab03-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="1ab03-118">Bu nedenle, örnek bir çapraz makine senaryosunda çalıştırırken, istemci kod dosyasında aşağıdaki satırları açıklama satırı yapın:</span><span class="sxs-lookup"><span data-stu-id="1ab03-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="1ab03-119">Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.</span><span class="sxs-lookup"><span data-stu-id="1ab03-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1ab03-120">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1ab03-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1ab03-121">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1ab03-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1ab03-122">Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1ab03-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1ab03-123">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1ab03-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1ab03-124">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="1ab03-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1ab03-125">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1ab03-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1ab03-126">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1ab03-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1ab03-127">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ab03-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="1ab03-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ab03-128">See Also</span></span>
