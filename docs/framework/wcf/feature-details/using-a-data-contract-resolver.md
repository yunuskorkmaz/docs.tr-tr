---
title: Veri Sözleşmesi Çözücü Kullanma
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: d9082d2979cf9bd0837635af567d69ef34c2e312
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975969"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="5af4e-102">Veri Sözleşmesi Çözücü Kullanma</span><span class="sxs-lookup"><span data-stu-id="5af4e-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="5af4e-103">Bir veri anlaşması Çözümleyicisi, bilinen türleri dinamik olarak yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5af4e-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="5af4e-104">Bir veri sözleşmesinin beklenmediği bir tür serileştirildiğinde veya seri durumdan çıkarılırken bilinen türler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5af4e-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="5af4e-105">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="5af4e-105">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="5af4e-106">Bilinen türler normalde statik olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5af4e-106">Known types are normally specified statically.</span></span> <span data-ttu-id="5af4e-107">Bu durum, işlem uygulanırken bir işlemin alabileceği tüm olası türleri bilmeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5af4e-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="5af4e-108">Bu, doğru olmayan ve bilinen türleri dinamik olarak belirleyebilen senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="5af4e-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="5af4e-109">Veri anlaşması Çözümleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5af4e-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="5af4e-110">Bir veri anlaşması Çözümleyicisi oluşturmak, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> ve <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>iki yöntem uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="5af4e-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="5af4e-111">Bu iki yöntem sırasıyla serileştirme ve seri durumundan çıkarma sırasında kullanılan geri çağırmaları uygular.</span><span class="sxs-lookup"><span data-stu-id="5af4e-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="5af4e-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> yöntemi serileştirme sırasında çağrılır ve bir veri anlaşması türü alır ve bunu bir `xsi:type` adı ve ad alanına eşler.</span><span class="sxs-lookup"><span data-stu-id="5af4e-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="5af4e-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> yöntemi, seri durumundan çıkarma sırasında çağrılır ve bir `xsi:type` adı ve ad alanı alır ve bunu bir veri anlaşması türünde çözer.</span><span class="sxs-lookup"><span data-stu-id="5af4e-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="5af4e-114">Bu yöntemlerin her ikisinde de uygulamanızda varsayılan bilinen tür çözümleyici 'yi kullanmak için kullanılabilecek bir `knownTypeResolver` parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="5af4e-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="5af4e-115">Aşağıdaki örnek, `Person`veri sözleşmesi türünden türetilmiş `Customer` adlı bir veri sözleşmesi türü ile eşlemek için <xref:System.Runtime.Serialization.DataContractResolver> nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5af4e-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="5af4e-116">Bir <xref:System.Runtime.Serialization.DataContractResolver> tanımladıktan sonra, aşağıdaki örnekte gösterildiği gibi onu <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusuna geçirerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5af4e-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="5af4e-117">Aşağıdaki örnekte gösterildiği gibi, <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> veya <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> yöntemlerine yapılan çağrıda bir <xref:System.Runtime.Serialization.DataContractResolver> belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5af4e-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="5af4e-118">Ya da aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5af4e-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5af4e-119">Bir hizmete uygulanabilen bir öznitelik uygulayarak bir veri anlaşması çözümleyicisini bildirimli olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5af4e-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="5af4e-120">Daha fazla bilgi için bkz. [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="5af4e-120">For more information, see the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="5af4e-121">Bu örnek, hizmetin davranışına özel bir veri sözleşme Çözümleyicisi ekleyen "KnownAssembly" adlı bir öznitelik uygular.</span><span class="sxs-lookup"><span data-stu-id="5af4e-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af4e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5af4e-122">See also</span></span>

- [<span data-ttu-id="5af4e-123">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="5af4e-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5af4e-124">DataContractSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="5af4e-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [<span data-ttu-id="5af4e-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="5af4e-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
