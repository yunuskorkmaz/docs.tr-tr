---
title: "Veri Sözleşmesi Çözücü Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc28086e0e4489df5594c4b1ce5ec16cea9b1e61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="fc132-102">Veri Sözleşmesi Çözücü Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc132-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="fc132-103">Veri sözleşmesi Çözücü bilinen türleri dinamik olarak yapılandırmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="fc132-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="fc132-104">Bilinen türler seri hale getirme veya bir veri sözleşmesine göre beklendiği bir türü seri durumdan gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fc132-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fc132-105">bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fc132-105"> known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="fc132-106">Bilinen türler normalde statik olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fc132-106">Known types are normally specified statically.</span></span> <span data-ttu-id="fc132-107">Bunun anlamı tüm olası türleri bir işlem bilmesi gerekir, uygulama işlemi sırasında alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc132-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="fc132-108">Bu doğru değildir ve bilinen türleri dinamik olarak belirtmek için önemli senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="fc132-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="fc132-109">Veri sözleşmesi Çözücü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc132-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="fc132-110">Veri sözleşmesi Çözücü oluşturulmasını ilgilendirir iki yöntem uygulama <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> ve <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc132-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="fc132-111">Bu iki yöntem sırasıyla seri hale getirme ve seri durumdan çıkarma, sırasında kullanılan geri aramalar uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fc132-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="fc132-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Yöntemi serileştirme sırasında çağrılır ve bir veri sözleşmesi türü alır ve varlığa eşlenen bir `xsi:type` adı ve ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fc132-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="fc132-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Yöntemi seri durumdan çıkarma sırasında çağrılır ve sürer bir `xsi:type` ve ad alanına ve bir veri sözleşmesi türü giderir.</span><span class="sxs-lookup"><span data-stu-id="fc132-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="fc132-114">Bu yöntemlerin her ikisi de sahip bir `knownTypeResolver` tür çözümleyici uygulamanızda bilinen varsayılan kullanmak üzere kullanılan parametre.</span><span class="sxs-lookup"><span data-stu-id="fc132-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="fc132-115">Aşağıdaki örnekte nasıl uygulanacağını gösterir bir <xref:System.Runtime.Serialization.DataContractResolver> adlı bir veri sözleşmesi türü gelen ve giden eşlemek için `Customer` bir veri sözleşmesi türden türetilmiş `Person`.</span><span class="sxs-lookup"><span data-stu-id="fc132-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="fc132-116">Tanımladığınız sonra bir <xref:System.Runtime.Serialization.DataContractResolver> geçirerek kullanabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="fc132-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="fc132-117">Belirleyebileceğiniz bir <xref:System.Runtime.Serialization.DataContractSerializer> çağrıda <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> veya <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> aşağıdaki örnekte gösterildiği gibi yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="fc132-117">You can specify a <xref:System.Runtime.Serialization.DataContractSerializer> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> methods, as shown in the following example.</span></span>  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="fc132-118">Veya üzerinde ayarlanmış <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fc132-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fc132-119">Veri sözleşmesi Çözücü bir hizmete uygulanan bir öznitelik uygulayarak bildirimli olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc132-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="fc132-120">[KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="fc132-120"> the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="fc132-121">Bu örnek "KnownAssembly" adlı bir öznitelik uygular, özel veri sözleşmesi Çözücü hizmetin davranışa ekler.</span><span class="sxs-lookup"><span data-stu-id="fc132-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc132-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc132-122">See Also</span></span>  
 [<span data-ttu-id="fc132-123">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="fc132-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="fc132-124">DataContractSerializer örneği</span><span class="sxs-lookup"><span data-stu-id="fc132-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [<span data-ttu-id="fc132-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="fc132-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
