---
title: 'Nasıl yapılır: DataContractJsonSerializer kullanma'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 3cf8cc52587a64e7273ab9e0de0b1751d00827cf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901222"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="00f4a-102">DataContractJsonSerializer 'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="00f4a-102">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="00f4a-103">Bu makale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="00f4a-103">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="00f4a-104">JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)API 'leri öneririz.</span><span class="sxs-lookup"><span data-stu-id="00f4a-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="00f4a-105">JSON (JavaScript Nesne Gösterimi), istemci tarayıcıları ve AJAX özellikli Web Hizmetleri arasında küçük miktarlarda verilerin hızlı bir şekilde değiş tokuşlanmasını sağlayan etkili bir veri kodlama biçimidir.</span><span class="sxs-lookup"><span data-stu-id="00f4a-105">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="00f4a-106">Bu makalede, .NET tür nesnelerinin JSON kodlu verilere nasıl serileştirildiğini ve sonra JSON biçimindeki verilerin serisini .NET türlerinin örneklerine nasıl seri hale getirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="00f4a-106">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="00f4a-107">Bu örnek, Kullanıcı tanımlı `Person` türünün serileştirilmesi ve serisini göstermek için bir veri sözleşmesi kullanır ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanır.</span><span class="sxs-lookup"><span data-stu-id="00f4a-107">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="00f4a-108">Genellikle, JSON serileştirme ve seri durumundan çıkarma, AJAX etkin uç noktalar üzerinde kullanıma sunulan hizmet işlemlerinde veri sözleşme türlerini kullandığınızda otomatik olarak Windows Communication Foundation (WCF) tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="00f4a-108">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="00f4a-109">Ancak, bazı durumlarda JSON verileriyle doğrudan çalışmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="00f4a-109">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="00f4a-110">Bu makale, [DataContractJsonSerializer örneğine](../samples/json-serialization.md)dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="00f4a-110">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="00f4a-111">Bir kişi türü için veri sözleşmesini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="00f4a-111">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="00f4a-112"><xref:System.Runtime.Serialization.DataContractAttribute> sınıfa ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine ekleyerek, seri hale getirmek istediğiniz üyelere `Person` için veri sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="00f4a-112">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="00f4a-113">Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="00f4a-113">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

    ```csharp
    [DataContract]
    internal class Person
    {
        [DataMember]
        internal string name;

        [DataMember]
        internal int age;
    }
    ```

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="00f4a-114">Kişi türündeki bir örneği JSON 'a seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="00f4a-114">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="00f4a-115">Sunucuda giden bir yanıtın serileştirilmesi sırasında veya başka bir nedenle hata oluşursa istemciye hata olarak döndürülmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="00f4a-115">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="00f4a-116">`Person` türünün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="00f4a-116">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="00f4a-117"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanarak `Person` nesnesini bir bellek akışına seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="00f4a-117">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="00f4a-118">Akışa JSON verisi yazmak için <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="00f4a-118">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="00f4a-119">JSON çıkışını göster.</span><span class="sxs-lookup"><span data-stu-id="00f4a-119">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="00f4a-120">JSON 'dan kişi türündeki bir örnek serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="00f4a-120">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="00f4a-121">JSON kodlu verileri, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemini kullanarak yeni bir `Person` örneğine serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="00f4a-121">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="00f4a-122">Sonuçları göster.</span><span class="sxs-lookup"><span data-stu-id="00f4a-122">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="00f4a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="00f4a-123">Example</span></span>

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> <span data-ttu-id="00f4a-124">JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi, aynı ada sahip birden çok üyesi olan veri sözleşmeleri için bir serileştirme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="00f4a-124">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

```csharp
[DataContract]
public class TestDuplicateDataBase
{
    [DataMember]
    public int field1 = 123;
}

[DataContract]
public class TestDuplicateDataDerived : TestDuplicateDataBase
{
    [DataMember]
    public new int field1 = 999;
}
```

## <a name="see-also"></a><span data-ttu-id="00f4a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00f4a-125">See also</span></span>

- [<span data-ttu-id="00f4a-126">.NET 'te JSON serileştirme</span><span class="sxs-lookup"><span data-stu-id="00f4a-126">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
