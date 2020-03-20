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
# <a name="datacontractresolver"></a><span data-ttu-id="d3632-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="d3632-102">DataContractResolver</span></span>
<span data-ttu-id="d3632-103">Bu örnek, serileştirme ve deserialization işlemlerinin <xref:System.Runtime.Serialization.DataContractResolver> sınıf kullanılarak nasıl özelleştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3632-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="d3632-104">Bu örnek, bir xsi:serileştirme ve deserialization sırasında tür gösterimi için CLR türlerini eşlemek için bir DataContractResolver'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3632-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="d3632-105">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d3632-105">Sample Details</span></span>
 <span data-ttu-id="d3632-106">Örnek aşağıdaki CLR türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3632-106">The sample defines the following CLR types.</span></span>

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

 <span data-ttu-id="d3632-107">Örnek, montajı yükler, bu türlerin her birini ayıklar ve seri hale getirerek deserialize eder.</span><span class="sxs-lookup"><span data-stu-id="d3632-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="d3632-108">Aşağıdaki <xref:System.Runtime.Serialization.DataContractResolver> örnekte gösterildiği <xref:System.Runtime.Serialization.DataContractResolver>gibi, türemiş sınıfın bir örneğini <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucuya geçirerek serileştirme işlemine takılır.</span><span class="sxs-lookup"><span data-stu-id="d3632-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="d3632-109">Örnek daha sonra aşağıdaki kod örneğinde gösterildiği gibi CLR türlerini serihale eder.</span><span class="sxs-lookup"><span data-stu-id="d3632-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

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

 <span data-ttu-id="d3632-110">Örnek daha sonra aşağıdaki kod örneğinde gösterildiği gibi xsi:türleri deserialize.</span><span class="sxs-lookup"><span data-stu-id="d3632-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

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

 <span data-ttu-id="d3632-111">Özel <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucuya geçirildiği için, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> bir CLR türünü eşdeğerbir `xsi:type`şekilde eşlemek için serileştirme sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d3632-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="d3632-112">Benzer şekilde <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> eşdeğer bir CLR türüne eşlemek `xsi:type` için deserialization sırasında denir.</span><span class="sxs-lookup"><span data-stu-id="d3632-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="d3632-113">Bu örnekte, <xref:System.Runtime.Serialization.DataContractResolver> aşağıdaki örnekte gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d3632-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="d3632-114">Aşağıdaki kod örneği, 'den <xref:System.Runtime.Serialization.DataContractResolver>türeyen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d3632-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

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

 <span data-ttu-id="d3632-115">Örneğin bir parçası olarak, Türler projesi bu örnekte kullanılan tüm türleri ile derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3632-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="d3632-116">Seri hale getirilecek türleri eklemek, kaldırmak veya değiştirmek için bu projeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3632-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="d3632-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d3632-117">To use this sample</span></span>

1. <span data-ttu-id="d3632-118">Visual Studio 2012'yi kullanarak DCRSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d3632-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="d3632-119">Çözümü çalıştırmak için F5 tuşuna basın</span><span class="sxs-lookup"><span data-stu-id="d3632-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3632-120">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3632-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3632-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d3632-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d3632-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="d3632-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3632-123">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3632-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="d3632-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3632-124">See also</span></span>

- [<span data-ttu-id="d3632-125">Veri Sözleşmesi Çözücü Kullanma</span><span class="sxs-lookup"><span data-stu-id="d3632-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
