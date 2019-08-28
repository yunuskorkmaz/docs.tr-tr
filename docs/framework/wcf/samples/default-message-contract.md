---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 2115ac88c52efca09d32a870fc52905f80f6f746
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045048"
---
# <a name="default-message-contract"></a><span data-ttu-id="48931-102">Varsayılan İleti Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="48931-102">Default Message Contract</span></span>
<span data-ttu-id="48931-103">Varsayılan Ileti sözleşmesi örneği, hizmet işlemlerine ve bu işlemlerden özel kullanıcı tanımlı bir iletinin geçirildiği bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="48931-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="48931-104">Bu örnek, türü belirlenmiş bir hizmet olarak Hesaplayıcı arabirimi uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="48931-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="48931-105">[Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), çıkarma, çarpma ve bölme işlemlerinde kullanılan tek tek hizmet işlemleri yerine, bu örnek hem işlenen hem de işlecini içeren özel bir ileti geçirir ve bu işlemin sonucunu döndürür. aritmetik hesaplama.</span><span class="sxs-lookup"><span data-stu-id="48931-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="48931-106">İstemci bir konsol programıdır (. exe) ve hizmet kitaplığı (. dll) Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="48931-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="48931-107">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="48931-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48931-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="48931-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="48931-109">Hizmette, Özel iletileri `MyMessage`kabul eden ve döndüren tek bir hizmet işlemi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="48931-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="48931-110">Bu örnekte istek ve yanıt iletileri aynı türde olsa da, gerektiğinde farklı ileti sözleşmeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="48931-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="48931-111">Özel ileti `MyMessage` , ve<xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageContractAttribute> öznitelikleri<xref:System.ServiceModel.MessageBodyMemberAttribute> ile açıklanmış bir sınıfta tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="48931-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="48931-112">Bu örnekte yalnızca üçüncü Oluşturucu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48931-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="48931-113">İleti sözleşmelerini kullanmak, SOAP iletisi üzerinde tam denetim yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="48931-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="48931-114">Bu örnekte, <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği bir soap üstbilgisine koymak `Operation` için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48931-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="48931-115">İşlenenler `N1` <xref:System.ServiceModel.MessageBodyMemberAttribute> ve özniteliği uygulanmış olduğundan SOAP gövdesi içinde görüntülenir.`Result` `N2`</span><span class="sxs-lookup"><span data-stu-id="48931-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="48931-116">Uygulama sınıfı, `Calculate` hizmet işleminin kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="48931-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="48931-117">`CalculateService` Sınıfı, istek iletisinden işlenen ve işleci edinir ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplamanın sonucunu içeren bir yanıt iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48931-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="48931-118">İstemci için üretilen istemci kodu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracıyla oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="48931-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="48931-119">Araç, gerekirse oluşturulan istemci kodunda ileti sözleşme türlerini otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48931-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="48931-120">İleti sözleşmelerinin oluşturulmasını zorlamak için komutseçeneğibelirtilebilir.`/messageContract`</span><span class="sxs-lookup"><span data-stu-id="48931-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="48931-121">Aşağıdaki örnek kod, `MyMessage` iletisini kullanarak istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="48931-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage() 
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="48931-122">Örneği çalıştırdığınızda, hesaplamalar istemci konsolu penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="48931-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="48931-123">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="48931-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="48931-124">Bu noktada, istemci ve hizmet işlemi arasında özel kullanıcı tanımlı iletiler geçirilir.</span><span class="sxs-lookup"><span data-stu-id="48931-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="48931-125">İleti anlaşması, işlenen ve sonuçların ileti gövdesinde olduğunu ve işlecin bir ileti üstbilgisinde olduğunu tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="48931-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="48931-126">İleti günlüğe kaydetme, bu ileti yapısını gözlemleyecek şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="48931-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48931-127">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="48931-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="48931-128">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="48931-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="48931-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="48931-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="48931-130">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="48931-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="48931-131">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="48931-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48931-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48931-132">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="48931-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="48931-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48931-134">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="48931-134">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
