---
title: Birlikte Çalışabilir Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 9cbbd5a34269a7c4a5c33d72487a02df21f2f0fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222711"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="c17e3-102">Birlikte Çalışabilir Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="c17e3-102">Interoperable Object References</span></span>
<span data-ttu-id="c17e3-103">Varsayılan olarak <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değerine göre serileştirir.</span><span class="sxs-lookup"><span data-stu-id="c17e3-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="c17e3-104">Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> türe ait nesneleri serileştirilirken nesne başvuruları korumak için veri sözleşmesi serileştiricisi istemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="c17e3-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="c17e3-105">Oluşturulan XML</span><span class="sxs-lookup"><span data-stu-id="c17e3-105">Generated XML</span></span>  
 <span data-ttu-id="c17e3-106">Örneğin, şu nesne göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="c17e3-106">As an example, consider the following object:</span></span>  
  
```  
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
  
 <span data-ttu-id="c17e3-107">İle <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> kümesine `false` (varsayılan), aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="c17e3-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="c17e3-108">İle <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> kümesine `true`, aşağıdaki XML oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="c17e3-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="c17e3-109">Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> açıklanmayan `id` ve `ref` ve şeması özniteliklerinde bile `preserveObjectReferences` özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="c17e3-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="c17e3-110">IsReference kullanma</span><span class="sxs-lookup"><span data-stu-id="c17e3-110">Using IsReference</span></span>  
 <span data-ttu-id="c17e3-111">Tanımladığı şemaya göre geçerli nesne başvuru bilgisi oluşturmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bir türe ve ayarlama <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrak `true`.</span><span class="sxs-lookup"><span data-stu-id="c17e3-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="c17e3-112">Kullanarak `IsReference` önceki örnek sınıfında `X`:</span><span class="sxs-lookup"><span data-stu-id="c17e3-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 <span data-ttu-id="c17e3-113">Oluşturulan XML aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c17e3-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="c17e3-114">Kullanarak `IsReference` ileti gidiş dönüşü üzerinde uyumluluğu güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="c17e3-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="c17e3-115">Bir türü şemadan oluşturulduğunda bu olmadan ne için XML olarak geri türü mutlaka başlangıçta kabul şemasıyla uyumlu değil gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c17e3-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="c17e3-116">Diğer bir deyişle, ancak `id` ve `ref` öznitelikleri seri hale getirilmiş, özgün şema bu öznitelikler (veya tüm öznitelikler) XML'de oluşmasını barred.</span><span class="sxs-lookup"><span data-stu-id="c17e3-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="c17e3-117">İle `IsReference` veri üyesi uygulanan, üye "başvurulabilir" olduğunda tanınması devam roundtripped.</span><span class="sxs-lookup"><span data-stu-id="c17e3-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17e3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c17e3-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
