---
title: Veri Sözleşmesi Çözücü Kullanma
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: b1c545d84db68f4b13925dd9088cc9d81050b5e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918573"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="352ef-102">Veri Sözleşmesi Çözücü Kullanma</span><span class="sxs-lookup"><span data-stu-id="352ef-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="352ef-103">Veri sözleşmesi Çözücü bilinen türleri dinamik olarak yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="352ef-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="352ef-104">Bilinen türler seri hale getirme veya bir veri anlaşması tarafından beklendiği bir türü seri durumdan çıkarılırken zaman gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="352ef-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="352ef-105">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="352ef-105">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="352ef-106">Normalde, bilinen türleri statik olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="352ef-106">Known types are normally specified statically.</span></span> <span data-ttu-id="352ef-107">Bir işlem olası tüm türleri bilmek zorunda anlamına gelir, uygulama işlemi sırasında alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352ef-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="352ef-108">Bu doğru değildir ve bilinen türleri dinamik olarak belirtmek için önemli senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="352ef-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="352ef-109">Veri sözleşmesi Çözücü oluşturma</span><span class="sxs-lookup"><span data-stu-id="352ef-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="352ef-110">Veri sözleşmesi Çözücü oluşturulmasını ilgilendirir iki yöntem uygulama <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> ve <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="352ef-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="352ef-111">Bu iki yöntem serileştirme ve seri durumundan çıkarma sırasında sırasıyla kullanılan geri çağırmaları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="352ef-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="352ef-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Yöntemi serileştirme sırasında çağrılır ve bir veri anlaşması türü alır ve için eşleyen bir `xsi:type` ad ve ad alanı.</span><span class="sxs-lookup"><span data-stu-id="352ef-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="352ef-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Yöntemi seri durumundan çıkarma sırasında çağrılır ve alan bir `xsi:type` ad ve ad alanı ve bir veri anlaşması türü giderir.</span><span class="sxs-lookup"><span data-stu-id="352ef-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="352ef-114">Bu yöntemlerin ikisi de sahip bir `knownTypeResolver` tür çözümleyici uygulamanızda bilinen varsayılan kullanmak için kullanılan parametre.</span><span class="sxs-lookup"><span data-stu-id="352ef-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="352ef-115">Aşağıdaki örnek nasıl uygulayacağınızı gösteren bir <xref:System.Runtime.Serialization.DataContractResolver> adlı bir veri anlaşması türü gelen ve giden eşlemek için `Customer` veri Sözleşme türünden türetilmiş `Person`.</span><span class="sxs-lookup"><span data-stu-id="352ef-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="352ef-116">Sonra tanımladığınız bir <xref:System.Runtime.Serialization.DataContractResolver> aktararak kullanabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="352ef-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="352ef-117">Belirtebileceğiniz bir <xref:System.Runtime.Serialization.DataContractResolver> çağrıda <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> veya <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> yöntemleri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="352ef-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="352ef-118">Veya üzerinde ayarlanmış <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="352ef-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```  
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="352ef-119">Veri sözleşmesi Çözücü hizmet için uygulanan bir öznitelik uygulayarak bildirimli olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="352ef-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="352ef-120">Daha fazla bilgi için [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="352ef-120">For more information, see the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="352ef-121">Bu örnek "KnownAssembly" adlı bir öznitelik uygular bu hizmetin davranışı için özel veri anlaşması çözümleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="352ef-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352ef-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="352ef-122">See also</span></span>

- [<span data-ttu-id="352ef-123">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="352ef-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="352ef-124">DataContractSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="352ef-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [<span data-ttu-id="352ef-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="352ef-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
