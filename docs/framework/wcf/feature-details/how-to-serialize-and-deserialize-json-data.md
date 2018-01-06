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
ms.openlocfilehash: 994ccb677d1376eff5b889a0a4ddfe072557bdea
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Nasıl yapılır: JSON Verilerini Seri Hale Getrime ve Seri Halden Çıkarma
JSON (JavaScript nesne gösterimi) küçük miktarda veri istemci tarayıcıları ve AJAX etkinleştirilmiş Web hizmetleri arasında hızlı alışverişleri sağlayan bir verimli veri kodlama biçimidir.  
  
 Bu konuda JSON olarak kodlanmış veri .NET türü nesneleri seri hale getirmek ve geri kullanarak .NET türleri örneğine verileri JSON biçiminde seri durumdan nasıl oluşturulduğunu gösteren <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Bu örnek bir veri sözleşmesi seri hale getirme ve seri durumdan çıkarma işlemi kullanıcı tarafından tanımlanan göstermek için kullanır. `Person` türü.  
  
 Normalde, JSON seri hale getirme ve seri durumdan çıkarma gerçekleştirilir tarafından otomatik olarak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] AJAX etkinleştirilmiş Uç noktalara sunulan hizmet işlemleri veri sözleşme türleri kullandığınızda. Ancak, JSON verileriyle doğrudan - çözüm bulmanız gerekebilecek bazı durumlarda bu, bu konuda gösteren senaryodur.  
  
> [!NOTE]
>  Sunucu üzerinde giden bir cevap serileştirme sırasında bir hata oluşursa veya yanıt işlemi başka bir nedenle bir özel durum oluşturur, istemciye bir hata döndürdüğü değil.  
  
 Bu konuda dayanır [JSON serileştirmesi](../../../../docs/framework/wcf/samples/json-serialization.md) örnek.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Bir kişi için veri sözleşmesi tanımlamak için  
  
1.  Veri sözleşmesi tanımlayın `Person` ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> sınıfına ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği seri hale getirmek istediğiniz üyeleri. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Veri sözleşmeleri bkz [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>JSON kişiye türünün bir örneği seri hale getirmek için  
  
1.  Bir örneğini oluşturmak `Person` türü.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Seri hale `Person` kullanarak bir bellek akış nesnesine <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Kullanım <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> JSON veri akışına yazmak için yöntem.  
  
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
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON kişiden türünün bir örneği serisini kaldırmak için  
  
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
>  JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi aynı ada sahip birden çok üyeli veri sözleşmeleri için seri hale getirme özel durumu oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımsız JSON Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [JSON ve Diğer Veri Aktarma Biçimleri için Destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
