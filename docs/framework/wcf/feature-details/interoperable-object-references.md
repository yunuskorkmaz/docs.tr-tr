---
title: Birlikte çalışabilir nesne başvuruları
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184699"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="dff0f-102">Birlikte çalışabilir nesne başvuruları</span><span class="sxs-lookup"><span data-stu-id="dff0f-102">Interoperable object references</span></span>
<span data-ttu-id="dff0f-103">Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değere göre serileştirir.</span><span class="sxs-lookup"><span data-stu-id="dff0f-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="dff0f-104">Nesneleri seri <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> hale alırken nesne başvurularını korumak için veri sözleşmesi serileştiricisini eğitmek için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dff0f-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="dff0f-105">Oluşturulan XML</span><span class="sxs-lookup"><span data-stu-id="dff0f-105">Generated XML</span></span>  
 <span data-ttu-id="dff0f-106">Örnek olarak, aşağıdaki nesneyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="dff0f-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="dff0f-107">Ayarlanan <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> `false` (varsayılan) ile aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="dff0f-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="dff0f-108"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> Ayarlamak ile, `true`aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="dff0f-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="dff0f-109">Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> `preserveObjectReferences` özelliği `true`olarak ayarlanmış `ref` olsa bile, şema ve öznitelikleri açıklamıyor. `id`</span><span class="sxs-lookup"><span data-stu-id="dff0f-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="dff0f-110">IsReference'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="dff0f-110">Using IsReference</span></span>  
 <span data-ttu-id="dff0f-111">Bunu açıklayan şemaya göre geçerli olan nesne başvuru bilgilerini oluşturmak <xref:System.Runtime.Serialization.DataContractAttribute> için, özniteliği bir türe <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `true`uygulayın ve bayrağı .</span><span class="sxs-lookup"><span data-stu-id="dff0f-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="dff0f-112">Aşağıdaki örnek, önceki `X` örnekte sınıfı aşağıdakileri ekleyerek `IsReference`değiştirir:</span><span class="sxs-lookup"><span data-stu-id="dff0f-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="dff0f-113">Oluşturulan XML aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dff0f-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="dff0f-114">Kullanarak `IsReference` ileti yuvarlak tripping üzerinde uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="dff0f-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="dff0f-115">Bu olmadan, şema bir tür oluşturulduğunda, bu tür için XML çıkışı mutlaka şema başlangıçta kabul ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="dff0f-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="dff0f-116">Başka bir deyişle, `id` `ref` öznitelikleri serihale edilmiş olsa da, özgün şema bu öznitelikleri (veya tüm öznitelikleri) XML'de oluşmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="dff0f-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="dff0f-117">Bir `IsReference` veri üyesine uygulandığında, üye gidiş-dönüş yapıldığında *başvurulabilir* olarak tanınmaya devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="dff0f-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff0f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dff0f-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
