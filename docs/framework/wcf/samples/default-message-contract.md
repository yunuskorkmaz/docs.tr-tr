---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 23ab534ef31773efc69b6a68e73ec30bde4f6e61
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502665"
---
# <a name="default-message-contract"></a><span data-ttu-id="db8a2-102">Varsayılan İleti Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="db8a2-102">Default Message Contract</span></span>
<span data-ttu-id="db8a2-103">Varsayılan ileti anlaşması örnek, kullanıcı tarafından tanımlanan özel bir ileti için ve hizmet işlemlerine geçirildiği hizmet gösterir.</span><span class="sxs-lookup"><span data-stu-id="db8a2-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="db8a2-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) belirlenmiş bir hizmet olarak bir hesap makinesi arabirimi uygulayan.</span><span class="sxs-lookup"><span data-stu-id="db8a2-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="db8a2-105">Toplama, çıkarma, çarpma ve bölme kullanılan bireysel hizmet işlemlerinde yerine [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), bu örnek, hem işlenen hem de işleç içeren ve döndüren özel bir ileti geçirir. aritmetik hesaplama sonucu.</span><span class="sxs-lookup"><span data-stu-id="db8a2-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="db8a2-106">İstemci bir konsol programı (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmet kitaplığı (.dll).</span><span class="sxs-lookup"><span data-stu-id="db8a2-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="db8a2-107">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="db8a2-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db8a2-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="db8a2-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="db8a2-109">Hizmetinde kabul eder ve özel ileti türü döndüren bir tek hizmet işlemi tanımlanan `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="db8a2-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="db8a2-110">Bu örnekte, istek ve yanıt iletilerinin aynı türde olsa da, bunlar farklı ileti sözleşmeleri Elbette gerekirse olabilir.</span><span class="sxs-lookup"><span data-stu-id="db8a2-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="db8a2-111">Özel ileti `MyMessage` ile ek açıklamalı bir sınıfta tanımlanan <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="db8a2-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="db8a2-112">Yalnızca üçüncü Oluşturucu, bu örnekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db8a2-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="db8a2-113">İleti sözleşmeleri kullanılıyor, SOAP iletisi üzerinde tam denetimle alıştırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="db8a2-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="db8a2-114">Bu örnekte <xref:System.ServiceModel.MessageHeaderAttribute> yerleştirmek için kullanılan öznitelik `Operation` bir SOAP üst bilgisindeki.</span><span class="sxs-lookup"><span data-stu-id="db8a2-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="db8a2-115">İşlenenler `N1`, `N2` ve `Result` SOAP gövdesi içinde sahip oldukları görünür <xref:System.ServiceModel.MessageBodyMemberAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="db8a2-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```  
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="db8a2-116">Uygulama sınıfı kodunu içeren `Calculate` hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="db8a2-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="db8a2-117">`CalculateService` Sınıfı, işleci ve işlenenleri istek iletisi alır ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplama sonucunu içeren bir yanıt iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db8a2-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```  
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="db8a2-118">İstemcisi için oluşturulan istemci kodu oluşturulurken [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="db8a2-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="db8a2-119">Araç, otomatik olarak oluşturulan istemci kodu gerekiyorsa, ileti anlaşması türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db8a2-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="db8a2-120">`/messageContract` İleti sözleşmeleri zorlamanızı komut seçeneği belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="db8a2-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="db8a2-121">Aşağıdaki örnek kodu kullanarak istemciyi gösterir `MyMessage` ileti.</span><span class="sxs-lookup"><span data-stu-id="db8a2-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="db8a2-122">Örneği çalıştırdığında hesaplamalar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="db8a2-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="db8a2-123">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="db8a2-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="db8a2-124">Bu noktada, kullanıcı tanımlı özel iletiler, istemci ve hizmet işlemi arasında geçti.</span><span class="sxs-lookup"><span data-stu-id="db8a2-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="db8a2-125">İşlenenler ve sonuçları ileti gövdesinde olduğunu ve işleci bir ileti üstbilgisinde olduğunu tanımlanan ileti sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="db8a2-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="db8a2-126">İleti günlüğe kaydetme, bu ileti yapı gözlemlemek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="db8a2-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="db8a2-127">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="db8a2-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="db8a2-128">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db8a2-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="db8a2-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db8a2-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="db8a2-130">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db8a2-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db8a2-131">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="db8a2-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="db8a2-132">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="db8a2-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="db8a2-133">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="db8a2-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db8a2-134">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="db8a2-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a><span data-ttu-id="db8a2-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db8a2-135">See Also</span></span>
