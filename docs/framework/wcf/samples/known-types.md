---
title: Bilinen Türler
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: dae271384905df890b2f42196d6e0aadad66be6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591845"
---
# <a name="known-types"></a><span data-ttu-id="9ca8c-102">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="9ca8c-102">Known Types</span></span>
<span data-ttu-id="9ca8c-103">Bu örnekte, bir veri sözleşmesindeki türetilmiş türler hakkında bilgilerin nasıl belirtileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="9ca8c-104">Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="9ca8c-105">Nesne odaklı programlamada, başka bir türden devralan bir tür özgün türün yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="9ca8c-106">Hizmet odaklı programlamada türler yerine şemalar iletilir ve bu nedenle, türler arasındaki ilişki korunmaz.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="9ca8c-107"><xref:System.Runtime.Serialization.KnownTypeAttribute>Özniteliği türetilmiş türler hakkındaki bilgilerin veri sözleşmesine dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="9ca8c-108">Bu mekanizma kullanılmazsa, bir temel türün beklenildiği bir türetilmiş tür gönderilemez veya alınamaz.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ca8c-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9ca8c-110">Hizmet sözleşmesi, aşağıdaki örnek kodda gösterildiği gibi karmaşık sayılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="9ca8c-111"><xref:System.Runtime.Serialization.DataContractAttribute>Ve, <xref:System.Runtime.Serialization.DataMemberAttribute> `ComplexNumber` istemci ve hizmet arasında sınıfın hangi alanlarının geçirilebileceğini göstermek için sınıfına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="9ca8c-112">Türetilmiş sınıf, yerine `ComplexNumberWithMagnitude` kullanılabilir `ComplexNumber` .</span><span class="sxs-lookup"><span data-stu-id="9ca8c-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="9ca8c-113"><xref:System.Runtime.Serialization.KnownTypeAttribute> `ComplexNumber` Türündeki özniteliği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
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
  
 <span data-ttu-id="9ca8c-114">`ComplexNumberWithMagnitude`Tür öğesinden türetilir `ComplexNumber` , ancak ek bir veri üyesi ekler `Magnitude` .</span><span class="sxs-lookup"><span data-stu-id="9ca8c-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
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
  
 <span data-ttu-id="9ca8c-115">Bilinen türler özelliğini göstermek için hizmet, `ComplexNumberWithMagnitude` yalnızca toplama ve çıkarma için döndüren bir şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="9ca8c-116">(Sözleşme, ' i belirtse de `ComplexNumber` , özniteliği nedeniyle bu izin verilir `KnownTypeAttribute` ).</span><span class="sxs-lookup"><span data-stu-id="9ca8c-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="9ca8c-117">Çarpma ve bölme hala temel türü döndürüyor `ComplexNumber` .</span><span class="sxs-lookup"><span data-stu-id="9ca8c-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
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
  
 <span data-ttu-id="9ca8c-118">İstemcide, hizmet sözleşmesinin ve veri sözleşmesinin her ikisi de, hizmet meta verilerinden [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan generatedClient.cs kaynak dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="9ca8c-119"><xref:System.Runtime.Serialization.KnownTypeAttribute>Özniteliği hizmetin veri sözleşmesinde belirtildiğinden, istemci, `ComplexNumber` hizmeti kullanırken hem hem de `ComplexNumberWithMagnitude` sınıflarını alabilir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="9ca8c-120">İstemci, bir olup olmadığını algılar `ComplexNumberWithMagnitude` ve uygun çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="9ca8c-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
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
  
 <span data-ttu-id="9ca8c-121">Örneği çalıştırdığınızda, işlemin istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="9ca8c-122">Bir büyüklük, hizmetin uygulanma biçimi nedeniyle toplama ve çıkarma için yazdırılmıştır ancak çarpma ve bölme için değildir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="9ca8c-123">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-123">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ca8c-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9ca8c-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9ca8c-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9ca8c-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9ca8c-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9ca8c-128">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ca8c-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9ca8c-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9ca8c-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ca8c-131">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9ca8c-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
