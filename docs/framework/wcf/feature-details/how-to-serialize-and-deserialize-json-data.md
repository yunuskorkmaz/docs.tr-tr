---
title: "Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: deb02217b5d2a79cdf90d511658657f642ca1fc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="78d7a-102">Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma</span><span class="sxs-lookup"><span data-stu-id="78d7a-102">How to: Serialize and Deserialize JSON Data</span></span>
<span data-ttu-id="78d7a-103">JSON (JavaScript nesne gösterimi) küçük miktarda veri istemci tarayıcıları ve AJAX etkinleştirilmiş Web hizmetleri arasında hızlı alışverişleri sağlayan bir verimli veri kodlama biçimidir.</span><span class="sxs-lookup"><span data-stu-id="78d7a-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="78d7a-104">Bu konuda JSON olarak kodlanmış veri .NET türü nesneleri seri hale getirmek ve geri kullanarak .NET türleri örneğine verileri JSON biçiminde seri durumdan nasıl oluşturulduğunu gösteren <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="78d7a-104">This topic demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="78d7a-105">Bu örnek bir veri sözleşmesi seri hale getirme ve seri durumdan çıkarma işlemi kullanıcı tarafından tanımlanan göstermek için kullanır. `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="78d7a-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type.</span></span>  
  
 <span data-ttu-id="78d7a-106">Normalde, JSON seri hale getirme ve seri durumdan çıkarma gerçekleştirilir tarafından otomatik olarak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] AJAX etkinleştirilmiş Uç noktalara sunulan hizmet işlemleri veri sözleşme türleri kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="78d7a-106">Normally, JSON serialization and deserialization is handled automatically by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="78d7a-107">Ancak, JSON verileriyle doğrudan - çözüm bulmanız gerekebilecek bazı durumlarda bu, bu konuda gösteren senaryodur.</span><span class="sxs-lookup"><span data-stu-id="78d7a-107">However, in some cases you may need to work with JSON data directly - this is the scenario that this topic demonstrates.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78d7a-108">Sunucu üzerinde giden bir cevap serileştirme sırasında bir hata oluşursa veya yanıt işlemi başka bir nedenle bir özel durum oluşturur, istemciye bir hata döndürdüğü değil.</span><span class="sxs-lookup"><span data-stu-id="78d7a-108">If an error occurs during serialization of an outgoing reply on the server or the reply operation throws an exception for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="78d7a-109">Bu konuda dayanır [JSON serileştirmesi](../../../../docs/framework/wcf/samples/json-serialization.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="78d7a-109">This topic is based on the [JSON Serialization](../../../../docs/framework/wcf/samples/json-serialization.md) sample.</span></span>  
  
### <a name="to-define-the-data-contract-for-a-person"></a><span data-ttu-id="78d7a-110">Bir kişi için veri sözleşmesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="78d7a-110">To define the data contract for a Person</span></span>  
  
1.  <span data-ttu-id="78d7a-111">Veri sözleşmesi tanımlayın `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfına ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri.</span><span class="sxs-lookup"><span data-stu-id="78d7a-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="78d7a-112">Veri sözleşmeleri bkz [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="78d7a-112"> data contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
    ```  
    [DataContract]  
        internal class Person  
        {  
            [DataMember]  
            internal string name;  
  
            [DataMember]  
            internal int age;  
        }  
    ```  
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="78d7a-113">JSON kişiye türünün bir örneği seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="78d7a-113">To serialize an instance of type Person to JSON</span></span>  
  
1.  <span data-ttu-id="78d7a-114">Bir örneğini oluşturmak `Person` türü.</span><span class="sxs-lookup"><span data-stu-id="78d7a-114">Create an instance of the `Person` type.</span></span>  
  
    ```  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  <span data-ttu-id="78d7a-115">Seri hale `Person` kullanarak bir bellek akış nesnesine <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="78d7a-115">Serialize the `Person` object to a memory stream using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  <span data-ttu-id="78d7a-116">Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON veri akışına yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="78d7a-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  <span data-ttu-id="78d7a-117">JSON çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78d7a-117">Show the JSON output.</span></span>  
  
    ```  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="78d7a-118">JSON kişiden türünün bir örneği serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="78d7a-118">To deserialize an instance of type Person from JSON</span></span>  
  
1.  <span data-ttu-id="78d7a-119">JSON olarak kodlanmış veriler yeni bir örneğini seri durumdan `Person` kullanarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="78d7a-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  <span data-ttu-id="78d7a-120">Sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="78d7a-120">Show the results.</span></span>  
  
    ```  
    Console.Write("Deserialized back, got name=");  
    Console.Write(p2.name);  
    Console.Write(", age=");  
    Console.WriteLine(p2.age);  
    ```  
  
## <a name="example"></a><span data-ttu-id="78d7a-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="78d7a-121">Example</span></span>  
  
```  
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
>  <span data-ttu-id="78d7a-122">JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi aynı ada sahip birden çok üyeli veri sözleşmeleri için seri hale getirme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78d7a-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="78d7a-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78d7a-123">See Also</span></span>  
 [<span data-ttu-id="78d7a-124">Bağımsız JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="78d7a-124">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="78d7a-125">JSON ve Diğer Veri Aktarma Biçimleri için Destek</span><span class="sxs-lookup"><span data-stu-id="78d7a-125">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
