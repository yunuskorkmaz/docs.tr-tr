---
title: Veri Sözleşmesi Çözücü Kullanma
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 844c4e0861c2cf4e6acb2b128ff1f5cefa0f7fa0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279155"
---
# <a name="using-a-data-contract-resolver"></a>Veri Sözleşmesi Çözücü Kullanma
Veri sözleşmesi Çözücü bilinen türleri dinamik olarak yapılandırmanıza olanak sağlar. Bilinen türler seri hale getirme veya bir veri anlaşması tarafından beklendiği bir türü seri durumdan çıkarılırken zaman gerekli değildir. Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Normalde, bilinen türleri statik olarak belirtilir. Bir işlem olası tüm türleri bilmek zorunda anlamına gelir, uygulama işlemi sırasında alabilirsiniz. Bu doğru değildir ve bilinen türleri dinamik olarak belirtmek için önemli senaryolar vardır.  
  
## <a name="creating-a-data-contract-resolver"></a>Veri sözleşmesi Çözücü oluşturma  
 Veri sözleşmesi Çözücü oluşturulmasını ilgilendirir iki yöntem uygulama <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> ve <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Bu iki yöntem serileştirme ve seri durumundan çıkarma sırasında sırasıyla kullanılan geri çağırmaları uygulayın. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Yöntemi serileştirme sırasında çağrılır ve bir veri anlaşması türü alır ve için eşleyen bir `xsi:type` ad ve ad alanı. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Yöntemi seri durumundan çıkarma sırasında çağrılır ve alan bir `xsi:type` ad ve ad alanı ve bir veri anlaşması türü giderir. Bu yöntemlerin ikisi de sahip bir `knownTypeResolver` tür çözümleyici uygulamanızda bilinen varsayılan kullanmak için kullanılan parametre.  
  
 Aşağıdaki örnek nasıl uygulayacağınızı gösteren bir <xref:System.Runtime.Serialization.DataContractResolver> adlı bir veri anlaşması türü gelen ve giden eşlemek için `Customer` veri Sözleşme türünden türetilmiş `Person`.  
  
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
  
 Sonra tanımladığınız bir <xref:System.Runtime.Serialization.DataContractResolver> aktararak kullanabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Belirtebileceğiniz bir <xref:System.Runtime.Serialization.DataContractResolver> çağrıda <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> veya <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> yöntemleri, aşağıdaki örnekte gösterildiği gibi.  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Veya üzerinde ayarlanmış <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 Veri sözleşmesi Çözücü hizmet için uygulanan bir öznitelik uygulayarak bildirimli olarak belirtebilirsiniz.  Daha fazla bilgi için [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) örnek. Bu örnek "KnownAssembly" adlı bir öznitelik uygular bu hizmetin davranışı için özel veri anlaşması çözümleyici ekler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Anlaşması Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [DataContractSerializer Örneği](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
