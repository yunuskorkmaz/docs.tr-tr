---
description: 'Hakkında daha fazla bilgi edinin: bilinen türler'
title: Bilinen Türler
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: 52aedb226b1e7396820292af3782274bd0ece847
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726331"
---
# <a name="known-types"></a><span data-ttu-id="22003-103">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="22003-103">Known Types</span></span>

<span data-ttu-id="22003-104">Bu örnekte, bir veri sözleşmesindeki türetilmiş türler hakkında bilgilerin nasıl belirtileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="22003-104">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="22003-105">Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="22003-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="22003-106">Nesne odaklı programlamada, başka bir türden devralan bir tür özgün türün yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22003-106">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="22003-107">Hizmet odaklı programlamada türler yerine şemalar iletilir ve bu nedenle, türler arasındaki ilişki korunmaz.</span><span class="sxs-lookup"><span data-stu-id="22003-107">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="22003-108"><xref:System.Runtime.Serialization.KnownTypeAttribute>Özniteliği türetilmiş türler hakkındaki bilgilerin veri sözleşmesine dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="22003-108">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="22003-109">Bu mekanizma kullanılmazsa, bir temel türün beklenildiği bir türetilmiş tür gönderilemez veya alınamaz.</span><span class="sxs-lookup"><span data-stu-id="22003-109">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22003-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="22003-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="22003-111">Hizmet sözleşmesi, aşağıdaki örnek kodda gösterildiği gibi karmaşık sayılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="22003-111">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
```csharp
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="22003-112"><xref:System.Runtime.Serialization.DataContractAttribute>Ve, <xref:System.Runtime.Serialization.DataMemberAttribute> `ComplexNumber` istemci ve hizmet arasında sınıfın hangi alanlarının geçirilebileceğini göstermek için sınıfına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="22003-112">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="22003-113">Türetilmiş sınıf, yerine `ComplexNumberWithMagnitude` kullanılabilir `ComplexNumber` .</span><span class="sxs-lookup"><span data-stu-id="22003-113">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="22003-114"><xref:System.Runtime.Serialization.KnownTypeAttribute> `ComplexNumber` Türündeki özniteliği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="22003-114">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="22003-115">`ComplexNumberWithMagnitude`Tür öğesinden türetilir `ComplexNumber` , ancak ek bir veri üyesi ekler `Magnitude` .</span><span class="sxs-lookup"><span data-stu-id="22003-115">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="22003-116">Bilinen türler özelliğini göstermek için hizmet, `ComplexNumberWithMagnitude` yalnızca toplama ve çıkarma için döndüren bir şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="22003-116">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="22003-117">(Sözleşme, ' i belirtse de `ComplexNumber` , özniteliği nedeniyle bu izin verilir `KnownTypeAttribute` ).</span><span class="sxs-lookup"><span data-stu-id="22003-117">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="22003-118">Çarpma ve bölme hala temel türü döndürüyor `ComplexNumber` .</span><span class="sxs-lookup"><span data-stu-id="22003-118">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="22003-119">İstemcide, hizmet sözleşmesinin ve veri sözleşmesinin her ikisi de, hizmet meta verilerinden [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan generatedClient.cs kaynak dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="22003-119">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="22003-120"><xref:System.Runtime.Serialization.KnownTypeAttribute>Özniteliği hizmetin veri sözleşmesinde belirtildiğinden, istemci, `ComplexNumber` hizmeti kullanırken hem hem de `ComplexNumberWithMagnitude` sınıflarını alabilir.</span><span class="sxs-lookup"><span data-stu-id="22003-120">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="22003-121">İstemci, bir olup olmadığını algılar `ComplexNumberWithMagnitude` ve uygun çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="22003-121">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="22003-122">Örneği çalıştırdığınızda, işlemin istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22003-122">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="22003-123">Bir büyüklük, hizmetin uygulanma biçimi nedeniyle toplama ve çıkarma için yazdırılmıştır ancak çarpma ve bölme için değildir.</span><span class="sxs-lookup"><span data-stu-id="22003-123">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="22003-124">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="22003-124">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="22003-125">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="22003-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="22003-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="22003-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="22003-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="22003-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="22003-128">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="22003-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="22003-129">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="22003-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="22003-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="22003-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="22003-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="22003-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22003-132">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="22003-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
