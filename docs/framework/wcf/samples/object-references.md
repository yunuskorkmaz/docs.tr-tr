---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183455"
---
# <a name="object-references"></a>Nesne Başvuruları
Bu örnek, sunucu ve istemci arasında başvurular tarafından nesnelerin nasıl geçirilmesini gösterir. Örnek simüle *sosyal ağlar*kullanır. Bir sosyal ağ, `Person` her arkadaşınızın kendi arkadaş listesiyle `Person` sınıfın bir örneği olduğu bir arkadaş listesi içeren bir sınıftan oluşur. Bu nesnelerin bir grafik oluşturur. Hizmet, bu sosyal ağlardaki işlemleri ortaya çıkarır.  
  
 Bu örnekte, hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulamasıdır (.exe).  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Sınıf, `Person` <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alan bir başvuru türü olarak `true` bildirmek için ayarlanmış olan öznitelik uygulanır. Tüm özellikler <xref:System.Runtime.Serialization.DataMemberAttribute> uygulanan öznitelik vardır.  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 İşlem `GetPeopleInNetwork` bir tür `Person` parametresi alır ve ağdaki tüm kişileri döndürür; yani, listedeki `friends` tüm insanlar, arkadaşının arkadaşları, ve saire, kopyaları olmadan.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 İşlem, `GetMutualFriends` bir tür `Person` parametresi alır ve listedeki bu kişiyi `friends` de listesinde bulunan tüm arkadaşları döndürür.  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 İşlem `GetCommonFriends` türü `Person`bir liste alır. Listede iki `Person` nesne olması bekleniyor. İşlem, giriş listesindeki her iki `Person` `friends` `Person` nesnenin listesinde yer alan nesnelerin listesini döndürür.  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>İstemci  
 İstemci proxy Visual Studio **Hizmet Başvurusu Ekle** özelliği kullanılarak oluşturulur.  
  
 Beş `Person` nesneden oluşan bir sosyal ağ oluşturulur. İstemci, hizmetteki üç yöntemin her birini çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Birlikte Çalışabilir Nesne Başvuruları](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
