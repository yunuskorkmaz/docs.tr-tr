---
description: 'Daha fazla bilgi edinin: birlikte çalışabilen nesne başvuruları'
title: Birlikte çalışabilen nesne başvuruları
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 27c801fb3954c7ea3f821a6588a2229502702989
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802690"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="8d886-103">Birlikte çalışabilen nesne başvuruları</span><span class="sxs-lookup"><span data-stu-id="8d886-103">Interoperable object references</span></span>

<span data-ttu-id="8d886-104">Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değere göre seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8d886-104">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="8d886-105"><xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>Nesneleri serileştirilirken nesne başvurularını korumak üzere veri sözleşmesinin serileştiriciye bildirmek için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d886-105">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="8d886-106">Oluşturulan XML</span><span class="sxs-lookup"><span data-stu-id="8d886-106">Generated XML</span></span>  

 <span data-ttu-id="8d886-107">Örnek olarak, aşağıdaki nesneyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8d886-107">As an example, consider the following object:</span></span>  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 <span data-ttu-id="8d886-108"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> `false` , (Varsayılan) olarak ayarlandığında, aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="8d886-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="8d886-109"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A>, Olarak ayarlanmış olarak `true` , aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="8d886-109">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="8d886-110">Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` `ref` özelliği olarak ayarlanmış olsa bile, şema içindeki ve özniteliklerini tanımlamaz `preserveObjectReferences` `true` .</span><span class="sxs-lookup"><span data-stu-id="8d886-110">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="8d886-111">IsReference kullanma</span><span class="sxs-lookup"><span data-stu-id="8d886-111">Using IsReference</span></span>  

 <span data-ttu-id="8d886-112">Tanımlayan şemaya göre geçerli olan nesne başvuru bilgileri oluşturmak için, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini bir türe uygulayın ve <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrağını olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="8d886-112">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="8d886-113">Aşağıdaki örnek, bir `X` önceki örnekteki sınıfını şunu ekleyerek değiştirir `IsReference` :</span><span class="sxs-lookup"><span data-stu-id="8d886-113">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 <span data-ttu-id="8d886-114">Oluşturulan XML aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8d886-114">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="8d886-115">Kullanma, `IsReference` iletinin gidiş dönüşü üzerinde uyumluluğu güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="8d886-115">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="8d886-116">Bu olmadan, şemadan bir tür oluşturulduğunda, bu tür için XML çıktısı, özgün olarak kabul edilen şemayla uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="8d886-116">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="8d886-117">Diğer bir deyişle, `id` ve `ref` öznitelikleri serileştirildiği halde, özgün şema bu özniteliklerin (veya tüm ÖZNITELIKLERIN) XML 'de oluşmasını önlemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d886-117">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="8d886-118">`IsReference`Bir veri üyesine uygulandığında, üye, yuvarlama sırasında *başvurulabilir* olarak tanınmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="8d886-118">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d886-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d886-119">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
