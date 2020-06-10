---
title: Veri Sözleşmesi Çözücü Kullanma
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 20abd4d928fc51eb359949ecbb216615e9659b7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595030"
---
# <a name="using-a-data-contract-resolver"></a>Veri Sözleşmesi Çözücü Kullanma
Bir veri anlaşması Çözümleyicisi, bilinen türleri dinamik olarak yapılandırmanıza olanak tanır. Bir veri sözleşmesinin beklenmediği bir tür serileştirildiğinde veya seri durumdan çıkarılırken bilinen türler gereklidir. Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md). Bilinen türler normalde statik olarak belirtilir. Bu durum, işlem uygulanırken bir işlemin alabileceği tüm olası türleri bilmeniz gerektiği anlamına gelir. Bu, doğru olmayan ve bilinen türleri dinamik olarak belirleyebilen senaryolar vardır.  
  
## <a name="creating-a-data-contract-resolver"></a>Veri anlaşması Çözümleyicisi oluşturma  
 Bir veri anlaşması Çözümleyicisi oluşturmak, iki yöntem ve uygulamayı <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> içerir <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> . Bu iki yöntem sırasıyla serileştirme ve seri durumundan çıkarma sırasında kullanılan geri çağırmaları uygular. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>Yöntem serileştirme sırasında çağrılır ve bir veri anlaşması türü alır ve bunu bir `xsi:type` ad ve ad alanına eşler. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>Yöntemi seri durumundan çıkarma sırasında çağrılır ve bir `xsi:type` ad ve ad alanı alır ve bunu bir veri anlaşması türü olarak çözer. Bu yöntemlerin her ikisinde de, `knownTypeResolver` uygulamanızda varsayılan olarak bilinen tür çözümleyici 'yi kullanmak için kullanılabilecek bir parametre vardır.  
  
 Aşağıdaki örnek, bir <xref:System.Runtime.Serialization.DataContractResolver> `Customer` veri anlaşması türünden türetilmiş adlı bir veri sözleşmesi türüne ve bir eşlemenin nasıl uygulanacağını gösterir `Person` .  
  
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
  
 Bir tanımladıktan sonra, <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> Aşağıdaki örnekte gösterildiği gibi onu oluşturucuya geçirerek kullanabilirsiniz.  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, veya yöntemlerine bir çağrısında belirtebilirsiniz.  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Ya da bunu, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Aşağıdaki örnekte gösterildiği gibi ' de ayarlayabilirsiniz.  
  
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
  
 Bir hizmete uygulanabilen bir öznitelik uygulayarak bir veri anlaşması çözümleyicisini bildirimli olarak belirtebilirsiniz.  Daha fazla bilgi için bkz. [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) örneği. Bu örnek, hizmetin davranışına özel bir veri sözleşme Çözümleyicisi ekleyen "KnownAssembly" adlı bir öznitelik uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Anlaşması Bilinen Türler](data-contract-known-types.md)
- [DataContractSerializer Örneği](../samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../samples/knownassemblyattribute.md)
