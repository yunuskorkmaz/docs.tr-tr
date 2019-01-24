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
# <a name="how-to-serialize-and-deserialize-json-data"></a>Nasıl yapılır: JSON verileri seri hale getrime ve
JSON (JavaScript nesne gösterimi), küçük miktarda bir AJAX içerebilen Web Hizmetleri ile istemci tarayıcıları arasında verileri hızlı değişimleri sağlar verimli veri kodlama biçimi değil.  
  
 Bu konuda, .NET türü nesneleri JSON olarak kodlanmış verileri seri hale getirmek ve geri kullanarak .NET türleri örneğine verileri JSON biçiminde seri durumdan çıkarmak gösterilmiştir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Bu örnek bir veri sözleşme serileştirme ve seri durumundan çıkarma, kullanıcı tanımlı göstermek için kullanır. `Person` türü.  
  
 Normalde, JSON seri hale getirme ve seri durumundan çıkarma otomatik işlenir Windows Communication Foundation (WCF) tarafından AJAX etkinleştirilmiş uç noktalar sunulan hizmet işlemlerinde veri anlaşması türlerini kullandığınızda. Ancak, doğrudan - JSON verileri ile çalışmak gerekebilir. Bazı durumlarda bu konunun gösteren senaryodur.  
  
> [!NOTE]
>  Sunucu üzerindeki bir giden yanıt serileştirilmesi sırasında bir hata oluşur veya yanıt işlemi başka bir nedenle bir özel durum oluşturur, bu istemciye bir hata döndürülmez.  
  
 Bu konuda dayanır [JSON serileştirme](../../../../docs/framework/wcf/samples/json-serialization.md) örnek.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Bir kişi için veri anlaşması tanımlamak için  
  
1.  Veri sözleşme tanımlamasına `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri. Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>JSON kişiye türün bir örneğini serileştirmek için  
  
1.  Bir örneğini oluşturmak `Person` türü.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Seri hale getirme `Person` nesnesi kullanarak bir bellek akış <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON verilerini akışa yazmak için yöntemi.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  JSON çıktısını gösterir.  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON kişiden türünün bir örneği seri durumdan çıkarılacak  
  
1.  JSON olarak kodlanmış veriler yeni bir örneğini seri durumdan `Person` kullanarak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  Sonuçları gösterir.  
  
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
- [Bağımsız JSON Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [JSON ve Diğer Veri Aktarma Biçimleri için Destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
