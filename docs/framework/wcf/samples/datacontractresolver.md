---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 75b8ccdef2ee0c8106edf4d25224bbec989ad966
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452972"
---
# <a name="datacontractresolver"></a>DataContractResolver
Bu örnek nasıl serileştirme ve seri durumundan çıkarma işlemleri kullanarak özelleştirilebilir gösterir <xref:System.Runtime.Serialization.DataContractResolver> sınıfı. Bu örnek bir xsi: type temsili serileştirme ve seri durumundan çıkarma sırasında gelen ve CLR Türleri eşleştirmek için bir DataContractResolver kullanmayı gösterir.

## <a name="sample-details"></a>Örnek Ayrıntıları
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

 Örnek derleme yüklenir, bu türlerinin her biri ayıklar ve ardından serileştirir ve bunları seri durumdan çıkarır. <xref:System.Runtime.Serialization.DataContractResolver> Seri hale getirme işlemine örneğini geçirerek takılı <xref:System.Runtime.Serialization.DataContractResolver>-türetilmiş sınıf için <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Örnek CLR türleri aşağıdaki kod örneğinde gösterildiği gibi ardından serileştirir.

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

 Örnek, ardından aşağıdaki kod örneğinde gösterildiği gibi xsi:types çıkarır.

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

 Özel beri <xref:System.Runtime.Serialization.DataContractResolver> için geçirilen <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> bir CLR türü bir eş değeri eşlemek için serileştirme sırasında çağrılır `xsi:type`. Benzer şekilde <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> eşlemek için seri durumundan çıkarma sırasında çağrılır `xsi:type` eşdeğer bir CLR türü. Bu örnekte <xref:System.Runtime.Serialization.DataContractResolver> aşağıdaki örnekte gösterildiği gibi tanımlanmaktadır.

 Aşağıdaki kod örneği, türetilen bir sınıf olan <xref:System.Runtime.Serialization.DataContractResolver>.

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

 Örnek bir parçası olarak, bu örnekte kullanılan tüm türler ile derleme türleri projesi oluşturur. Eklemek, kaldırmak veya seri hale türlerini değiştirmek için bu projeyi kullanın.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1.  Visual Studio 2012 kullanarak DCRSample.sln çözüm dosyasını açın.

2.  Çözümü çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Anlaşması Çözümleyici Kullanma](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
