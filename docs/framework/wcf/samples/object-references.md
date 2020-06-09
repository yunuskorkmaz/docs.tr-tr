---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: ba4ee3fd0cc16130f66570891ecc295b2d2c50aa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599990"
---
# <a name="object-references"></a>Nesne Başvuruları
Bu örnek, nesneleri sunucu ve istemci arasında başvuruya göre nasıl geçileceğini gösterir. Örnek, sanal *sosyal ağları*kullanır. Sosyal ağ `Person` , her arkadaşın `Person` kendi arkadaş listesi ile sınıfın bir örneği olduğu arkadaş listesini içeren bir sınıftan oluşur. Bu, nesnelerin bir grafiğini oluşturur. Hizmet, bu sosyal ağlarda işlemleri kullanıma sunar.  
  
 Bu örnekte, hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulaması (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="service"></a>Hizmet  
 `Person`Sınıfı, <xref:System.Runtime.Serialization.DataContractAttribute> öğesini <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `true` bir başvuru türü olarak bildirmek üzere ayarlanmış olan özniteliği ile birlikte uygulandı. Tüm Özellikler <xref:System.Runtime.Serialization.DataMemberAttribute> uygulanmış özniteliği vardır.  
  
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
  
 `GetPeopleInNetwork`İşlem, türünde bir parametre alır `Person` ve ağdaki tüm kişileri döndürür; diğer bir deyişle, listedeki tüm kişiler `friends` , arkadaşınızın arkadaşları, vb., yinelemeler olmadan.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends`İşlem türünde bir parametre alır ve listede `Person` Bu kişinin da bulunduğu tüm arkadaşlarınızı döndürür `friends` .  
  
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
  
 `GetCommonFriends`İşlem, türün bir listesini alır `Person` . Listede iki nesne olması beklenir `Person` . İşlem, `Person` `friends` giriş listesindeki her iki nesnenin listelerinde bulunan nesnelerin listesini döndürür `Person` .  
  
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
 İstemci proxy 'si, Visual Studio 'nun **hizmet başvurusu Ekle** özelliği kullanılarak oluşturulur.  
  
 Beş nesneden oluşan bir sosyal ağ `Person` oluşturulur. İstemci, hizmette üç yöntemin her birini çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Birlikte Çalışabilir Nesne Başvuruları](../feature-details/interoperable-object-references.md)
