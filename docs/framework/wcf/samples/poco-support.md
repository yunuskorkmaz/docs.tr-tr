---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: bb4f8b0a5eb20be50a2d3ba9a15d66fd7fc573f8
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452816"
---
# <a name="poco-support"></a><span data-ttu-id="66fe5-102">POCO Desteği</span><span class="sxs-lookup"><span data-stu-id="66fe5-102">POCO Support</span></span>
<span data-ttu-id="66fe5-103">Bu örnek, işaretsiz türleri için serileştirme destek gösterir; diğer bir deyişle, türleri, serileştirme öznitelikleri uygulanmadı, bazen ifade türleri olarak düz eski CLR nesnesi (POCO).</span><span class="sxs-lookup"><span data-stu-id="66fe5-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="66fe5-104"><xref:System.Runtime.Serialization.DataContractSerializer> Varsayılan bir oluşturucuya sahip tüm genel işaretsiz türleri için bir veri anlaşması algılar.</span><span class="sxs-lookup"><span data-stu-id="66fe5-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a default constructor.</span></span> <span data-ttu-id="66fe5-105">Veri sözleşmeleri, yapılandırılmış veriler için ve hizmetlerden geçmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="66fe5-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="66fe5-106">İşaretsiz türleri hakkında daha fazla bilgi için bkz. [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="66fe5-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="66fe5-107">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), ancak karmaşık sayılar yerine basit sayısal türler kullanır.</span><span class="sxs-lookup"><span data-stu-id="66fe5-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="66fe5-108">Aynı zamanda benzeyen [temel veri anlaşması](../../../../docs/framework/wcf/samples/basic-data-contract.md) , hariç örnek <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="66fe5-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="66fe5-109">Hizmet, Internet Information Services (IIS) tarafından barındırılan ve istemcisinin bir konsol uygulaması (.exe).</span><span class="sxs-lookup"><span data-stu-id="66fe5-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66fe5-110">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="66fe5-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="66fe5-111">`ComplexNumber` Sınıfı kullanılan `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="66fe5-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="66fe5-112">`ComplexNumber` Türü yok <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> , aşağıdaki örnek kodda gösterildiği gibi öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="66fe5-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="66fe5-113">Varsayılan olarak, tüm ortak özellikler ve alanları serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="66fe5-113">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="66fe5-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="66fe5-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="66fe5-115">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66fe5-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="66fe5-116">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66fe5-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="66fe5-117">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66fe5-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="66fe5-118">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="66fe5-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66fe5-119">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="66fe5-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="66fe5-120">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="66fe5-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66fe5-121">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="66fe5-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="66fe5-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66fe5-122">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [<span data-ttu-id="66fe5-123">Seri Hale Getirilebilir Türler</span><span class="sxs-lookup"><span data-stu-id="66fe5-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
