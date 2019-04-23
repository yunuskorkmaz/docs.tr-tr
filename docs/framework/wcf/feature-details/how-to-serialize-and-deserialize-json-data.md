---
title: 'Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 7edce66a23021fa03a6f98b3b847a5b671c17124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336960"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="eaa38-102">Nasıl yapılır: JSON verileri seri hale getrime ve</span><span class="sxs-lookup"><span data-stu-id="eaa38-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="eaa38-103">JSON (JavaScript nesne gösterimi), küçük miktarda bir AJAX içerebilen Web Hizmetleri ile istemci tarayıcıları arasında verileri hızlı değişimleri sağlar verimli veri kodlama biçimi değil.</span><span class="sxs-lookup"><span data-stu-id="eaa38-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="eaa38-104">Bu makale, JSON olarak kodlanmış veri .NET türü nesneleri serileştirmek ve ardından geri .NET türleri örneğine verileri JSON biçiminde seri durumdan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eaa38-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="eaa38-105">Bu örnek bir veri sözleşme serileştirme ve seri durumundan çıkarma, kullanıcı tanımlı göstermek için kullanır. `Person` türüne ve kullandığı <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="eaa38-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="eaa38-106">AJAX etkinleştirilmiş uç noktalar sunulan hizmet işlemlerinde veri anlaşması türlerini kullandığınızda normalde, JSON seri hale getirme ve seri durumundan çıkarma otomatik olarak Windows Communication Foundation (WCF) tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="eaa38-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="eaa38-107">Ancak, bazı durumlarda JSON verileri ile doğrudan çalışmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="eaa38-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
>  <span data-ttu-id="eaa38-108">Sunucuda veya başka bir nedenle bir giden yanıt serileştirilmesi sırasında bir hata meydana gelirse, bu istemciye bir hata döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="eaa38-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="eaa38-109">Bu makalede dayanır [JSON serileştirme](../samples/json-serialization.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="eaa38-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="eaa38-110">Bir kişi türü için veri anlaşması tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="eaa38-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="eaa38-111">Veri sözleşme tanımlamasına `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri.</span><span class="sxs-lookup"><span data-stu-id="eaa38-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="eaa38-112">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="eaa38-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="eaa38-113">JSON kişiye türün bir örneğini serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="eaa38-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="eaa38-114">Bir örneğini oluşturmak `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="eaa38-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="eaa38-115">Seri hale getirme `Person` kullanarak bellek akışı nesnesine <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="eaa38-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="eaa38-116">Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON verilerini akışa yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eaa38-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="eaa38-117">JSON çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaa38-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="eaa38-118">JSON kişiden türünün bir örneği seri durumdan çıkarılacak</span><span class="sxs-lookup"><span data-stu-id="eaa38-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="eaa38-119">JSON olarak kodlanmış veriler yeni bir örneğini seri durumdan `Person` kullanarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="eaa38-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="eaa38-120">Sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaa38-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="eaa38-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="eaa38-121">Example</span></span>  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="eaa38-122">JSON serileştirici, aşağıdaki örnek kodda gösterildiği gibi birden çok üye ile aynı ada sahip veri anlaşmaları için bir seri hale getirme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eaa38-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eaa38-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaa38-123">See also</span></span>

- [<span data-ttu-id="eaa38-124">Bağımsız JSON seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="eaa38-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="eaa38-125">Biçimleri JSON desteği ve diğer veri aktarma</span><span class="sxs-lookup"><span data-stu-id="eaa38-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
