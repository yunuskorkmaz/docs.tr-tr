---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 6c04a055a5ce87ac285d05b086c22b900bc92145
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253654"
---
# <a name="datacontractresolver"></a>DataContractResolver

Bu örnek, serileştirme ve seri kaldırma işlemlerinin sınıfı kullanılarak nasıl özelleştirilebileceğini gösterir <xref:System.Runtime.Serialization.DataContractResolver> . Bu örnek, serileştirme ve seri durumundan çıkarma sırasında CLR türlerini bir xsi: tür gösterimine eşlemek için bir DataContractResolver 'ın nasıl kullanılacağını gösterir.

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

 Örnek, derlemeyi yükler, bu türlerin her birini ayıklar ve sonra bunları seri hale getirir ve onları yeniden sıralar. , <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> Aşağıdaki örnekte gösterildiği gibi, türetilmiş sınıfın bir örneğini oluşturucuya geçirerek serileştirme işlemine takılır.

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

 Özel, <xref:System.Runtime.Serialization.DataContractResolver> oluşturucuya geçirildiğinden, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> SERILEŞTIRME sırasında bir clr türünü eşdeğer olarak eşlemek için çağrılır `xsi:type` . Benzer şekilde, <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> `xsi:type` BIR eşdeğer clr türüne eşlemek için seri durumundan çıkarma sırasında çağrılır. Bu örnekte, <xref:System.Runtime.Serialization.DataContractResolver> Aşağıdaki örnekte gösterildiği gibi tanımlanmıştır.

 Aşağıdaki kod örneği, öğesinden türetilen bir sınıftır <xref:System.Runtime.Serialization.DataContractResolver> .

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sözleşmesi Çözücü Kullanma](../feature-details/using-a-data-contract-resolver.md)
