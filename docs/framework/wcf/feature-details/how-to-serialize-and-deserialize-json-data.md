---
title: 'Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma'
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: f51ffb180adfc8310c91ff3c1ec7b7725f6b8b15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492596"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="da809-102">Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma</span><span class="sxs-lookup"><span data-stu-id="da809-102">How to: Serialize and Deserialize JSON Data</span></span>
<span data-ttu-id="da809-103">JSON (JavaScript nesne gösterimi) küçük miktarda veri istemci tarayıcıları ve AJAX etkinleştirilmiş Web hizmetleri arasında hızlı alışverişleri sağlayan bir verimli veri kodlama biçimidir.</span><span class="sxs-lookup"><span data-stu-id="da809-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="da809-104">Bu konuda JSON olarak kodlanmış veri .NET türü nesneleri seri hale getirmek ve geri kullanarak .NET türleri örneğine verileri JSON biçiminde seri durumdan nasıl oluşturulduğunu gösteren <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="da809-104">This topic demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="da809-105">Bu örnek bir veri sözleşmesi seri hale getirme ve seri durumdan çıkarma işlemi kullanıcı tarafından tanımlanan göstermek için kullanır. `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="da809-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type.</span></span>  
  
 <span data-ttu-id="da809-106">Normalde, JSON seri hale getirme ve seri durumdan gerçekleştirilir otomatik olarak Windows Communication Foundation (WCF) tarafından AJAX etkinleştirilmiş Uç noktalara sunulan hizmet işlemleri veri sözleşme türleri kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="da809-106">Normally, JSON serialization and deserialization is handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="da809-107">Ancak, JSON verileriyle doğrudan - çözüm bulmanız gerekebilecek bazı durumlarda bu, bu konuda gösteren senaryodur.</span><span class="sxs-lookup"><span data-stu-id="da809-107">However, in some cases you may need to work with JSON data directly - this is the scenario that this topic demonstrates.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da809-108">Sunucu üzerinde giden bir cevap serileştirme sırasında bir hata oluşursa veya yanıt işlemi başka bir nedenle bir özel durum oluşturur, istemciye bir hata döndürdüğü değil.</span><span class="sxs-lookup"><span data-stu-id="da809-108">If an error occurs during serialization of an outgoing reply on the server or the reply operation throws an exception for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="da809-109">Bu konuda dayanır [JSON serileştirmesi](../../../../docs/framework/wcf/samples/json-serialization.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="da809-109">This topic is based on the [JSON Serialization](../../../../docs/framework/wcf/samples/json-serialization.md) sample.</span></span>  
  
### <a name="to-define-the-data-contract-for-a-person"></a><span data-ttu-id="da809-110">Bir kişi için veri sözleşmesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="da809-110">To define the data contract for a Person</span></span>  
  
1.  <span data-ttu-id="da809-111">Veri sözleşmesi tanımlayın `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfına ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri.</span><span class="sxs-lookup"><span data-stu-id="da809-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="da809-112">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="da809-112">For more information about data contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="da809-113">JSON kişiye türünün bir örneği seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="da809-113">To serialize an instance of type Person to JSON</span></span>  
  
1.  <span data-ttu-id="da809-114">Bir örneğini oluşturmak `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="da809-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  <span data-ttu-id="da809-115">Seri hale `Person` kullanarak bir bellek akış nesnesine <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="da809-115">Serialize the `Person` object to a memory stream using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  <span data-ttu-id="da809-116">Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON veri akışına yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="da809-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  <span data-ttu-id="da809-117">JSON çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da809-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="da809-118">JSON kişiden türünün bir örneği serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="da809-118">To deserialize an instance of type Person from JSON</span></span>  
  
1.  <span data-ttu-id="da809-119">JSON olarak kodlanmış veriler yeni bir örneğini seri durumdan `Person` kullanarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="da809-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  <span data-ttu-id="da809-120">Sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="da809-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="da809-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="da809-121">Example</span></span>  
  
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
>  <span data-ttu-id="da809-122">JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi aynı ada sahip birden çok üyeli veri sözleşmeleri için seri hale getirme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da809-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da809-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da809-123">See Also</span></span>  
 [<span data-ttu-id="da809-124">Bağımsız JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="da809-124">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="da809-125">JSON ve Diğer Veri Aktarma Biçimleri için Destek</span><span class="sxs-lookup"><span data-stu-id="da809-125">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
