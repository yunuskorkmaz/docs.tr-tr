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
# <a name="how-to-serialize-and-deserialize-json-data"></a>Nasıl yapılır: JSON verilerini serileştirme ve serisini kaldırma
JSON (JavaScript Nesne Gösterimi), istemci tarayıcıları ve AJAX özellikli Web Hizmetleri arasında küçük miktarlarda verilerin hızlı bir şekilde değiş tokuşlanmasını sağlayan etkili bir veri kodlama biçimidir.  
  
 Bu makalede, .NET tür nesnelerinin JSON kodlu verilere nasıl serileştirildiğini ve sonra JSON biçimindeki verilerin serisini .NET türlerinin örneklerine nasıl seri hale getirilebileceğini gösterir. Bu örnek, Kullanıcı tanımlı `Person` bir türün serileştirilmesi ve serisini göstermek için bir veri sözleşmesi kullanır ve kullanır. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
 Genellikle, JSON serileştirme ve seri durumundan çıkarma, AJAX etkin uç noktalar üzerinde kullanıma sunulan hizmet işlemlerinde veri sözleşme türlerini kullandığınızda otomatik olarak Windows Communication Foundation (WCF) tarafından işlenir. Ancak, bazı durumlarda JSON verileriyle doğrudan çalışmanız gerekebilir.   
  
> [!NOTE]
> Sunucuda giden bir yanıtın serileştirilmesi sırasında veya başka bir nedenle hata oluşursa istemciye hata olarak döndürülmeyebilir.  
  
 Bu makale, [JSON serileştirme](../samples/json-serialization.md) örneğine dayalıdır.  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Bir kişi türü için veri sözleşmesini tanımlamak için 
  
1. İçin `Person` veri sözleşmesini, <xref:System.Runtime.Serialization.DataContractAttribute> seri hale getirmek istediğiniz üyelere sınıfına ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine ekleyerek tanımlayın. Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Kişi türündeki bir örneği JSON 'a seri hale getirmek için  
  
1. `Person` Türün bir örneğini oluşturun.  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. Kullanarak nesnesini bir bellek akışına serileştirme. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> `Person`  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. JSON verilerini akışa yazmak için yönteminikullanın.<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. JSON çıkışını göster.  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON 'dan kişi türündeki bir örnek serisini kaldırmak için  
  
1. JSON kodlu verileri ' ın `Person` <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metodunu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanarak yeni bir örneğine serisini kaldırma.  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. Sonuçları göster.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Örnek  
  
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
> JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi, aynı ada sahip birden çok üyesi olan veri sözleşmeleri için bir serileştirme özel durumu oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek başına JSON serileştirmesi](stand-alone-json-serialization.md)
- [JSON ve diğer veri aktarımı biçimleri için destek](support-for-json-and-other-data-transfer-formats.md)
