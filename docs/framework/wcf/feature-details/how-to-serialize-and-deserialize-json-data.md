---
title: 'Nasıl yapılır: JSON verileri seri hale getrime ve'
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 797b29fd7ddecd3e3ed85f8cb3a6df93044942ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704348"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="ec0e6-102">Nasıl yapılır: JSON verileri seri hale getrime ve</span><span class="sxs-lookup"><span data-stu-id="ec0e6-102">How to: Serialize and Deserialize JSON Data</span></span>
<span data-ttu-id="ec0e6-103">JSON (JavaScript nesne gösterimi), küçük miktarda bir AJAX içerebilen Web Hizmetleri ile istemci tarayıcıları arasında verileri hızlı değişimleri sağlar verimli veri kodlama biçimi değil.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="ec0e6-104">Bu konuda, .NET türü nesneleri JSON olarak kodlanmış verileri seri hale getirmek ve geri kullanarak .NET türleri örneğine verileri JSON biçiminde seri durumdan çıkarmak gösterilmiştir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-104">This topic demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="ec0e6-105">Bu örnek bir veri sözleşme serileştirme ve seri durumundan çıkarma, kullanıcı tanımlı göstermek için kullanır. `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type.</span></span>  
  
 <span data-ttu-id="ec0e6-106">Normalde, JSON seri hale getirme ve seri durumundan çıkarma otomatik işlenir Windows Communication Foundation (WCF) tarafından AJAX etkinleştirilmiş uç noktalar sunulan hizmet işlemlerinde veri anlaşması türlerini kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-106">Normally, JSON serialization and deserialization is handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="ec0e6-107">Ancak, doğrudan - JSON verileri ile çalışmak gerekebilir. Bazı durumlarda bu konunun gösteren senaryodur.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-107">However, in some cases you may need to work with JSON data directly - this is the scenario that this topic demonstrates.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec0e6-108">Sunucu üzerindeki bir giden yanıt serileştirilmesi sırasında bir hata oluşur veya yanıt işlemi başka bir nedenle bir özel durum oluşturur, bu istemciye bir hata döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-108">If an error occurs during serialization of an outgoing reply on the server or the reply operation throws an exception for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="ec0e6-109">Bu konuda dayanır [JSON serileştirme](../../../../docs/framework/wcf/samples/json-serialization.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-109">This topic is based on the [JSON Serialization](../../../../docs/framework/wcf/samples/json-serialization.md) sample.</span></span>  
  
### <a name="to-define-the-data-contract-for-a-person"></a><span data-ttu-id="ec0e6-110">Bir kişi için veri anlaşması tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="ec0e6-110">To define the data contract for a Person</span></span>  
  
1.  <span data-ttu-id="ec0e6-111">Veri sözleşme tanımlamasına `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="ec0e6-112">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ec0e6-112">For more information about data contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="ec0e6-113">JSON kişiye türün bir örneğini serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="ec0e6-113">To serialize an instance of type Person to JSON</span></span>  
  
1.  <span data-ttu-id="ec0e6-114">Bir örneğini oluşturmak `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  <span data-ttu-id="ec0e6-115">Seri hale getirme `Person` nesnesi kullanarak bir bellek akış <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-115">Serialize the `Person` object to a memory stream using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  <span data-ttu-id="ec0e6-116">Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON verilerini akışa yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  <span data-ttu-id="ec0e6-117">JSON çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="ec0e6-118">JSON kişiden türünün bir örneği seri durumdan çıkarılacak</span><span class="sxs-lookup"><span data-stu-id="ec0e6-118">To deserialize an instance of type Person from JSON</span></span>  
  
1.  <span data-ttu-id="ec0e6-119">JSON olarak kodlanmış veriler yeni bir örneğini seri durumdan `Person` kullanarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  <span data-ttu-id="ec0e6-120">Sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="ec0e6-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec0e6-121">Example</span></span>  
  
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
>  <span data-ttu-id="ec0e6-122">JSON serileştirici, aşağıdaki örnek kodda gösterildiği gibi birden çok üye ile aynı ada sahip veri anlaşmaları için bir seri hale getirme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec0e6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec0e6-123">See also</span></span>
- [<span data-ttu-id="ec0e6-124">Bağımsız JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ec0e6-124">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [<span data-ttu-id="ec0e6-125">JSON ve Diğer Veri Aktarma Biçimleri için Destek</span><span class="sxs-lookup"><span data-stu-id="ec0e6-125">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
