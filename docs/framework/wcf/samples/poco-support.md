---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183412"
---
# <a name="poco-support"></a><span data-ttu-id="707e0-102">POCO Desteği</span><span class="sxs-lookup"><span data-stu-id="707e0-102">POCO Support</span></span>
<span data-ttu-id="707e0-103">Bu örnek, işaretlenmemiş türler için serileştirme desteğini gösterir; diğer bir şey, serileştirme özniteliklerinin uygulanmadığı, bazen Düz Eski CLR Nesnesi (POCO) türleri olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="707e0-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="707e0-104">Parametresiz <xref:System.Runtime.Serialization.DataContractSerializer> bir oluşturucusu olan tüm genel işaretlenmemiş türler için bir veri sözleşmesi çıkar.</span><span class="sxs-lookup"><span data-stu-id="707e0-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="707e0-105">Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden aktarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="707e0-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="707e0-106">İşaretlenmemiş türler hakkında daha fazla bilgi için [Serializable Türleri'ne](../../../../docs/framework/wcf/feature-details/serializable-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="707e0-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="707e0-107">Bu örnek [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır, ancak ilkel sayısal türler yerine karmaşık sayılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="707e0-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="707e0-108">Ayrıca, özniteliklerin ve <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerin kullanılmaması [dışında, Temel Veri Sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md) örneğine de benzer.</span><span class="sxs-lookup"><span data-stu-id="707e0-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="707e0-109">Hizmet Internet Information Services (IIS) tarafından barındırılan ve istemci bir konsol uygulamasıdır (.exe).</span><span class="sxs-lookup"><span data-stu-id="707e0-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="707e0-110">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="707e0-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="707e0-111">Sınıf `ComplexNumber` ' da `ServiceContract`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="707e0-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="707e0-112">Tür, `ComplexNumber` aşağıdaki örnek <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> kodda gösterildiği gibi özniteliklere ve özniteliklere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="707e0-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="707e0-113">Varsayılan olarak, tüm ortak özellikler ve alanlar seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="707e0-113">By default, all public properties and fields are serialized.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="707e0-114">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="707e0-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="707e0-115">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="707e0-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="707e0-116">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="707e0-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="707e0-117">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="707e0-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="707e0-118">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="707e0-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="707e0-119">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="707e0-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="707e0-120">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="707e0-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="707e0-121">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="707e0-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="707e0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="707e0-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="707e0-123">Seri Hale Getirilebilir Türler</span><span class="sxs-lookup"><span data-stu-id="707e0-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
