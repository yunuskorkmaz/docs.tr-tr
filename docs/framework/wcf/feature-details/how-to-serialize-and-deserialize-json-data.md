---
title: 'Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0bebdbb3d74d58db093c4ec1e0e88138c7080335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947892"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="ece72-102">Nasıl yapılır: JSON verilerini serileştirme ve serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="ece72-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="ece72-103">JSON (JavaScript Nesne Gösterimi), istemci tarayıcıları ve AJAX özellikli Web Hizmetleri arasında küçük miktarlarda verilerin hızlı bir şekilde değiş tokuşlanmasını sağlayan etkili bir veri kodlama biçimidir.</span><span class="sxs-lookup"><span data-stu-id="ece72-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="ece72-104">Bu makalede, .NET tür nesnelerinin JSON kodlu verilere nasıl serileştirildiğini ve sonra JSON biçimindeki verilerin serisini .NET türlerinin örneklerine nasıl seri hale getirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ece72-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="ece72-105">Bu örnek, Kullanıcı tanımlı `Person` bir türün serileştirilmesi ve serisini göstermek için bir veri sözleşmesi kullanır ve kullanır. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="ece72-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="ece72-106">Genellikle, JSON serileştirme ve seri durumundan çıkarma, AJAX etkin uç noktalar üzerinde kullanıma sunulan hizmet işlemlerinde veri sözleşme türlerini kullandığınızda otomatik olarak Windows Communication Foundation (WCF) tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="ece72-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="ece72-107">Ancak, bazı durumlarda JSON verileriyle doğrudan çalışmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ece72-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
> <span data-ttu-id="ece72-108">Sunucuda giden bir yanıtın serileştirilmesi sırasında veya başka bir nedenle hata oluşursa istemciye hata olarak döndürülmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="ece72-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="ece72-109">Bu makale, [JSON serileştirme](../samples/json-serialization.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="ece72-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="ece72-110">Bir kişi türü için veri sözleşmesini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="ece72-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="ece72-111">İçin `Person` veri sözleşmesini, <xref:System.Runtime.Serialization.DataContractAttribute> seri hale getirmek istediğiniz üyelere sınıfına ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine ekleyerek tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ece72-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="ece72-112">Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ece72-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="ece72-113">Kişi türündeki bir örneği JSON 'a seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="ece72-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="ece72-114">`Person` Türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ece72-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="ece72-115">Kullanarak nesnesini bir bellek akışına serileştirme. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> `Person`</span><span class="sxs-lookup"><span data-stu-id="ece72-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="ece72-116">JSON verilerini akışa yazmak için yönteminikullanın.<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A></span><span class="sxs-lookup"><span data-stu-id="ece72-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="ece72-117">JSON çıkışını göster.</span><span class="sxs-lookup"><span data-stu-id="ece72-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="ece72-118">JSON 'dan kişi türündeki bir örnek serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="ece72-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="ece72-119">JSON kodlu verileri ' ın `Person` <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metodunu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanarak yeni bir örneğine serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="ece72-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="ece72-120">Sonuçları göster.</span><span class="sxs-lookup"><span data-stu-id="ece72-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="ece72-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ece72-121">Example</span></span>  
  
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
> <span data-ttu-id="ece72-122">JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi, aynı ada sahip birden çok üyesi olan veri sözleşmeleri için bir serileştirme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ece72-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ece72-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ece72-123">See also</span></span>

- [<span data-ttu-id="ece72-124">Tek başına JSON serileştirmesi</span><span class="sxs-lookup"><span data-stu-id="ece72-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="ece72-125">JSON ve diğer veri aktarımı biçimleri için destek</span><span class="sxs-lookup"><span data-stu-id="ece72-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
