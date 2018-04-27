---
title: Nesne Başvuruları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fcb34efeb7eed28f85774dc5489b3e56aeac4e6c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="object-references"></a>Nesne Başvuruları
Bu örnek, sunucu ve istemci arasında başvurular nesneleri geçirmek gösterilmiştir. Örnek kullandığı benzetimli *sosyal ağlar*. Sosyal ağ oluşan bir `Person` her arkadaş örneği olan arkadaş listesi içeren sınıf `Person` sınıfıyla arkadaş kendi listesi. Bu nesne bir grafik oluşturur. Hizmet bu sosyal ağlarda işlemini kullanıma sunar.  
  
 Bu örnekte, Internet Information Services (IIS) tarafından barındırılan hizmetindeki ve istemcinin bir konsol uygulaması (.exe).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 `Person` Sınıfına sahip <xref:System.Runtime.Serialization.DataContractAttribute> uygulanan özniteliği ile <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alan kümesi'ne `true` gibi bir başvuru türü bildirmek için. Tüm özelliklere sahip <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulanmıştır.  
  
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
  
 `GetPeopleInNetwork` İşlemi türünde bir parametre alır `Person` ve tüm kişilerin ağda; döndürür diğer bir deyişle, tüm kişiler `friends` listesi, arkadaşınızın arkadaşlarınız ve yinelemeleri olmadan belirli bir benzeri.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` İşlemi türünde bir parametre alır `Person` ve ayrıca bu kişinin sahip listesindeki tüm arkadaş verir, bunların `friends` listesi.  
  
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
  
 `GetCommonFriends` İşlemi türü listesini alır `Person`. Liste iki olması beklenir `Person` içindeki nesneleri. İşlemi bir listesini döndürür `Person` nesnelerine `friends` listeleri hem `Person` giriş listesi nesneleri.  
  
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
 İstemci proxy kullanılarak oluşturulan **hizmet Başvurusu Ekle** Visual Studio özelliğidir.  
  
 Beş oluşan bir sosyal ağda `Person` nesneleri oluşturulur. İstemci hizmeti her üç yöntemi çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Birlikte Çalışabilir Nesne Başvuruları](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
