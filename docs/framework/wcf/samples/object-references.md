---
description: 'Daha fazla bilgi edinin: nesne başvuruları'
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: ae76cf13b4ccbbde2ad6d5022248bbcfeb263879
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732416"
---
# <a name="object-references"></a><span data-ttu-id="2da24-103">Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="2da24-103">Object References</span></span>

<span data-ttu-id="2da24-104">Bu örnek, nesneleri sunucu ve istemci arasında başvuruya göre nasıl geçileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2da24-104">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="2da24-105">Örnek, sanal *sosyal ağları* kullanır.</span><span class="sxs-lookup"><span data-stu-id="2da24-105">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="2da24-106">Sosyal ağ `Person` , her arkadaşın `Person` kendi arkadaş listesi ile sınıfın bir örneği olduğu arkadaş listesini içeren bir sınıftan oluşur.</span><span class="sxs-lookup"><span data-stu-id="2da24-106">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="2da24-107">Bu, nesnelerin bir grafiğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2da24-107">This creates a graph of objects.</span></span> <span data-ttu-id="2da24-108">Hizmet, bu sosyal ağlarda işlemleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="2da24-108">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="2da24-109">Bu örnekte, hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="2da24-109">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2da24-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="2da24-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="2da24-111">Hizmet</span><span class="sxs-lookup"><span data-stu-id="2da24-111">Service</span></span>  

 <span data-ttu-id="2da24-112">`Person`Sınıfı, <xref:System.Runtime.Serialization.DataContractAttribute> öğesini <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `true` bir başvuru türü olarak bildirmek üzere ayarlanmış olan özniteliği ile birlikte uygulandı.</span><span class="sxs-lookup"><span data-stu-id="2da24-112">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="2da24-113">Tüm Özellikler <xref:System.Runtime.Serialization.DataMemberAttribute> uygulanmış özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="2da24-113">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="2da24-114">`GetPeopleInNetwork`İşlem, türünde bir parametre alır `Person` ve ağdaki tüm kişileri döndürür; diğer bir deyişle, listedeki tüm kişiler `friends` , arkadaşınızın arkadaşları, vb., yinelemeler olmadan.</span><span class="sxs-lookup"><span data-stu-id="2da24-114">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="2da24-115">`GetMutualFriends`İşlem türünde bir parametre alır ve listede `Person` Bu kişinin da bulunduğu tüm arkadaşlarınızı döndürür `friends` .</span><span class="sxs-lookup"><span data-stu-id="2da24-115">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="2da24-116">`GetCommonFriends`İşlem, türün bir listesini alır `Person` .</span><span class="sxs-lookup"><span data-stu-id="2da24-116">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="2da24-117">Listede iki nesne olması beklenir `Person` .</span><span class="sxs-lookup"><span data-stu-id="2da24-117">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="2da24-118">İşlem, `Person` `friends` giriş listesindeki her iki nesnenin listelerinde bulunan nesnelerin listesini döndürür `Person` .</span><span class="sxs-lookup"><span data-stu-id="2da24-118">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="2da24-119">İstemci</span><span class="sxs-lookup"><span data-stu-id="2da24-119">Client</span></span>  

 <span data-ttu-id="2da24-120">İstemci proxy 'si, Visual Studio 'nun **hizmet başvurusu Ekle** özelliği kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2da24-120">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="2da24-121">Beş nesneden oluşan bir sosyal ağ `Person` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2da24-121">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="2da24-122">İstemci, hizmette üç yöntemin her birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2da24-122">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2da24-123">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2da24-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2da24-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2da24-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2da24-125">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2da24-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2da24-126">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2da24-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2da24-127">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2da24-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2da24-128">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2da24-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2da24-129">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2da24-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2da24-130">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2da24-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="2da24-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2da24-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="2da24-132">Birlikte Çalışabilir Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="2da24-132">Interoperable Object References</span></span>](../feature-details/interoperable-object-references.md)
