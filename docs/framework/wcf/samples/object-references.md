---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 1aa8b1c9d135186dba9e4da75f0c7cb9297d8e5c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462291"
---
# <a name="object-references"></a>Nesne Başvuruları
Bu örnek nesnesinin başvuruları göre sunucu ile istemci arasında nasıl geçirileceğini gösterir. Benzetimli örnek kullandığı *sosyal ağlar*. Bir sosyal ağ oluşan bir `Person` her arkadaş örneği olduğu arkadaş listesi içeren sınıf `Person` sınıfıyla kendi arkadaş listesi. Bu nesne bir grafik oluşturur. Hizmet, bu sosyal ağlarda işlemini kullanıma sunar.  
  
 Bu örnekte, Internet Information Services (IIS) tarafından barındırılan hizmet ve bir konsol uygulaması (.exe) istemcidir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 `Person` Sınıfında <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulandı, ile <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alan kümesine `true` gibi bir başvuru türü bildirmek için. Tüm özelliklere sahip <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulandı.  
  
```  
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
  
 `GetPeopleInNetwork` İşlemi türünde bir parametre alır `Person` ve tüm kişilerin ağdaki; döndürür. diğer bir deyişle, tüm kişiler `friends` listesi, arkadaşınızın arkadaşlarınız ve yinelemeleri olmadan benzeri.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` İşlemi türünde bir parametre alır `Person` ve ayrıca bu kişinin sahip listesindeki tüm arkadaşlarını döndürür içinde kendi `friends` listesi.  
  
```  
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
  
 `GetCommonFriends` İşlemi türü listesini alır `Person`. Listeye iki olması beklenir `Person` içindeki nesneleri. İşlem listesini döndürür `Person` bulunan nesneleri `friends` hem listelerini `Person` Giriş listesindeki nesneler.  
  
```  
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
 İstemci proxy kullanılarak oluşturulan **hizmet Başvurusu Ekle** Visual Studio özelliği.  
  
 Beş oluşan bir sosyal ağ `Person` nesneleri oluşturulur. İstemci, her üç yöntemi hizmeti çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Birlikte Çalışabilir Nesne Başvuruları](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
