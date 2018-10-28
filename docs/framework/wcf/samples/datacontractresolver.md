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
# <a name="datacontractresolver"></a><span data-ttu-id="02650-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="02650-102">DataContractResolver</span></span>
<span data-ttu-id="02650-103">Bu örnek nasıl serileştirme ve seri durumundan çıkarma işlemleri kullanarak özelleştirilebilir gösterir <xref:System.Runtime.Serialization.DataContractResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="02650-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="02650-104">Bu örnek bir xsi: type temsili serileştirme ve seri durumundan çıkarma sırasında gelen ve CLR Türleri eşleştirmek için bir DataContractResolver kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="02650-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="02650-105">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="02650-105">Sample Details</span></span>
 <span data-ttu-id="02650-106">Örnek aşağıdaki CLR türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02650-106">The sample defines the following CLR types.</span></span>

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

 <span data-ttu-id="02650-107">Örnek derleme yüklenir, bu türlerinin her biri ayıklar ve ardından serileştirir ve bunları seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="02650-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="02650-108"><xref:System.Runtime.Serialization.DataContractResolver> Seri hale getirme işlemine örneğini geçirerek takılı <xref:System.Runtime.Serialization.DataContractResolver>-türetilmiş sınıf için <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="02650-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="02650-109">Örnek CLR türleri aşağıdaki kod örneğinde gösterildiği gibi ardından serileştirir.</span><span class="sxs-lookup"><span data-stu-id="02650-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

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

 <span data-ttu-id="02650-110">Örnek, ardından aşağıdaki kod örneğinde gösterildiği gibi xsi:types çıkarır.</span><span class="sxs-lookup"><span data-stu-id="02650-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

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

 <span data-ttu-id="02650-111">Özel beri <xref:System.Runtime.Serialization.DataContractResolver> için geçirilen <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> bir CLR türü bir eş değeri eşlemek için serileştirme sırasında çağrılır `xsi:type`.</span><span class="sxs-lookup"><span data-stu-id="02650-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="02650-112">Benzer şekilde <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> eşlemek için seri durumundan çıkarma sırasında çağrılır `xsi:type` eşdeğer bir CLR türü.</span><span class="sxs-lookup"><span data-stu-id="02650-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="02650-113">Bu örnekte <xref:System.Runtime.Serialization.DataContractResolver> aşağıdaki örnekte gösterildiği gibi tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02650-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="02650-114">Aşağıdaki kod örneği, türetilen bir sınıf olan <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="02650-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

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

 <span data-ttu-id="02650-115">Örnek bir parçası olarak, bu örnekte kullanılan tüm türler ile derleme türleri projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02650-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="02650-116">Eklemek, kaldırmak veya seri hale türlerini değiştirmek için bu projeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="02650-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="02650-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="02650-117">To use this sample</span></span>

1.  <span data-ttu-id="02650-118">Visual Studio 2012 kullanarak DCRSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="02650-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2.  <span data-ttu-id="02650-119">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="02650-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="02650-120">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="02650-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="02650-121">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="02650-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="02650-122">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="02650-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02650-123">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="02650-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="02650-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02650-124">See Also</span></span>  
 [<span data-ttu-id="02650-125">Veri Anlaşması Çözümleyici Kullanma</span><span class="sxs-lookup"><span data-stu-id="02650-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
