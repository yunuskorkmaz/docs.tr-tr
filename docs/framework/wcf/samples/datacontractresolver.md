---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 716bcb2bb43656051beffb15da9c7a988942ecd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183790"
---
# <a name="datacontractresolver"></a>DataContractResolver
Bu örnek, serileştirme ve deserialization işlemlerinin <xref:System.Runtime.Serialization.DataContractResolver> sınıf kullanılarak nasıl özelleştirilebildiğini gösterir. Bu örnek, bir xsi:serileştirme ve deserialization sırasında tür gösterimi için CLR türlerini eşlemek için bir DataContractResolver'ın nasıl kullanılacağını gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Örnek aşağıdaki CLR türlerini tanımlar.

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

 Örnek, montajı yükler, bu türlerin her birini ayıklar ve seri hale getirerek deserialize eder. Aşağıdaki <xref:System.Runtime.Serialization.DataContractResolver> örnekte gösterildiği <xref:System.Runtime.Serialization.DataContractResolver>gibi, türemiş sınıfın bir örneğini <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucuya geçirerek serileştirme işlemine takılır.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Örnek daha sonra aşağıdaki kod örneğinde gösterildiği gibi CLR türlerini serihale eder.

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

 Örnek daha sonra aşağıdaki kod örneğinde gösterildiği gibi xsi:türleri deserialize.

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

 Özel <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucuya geçirildiği için, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> bir CLR türünü eşdeğerbir `xsi:type`şekilde eşlemek için serileştirme sırasında çağrılır. Benzer şekilde <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> eşdeğer bir CLR türüne eşlemek `xsi:type` için deserialization sırasında denir. Bu örnekte, <xref:System.Runtime.Serialization.DataContractResolver> aşağıdaki örnekte gösterildiği gibi tanımlanır.

 Aşağıdaki kod örneği, 'den <xref:System.Runtime.Serialization.DataContractResolver>türeyen bir sınıftır.

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

 Örneğin bir parçası olarak, Türler projesi bu örnekte kullanılan tüm türleri ile derleme oluşturur. Seri hale getirilecek türleri eklemek, kaldırmak veya değiştirmek için bu projeyi kullanın.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012'yi kullanarak DCRSample.sln çözüm dosyasını açın.

2. Çözümü çalıştırmak için F5 tuşuna basın

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sözleşmesi Çözücü Kullanma](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
