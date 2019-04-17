---
title: Birlikte çalışabilir nesne başvuruları
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610645"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="12131-102">Birlikte çalışabilir nesne başvuruları</span><span class="sxs-lookup"><span data-stu-id="12131-102">Interoperable object references</span></span>
<span data-ttu-id="12131-103">Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değerine göre serileştirir.</span><span class="sxs-lookup"><span data-stu-id="12131-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="12131-104">Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bildirmesine nesne serileştirilirken nesne başvuruları korumak için veri sözleşmesi serileştiricisi özelliği.</span><span class="sxs-lookup"><span data-stu-id="12131-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="12131-105">Oluşturulan XML</span><span class="sxs-lookup"><span data-stu-id="12131-105">Generated XML</span></span>  
 <span data-ttu-id="12131-106">Örneğin, şu nesne göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="12131-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="12131-107">İle <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> kümesine `false` (varsayılan), aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="12131-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="12131-108">İle <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> kümesine `true`, aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="12131-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="12131-109">Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> açıklanmamaktadır `id` ve `ref` ve şeması özniteliklerinde bile `preserveObjectReferences` özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="12131-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="12131-110">IsReference kullanma</span><span class="sxs-lookup"><span data-stu-id="12131-110">Using IsReference</span></span>  
 <span data-ttu-id="12131-111">Tanımladığı şemaya göre geçerli nesne başvuru bilgisi oluşturmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bir türe ve ayarlama <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrak `true`.</span><span class="sxs-lookup"><span data-stu-id="12131-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="12131-112">Aşağıdaki örnek, sınıf değiştirir `X` ekleyerek önceki örnekte `IsReference`:</span><span class="sxs-lookup"><span data-stu-id="12131-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="12131-113">Oluşturulan XML aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="12131-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="12131-114">Kullanarak `IsReference` ileti gidiş dönüşü üzerinde uyumluluğu güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="12131-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="12131-115">Bir türü şemadan oluşturulduğunda bu olmadan XML için türü mutlaka başlangıçta kabul şemasıyla uyumlu değil çıktı.</span><span class="sxs-lookup"><span data-stu-id="12131-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="12131-116">Diğer bir deyişle, ancak `id` ve `ref` öznitelikleri seri hale getirilmiş, özgün şema bu öznitelikler (veya tüm öznitelikler) XML'de oluşmasını barred.</span><span class="sxs-lookup"><span data-stu-id="12131-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="12131-117">İle `IsReference` veri üyesi uygulanan, üye olarak tanınması devam *başvurulabilir* olduğunda gidiş dönüşlü.</span><span class="sxs-lookup"><span data-stu-id="12131-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12131-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12131-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
