---
title: 'Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 7edce66a23021fa03a6f98b3b847a5b671c17124
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972997"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Nasıl yapılır: JSON verileri seri hale getrime ve
JSON (JavaScript nesne gösterimi), küçük miktarda bir AJAX içerebilen Web Hizmetleri ile istemci tarayıcıları arasında verileri hızlı değişimleri sağlar verimli veri kodlama biçimi değil.  
  
 Bu makale, JSON olarak kodlanmış veri .NET türü nesneleri serileştirmek ve ardından geri .NET türleri örneğine verileri JSON biçiminde seri durumdan gösterilmektedir. Bu örnek bir veri sözleşme serileştirme ve seri durumundan çıkarma, kullanıcı tanımlı göstermek için kullanır. `Person` türüne ve kullandığı <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
 AJAX etkinleştirilmiş uç noktalar sunulan hizmet işlemlerinde veri anlaşması türlerini kullandığınızda normalde, JSON seri hale getirme ve seri durumundan çıkarma otomatik olarak Windows Communication Foundation (WCF) tarafından işlenir. Ancak, bazı durumlarda JSON verileri ile doğrudan çalışmanız gerekebilir.   
  
> [!NOTE]
>  Sunucuda veya başka bir nedenle bir giden yanıt serileştirilmesi sırasında bir hata meydana gelirse, bu istemciye bir hata döndürülmez.  
  
 Bu makalede dayanır [JSON serileştirme](../samples/json-serialization.md) örnek.  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Bir kişi türü için veri anlaşması tanımlamak için 
  
1. Veri sözleşme tanımlamasına `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri. Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>JSON kişiye türün bir örneğini serileştirmek için  
  
1. Bir örneğini oluşturmak `Person` türü.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. Seri hale getirme `Person` kullanarak bellek akışı nesnesine <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON verilerini akışa yazmak için yöntemi.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. JSON çıktısını gösterir.  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON kişiden türünün bir örneği seri durumdan çıkarılacak  
  
1. JSON olarak kodlanmış veriler yeni bir örneğini seri durumdan `Person` kullanarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. Sonuçları gösterir.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Örnek  
  
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
>  JSON serileştirici, aşağıdaki örnek kodda gösterildiği gibi birden çok üye ile aynı ada sahip veri anlaşmaları için bir seri hale getirme özel durumu oluşturur.  
  
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

- [Bağımsız JSON seri hale getirme](stand-alone-json-serialization.md)
- [Biçimleri JSON desteği ve diğer veri aktarma](support-for-json-and-other-data-transfer-formats.md)
