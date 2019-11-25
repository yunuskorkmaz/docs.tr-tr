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
# <a name="using-a-data-contract-resolver"></a>Veri Sözleşmesi Çözücü Kullanma
Bir veri anlaşması Çözümleyicisi, bilinen türleri dinamik olarak yapılandırmanıza olanak tanır. Bir veri sözleşmesinin beklenmediği bir tür serileştirildiğinde veya seri durumdan çıkarılırken bilinen türler gereklidir. Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Bilinen türler normalde statik olarak belirtilir. Bu durum, işlem uygulanırken bir işlemin alabileceği tüm olası türleri bilmeniz gerektiği anlamına gelir. Bu, doğru olmayan ve bilinen türleri dinamik olarak belirleyebilen senaryolar vardır.  
  
## <a name="creating-a-data-contract-resolver"></a>Veri anlaşması Çözümleyicisi oluşturma  
 Bir veri anlaşması Çözümleyicisi oluşturmak, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> ve <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>iki yöntem uygulamayı içerir. Bu iki yöntem sırasıyla serileştirme ve seri durumundan çıkarma sırasında kullanılan geri çağırmaları uygular. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> yöntemi serileştirme sırasında çağrılır ve bir veri anlaşması türü alır ve bunu bir `xsi:type` adı ve ad alanına eşler. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> yöntemi, seri durumundan çıkarma sırasında çağrılır ve bir `xsi:type` adı ve ad alanı alır ve bunu bir veri anlaşması türünde çözer. Bu yöntemlerin her ikisinde de uygulamanızda varsayılan bilinen tür çözümleyici 'yi kullanmak için kullanılabilecek bir `knownTypeResolver` parametresi vardır.  
  
 Aşağıdaki örnek, `Person`veri sözleşmesi türünden türetilmiş `Customer` adlı bir veri sözleşmesi türü ile eşlemek için <xref:System.Runtime.Serialization.DataContractResolver> nasıl uygulanacağını gösterir.  
  
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
  
 Bir <xref:System.Runtime.Serialization.DataContractResolver> tanımladıktan sonra, aşağıdaki örnekte gösterildiği gibi onu <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusuna geçirerek kullanabilirsiniz.  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Aşağıdaki örnekte gösterildiği gibi, <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> veya <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> yöntemlerine yapılan çağrıda bir <xref:System.Runtime.Serialization.DataContractResolver> belirtebilirsiniz.  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Ya da aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ayarlayabilirsiniz.  
  
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
  
 Bir hizmete uygulanabilen bir öznitelik uygulayarak bir veri anlaşması çözümleyicisini bildirimli olarak belirtebilirsiniz.  Daha fazla bilgi için bkz. [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) örneği. Bu örnek, hizmetin davranışına özel bir veri sözleşme Çözümleyicisi ekleyen "KnownAssembly" adlı bir öznitelik uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Anlaşması Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [DataContractSerializer Örneği](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
