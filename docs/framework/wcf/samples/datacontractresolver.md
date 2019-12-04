---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 101c33ca197be9dff52a73c844dd0b006e62b2ac
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716587"
---
# <a name="datacontractresolver"></a>DataContractResolver
Bu örnek, serileştirme ve seri kaldırma işlemlerinin <xref:System.Runtime.Serialization.DataContractResolver> sınıfı kullanılarak nasıl özelleştirilebileceğini gösterir. Bu örnek, serileştirme ve seri durumundan çıkarma sırasında CLR türlerini bir xsi: tür gösterimine eşlemek için bir DataContractResolver 'ın nasıl kullanılacağını gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Örnek, aşağıdaki CLR türlerini tanımlar.

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 Örnek, derlemeyi yükler, bu türlerin her birini ayıklar ve sonra bunları seri hale getirir ve onları yeniden sıralar. <xref:System.Runtime.Serialization.DataContractResolver>, aşağıdaki örnekte gösterildiği gibi <xref:System.Runtime.Serialization.DataContractResolver>türetilmiş sınıfın bir örneğini <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusuna geçirerek serileştirme işlemine takılır.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Örnek, aşağıdaki kod örneğinde gösterildiği gibi CLR türlerini seri hale getirir.

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 Örnek, aşağıdaki kod örneğinde gösterildiği gibi xsi: Types öğesini de kaldırır.

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 Özel <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusuna geçirildiğinden, bir CLR türünü eşdeğer bir `xsi:type`eşlemek için serileştirme sırasında <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> çağırılır. Benzer şekilde, `xsi:type` bir eşdeğer CLR türüne eşlemek için seri durumundan çıkarma sırasında <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> çağrılır. Bu örnekte, <xref:System.Runtime.Serialization.DataContractResolver> aşağıdaki örnekte gösterildiği gibi tanımlanmıştır.

 Aşağıdaki kod örneği, <xref:System.Runtime.Serialization.DataContractResolver>türetilen bir sınıftır.

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 Örneğin, Types projesi, derlemeyi Bu örnekte kullanılan tüm türlerle oluşturur. Bu projeyi, serileştirilecek türleri eklemek, kaldırmak veya değiştirmek için kullanın.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak DCRSample. sln çözüm dosyasını açın.

2. Çözümü çalıştırmak için F5 'e basın

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Anlaşması Çözümleyici Kullanma](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
