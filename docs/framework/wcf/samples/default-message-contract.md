---
title: Varsayılan İleti Sözleşmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183764"
---
# <a name="default-message-contract"></a><span data-ttu-id="8adea-102">Varsayılan İleti Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="8adea-102">Default Message Contract</span></span>
<span data-ttu-id="8adea-103">Varsayılan İleti Sözleşmesi örneği, özel kullanıcı tanımlı iletinin hizmet işlemlerine ve hizmet işlemlerine aktarıldığı bir hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adea-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="8adea-104">Bu örnek, bir hesap makinesi arabirimini yazılı hizmet olarak uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.</span><span class="sxs-lookup"><span data-stu-id="8adea-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="8adea-105">[Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlatılan'da kullanılan toplama, çıkarma, çarpma ve bölme için tek tek hizmet işlemleri yerine, bu örnek hem operandları hem de işleci içeren özel bir ileti geçirir ve aritmetik hesaplama nın sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8adea-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="8adea-106">İstemci bir konsol programıdır (.exe) ve hizmet kitaplığı (.dll) Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="8adea-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="8adea-107">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8adea-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8adea-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8adea-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8adea-109">Hizmette, özel tür `MyMessage`iletilerini kabul eden ve döndüren tek bir hizmet işlemi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8adea-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="8adea-110">Bu örnekte istek ve yanıt iletileri aynı türde olsa da, gerekirse elbette farklı ileti sözleşmeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="8adea-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="8adea-111">Özel `MyMessage` ileti, açıklamalı <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> özniteliklere sahip bir sınıfta tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8adea-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="8adea-112">Bu örnekte yalnızca üçüncü yapıcı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8adea-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="8adea-113">İleti sözleşmelerini kullanmak, SOAP iletisi üzerinde tam kontrol eve sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adea-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="8adea-114">Bu örnekte, <xref:System.ServiceModel.MessageHeaderAttribute> öznitelik bir `Operation` SOAP üstbilgi koymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8adea-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="8adea-115">Operands `N1`, `N2` ve `Result` onlar uygulanan <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelik var çünkü SOAP vücut içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8adea-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="8adea-116">Uygulama sınıfı `Calculate` hizmet çalışması için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="8adea-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="8adea-117">Sınıf, `CalculateService` istek iletisinden operands ve işleci alır ve aşağıdaki örnek kodda gösterildiği gibi istenen hesaplamanın sonucunu içeren bir yanıt iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8adea-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="8adea-118">İstemci için oluşturulan istemci kodu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı ile oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="8adea-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="8adea-119">Araç, gerekirse oluşturulan istemci kodunda otomatik olarak ileti sözleşmesi türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8adea-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="8adea-120">Komut `/messageContract` seçeneği, ileti sözleşmelerinin oluşumunu zorlamak için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8adea-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="8adea-121">Aşağıdaki örnek kod, `MyMessage` istemcinin iletiyi kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adea-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
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
  
 <span data-ttu-id="8adea-122">Örneği çalıştırdığınızda, hesaplamalar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8adea-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="8adea-123">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8adea-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="8adea-124">Bu noktada, istemci ve hizmet işlemi arasında özel kullanıcı tanımlı iletiler geçti.</span><span class="sxs-lookup"><span data-stu-id="8adea-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="8adea-125">İleti sözleşmesi, operands ve sonuçları ileti gövdesinde olduğunu ve işleç bir ileti üstbilgisinde olduğunu tanımladı.</span><span class="sxs-lookup"><span data-stu-id="8adea-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="8adea-126">İleti günlüğe kaydetme, bu ileti yapısını gözlemlemek için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8adea-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8adea-127">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8adea-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8adea-128">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="8adea-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8adea-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8adea-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8adea-130">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8adea-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8adea-131">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8adea-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8adea-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8adea-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8adea-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="8adea-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8adea-134">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8adea-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
