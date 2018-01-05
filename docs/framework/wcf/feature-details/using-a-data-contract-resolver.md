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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28bba68c985191b69fea3b7ab85812917a827b30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-data-contract-resolver"></a>Veri Sözleşmesi Çözücü Kullanma
Veri sözleşmesi Çözücü bilinen türleri dinamik olarak yapılandırmanıza izin verir. Bilinen türler seri hale getirme veya bir veri sözleşmesine göre beklendiği bir türü seri durumdan gereklidir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Bilinen türler normalde statik olarak belirtilir. Bunun anlamı tüm olası türleri bir işlem bilmesi gerekir, uygulama işlemi sırasında alabilirsiniz. Bu doğru değildir ve bilinen türleri dinamik olarak belirtmek için önemli senaryolar vardır.  
  
## <a name="creating-a-data-contract-resolver"></a>Veri sözleşmesi Çözücü oluşturma  
 Veri sözleşmesi Çözücü oluşturulmasını ilgilendirir iki yöntem uygulama <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> ve <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Bu iki yöntem sırasıyla seri hale getirme ve seri durumdan çıkarma, sırasında kullanılan geri aramalar uygulayın. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Yöntemi serileştirme sırasında çağrılır ve bir veri sözleşmesi türü alır ve varlığa eşlenen bir `xsi:type` adı ve ad alanı. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Yöntemi seri durumdan çıkarma sırasında çağrılır ve sürer bir `xsi:type` ve ad alanına ve bir veri sözleşmesi türü giderir. Bu yöntemlerin her ikisi de sahip bir `knownTypeResolver` tür çözümleyici uygulamanızda bilinen varsayılan kullanmak üzere kullanılan parametre.  
  
 Aşağıdaki örnekte nasıl uygulanacağını gösterir bir <xref:System.Runtime.Serialization.DataContractResolver> adlı bir veri sözleşmesi türü gelen ve giden eşlemek için `Customer` bir veri sözleşmesi türden türetilmiş `Person`.  
  
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
  
 Tanımladığınız sonra bir <xref:System.Runtime.Serialization.DataContractResolver> geçirerek kullanabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Belirleyebileceğiniz bir <xref:System.Runtime.Serialization.DataContractSerializer> çağrıda <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> veya <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> aşağıdaki örnekte gösterildiği gibi yöntemleri.  
  
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
  
 Veri sözleşmesi Çözücü bir hizmete uygulanan bir öznitelik uygulayarak bildirimli olarak belirtebilirsiniz.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) örnek. Bu örnek "KnownAssembly" adlı bir öznitelik uygular, özel veri sözleşmesi Çözücü hizmetin davranışa ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Anlaşması Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [DataContractSerializer Örneği](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
