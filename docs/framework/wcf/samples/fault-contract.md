---
title: "Hatalı Sözleşme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8fabe025e8eb2fc983094fdb78bcc37a03d0b7da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="fault-contract"></a><span data-ttu-id="6ce97-102">Hatalı Sözleşme</span><span class="sxs-lookup"><span data-stu-id="6ce97-102">Fault Contract</span></span>
<span data-ttu-id="6ce97-103">Hatalı sözleşme örnek, bir istemciye bir hizmetten hata bilgileri iletişim gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ce97-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="6ce97-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), dahili bir özel durum bir hataya dönüştürmek için hizmetine eklenen bazı ek kod.</span><span class="sxs-lookup"><span data-stu-id="6ce97-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="6ce97-105">İstemci bir hata koşulu hizmette zorla sıfıra bölme gerçekleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="6ce97-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ce97-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="6ce97-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6ce97-107">Hesaplayıcı sözleşme içerecek şekilde değiştirilmiş bir <xref:System.ServiceModel.FaultContractAttribute> aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6ce97-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="6ce97-108"><xref:System.ServiceModel.FaultContractAttribute> Öznitelik gösterir `Divide` işlemi türünde bir hata döndürebilir `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="6ce97-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="6ce97-109">Bir arıza serileştirilebilir herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ce97-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="6ce97-110">Bu durumda, `MathFault` bir veri sözleşmesi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6ce97-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="6ce97-111">`Divide` Yöntemi atar bir <xref:System.ServiceModel.FaultException%601> aşağıdaki örnek kodda gösterildiği gibi özel durumu Böl olduğunda sıfır özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="6ce97-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="6ce97-112">Bu durum istemciye gönderilen bir hata ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6ce97-112">This exception results in a fault being sent to the client.</span></span>  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="6ce97-113">İstemci kodu bir hata sıfıra bölme isteyerek zorlar.</span><span class="sxs-lookup"><span data-stu-id="6ce97-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="6ce97-114">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6ce97-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6ce97-115">Bir hata bildirilen sıfıra bölme bakın.</span><span class="sxs-lookup"><span data-stu-id="6ce97-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="6ce97-116">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6ce97-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="6ce97-117">İstemci bunu uygun yakalama tarafından yapar `FaultException<MathFault>` özel durum:</span><span class="sxs-lookup"><span data-stu-id="6ce97-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="6ce97-118">Varsayılan olarak, beklenmeyen özel durum ayrıntıları istemciye hizmetinin güvenli sınır kaçış gelen hizmet uygulaması ayrıntılarını önlemek için gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="6ce97-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="6ce97-119">`FaultContract`Bir sözleşmede hataları tanımlamak ve belirli türde bir özel durum iletilmesi istemci için uygun olarak işaretlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ce97-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="6ce97-120">`FaultException<T>`tüketicilere hataları göndermek için çalışma zamanı mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ce97-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="6ce97-121">Ancak, hata ayıklama sırasında iç hizmet hatası ayrıntılarını görmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ce97-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="6ce97-122">Daha önce açıklanan güvenli davranışı devre dışı bırakmak için her sunucuda işlenmeyen bir özel durum ayrıntıları istemciye gönderilen hata bulunması belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ce97-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="6ce97-123">Bu ayar gerçekleştirilir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="6ce97-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="6ce97-124">Bu kod veya aşağıdaki örnekte gösterildiği gibi yapılandırmasında ya da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ce97-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="6ce97-125">Ayrıca, davranışı ayarlayarak hizmeti ile ilişkilendirilmelidir `behaviorConfiguration` "CalculatorServiceBehavior" yapılandırma dosyasında hizmetin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6ce97-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="6ce97-126">Bu tür hataları istemcide, genel olmayan yakalamak için <xref:System.ServiceModel.FaultException> yakalanan gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ce97-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="6ce97-127">Bu davranış, yalnızca hata ayıklama amacıyla kullanılmalıdır ve hiçbir zaman üretimde etkinleştirilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ce97-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ce97-128">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6ce97-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6ce97-129">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ce97-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6ce97-130">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ce97-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6ce97-131">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ce97-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ce97-132">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ce97-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ce97-133">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6ce97-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6ce97-134">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6ce97-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ce97-135">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6ce97-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="6ce97-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ce97-136">See Also</span></span>
