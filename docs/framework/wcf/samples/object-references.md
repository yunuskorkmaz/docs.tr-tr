---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: bc9c318fc0e05f384a00df7cd1436a138315d880
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714675"
---
# <a name="object-references"></a><span data-ttu-id="e1983-102">Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="e1983-102">Object References</span></span>
<span data-ttu-id="e1983-103">Bu örnek, nesneleri sunucu ve istemci arasında başvuruya göre nasıl geçileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1983-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="e1983-104">Örnek, sanal *sosyal ağları*kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1983-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="e1983-105">Sosyal ağ, her arkadaşın kendi arkadaş listesi ile `Person` sınıfının bir örneği olduğu arkadaş listesini içeren `Person` sınıfından oluşur.</span><span class="sxs-lookup"><span data-stu-id="e1983-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="e1983-106">Bu, nesnelerin bir grafiğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1983-106">This creates a graph of objects.</span></span> <span data-ttu-id="e1983-107">Hizmet, bu sosyal ağlarda işlemleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="e1983-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="e1983-108">Bu örnekte, hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="e1983-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1983-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e1983-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e1983-110">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e1983-110">Service</span></span>  
 <span data-ttu-id="e1983-111">`Person` sınıfında, <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alanı bir başvuru türü olarak bildirmek için `true` olarak ayarlanmış <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e1983-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="e1983-112">Tüm özelliklerde <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="e1983-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="e1983-113">`GetPeopleInNetwork` işlemi, `Person` türünde bir parametre alır ve ağdaki tüm kişileri döndürür; diğer bir deyişle, `friends` listesindeki tüm kişiler, arkadaşınızın arkadaşları, vb., yinelemeler olmadan.</span><span class="sxs-lookup"><span data-stu-id="e1983-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="e1983-114">`GetMutualFriends` işlem, `Person` türünde bir parametre alır ve bu kişinin `friends` listesinde de bulunan tüm arkadaşlarınızı geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1983-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="e1983-115">`GetCommonFriends` işlem `Person`türünün bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="e1983-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="e1983-116">Listenin içinde iki `Person` nesne olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="e1983-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="e1983-117">İşlem, giriş listesindeki `Person` nesnelerinin `friends` listelerinde bulunan `Person` nesnelerinin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1983-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="e1983-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="e1983-118">Client</span></span>  
 <span data-ttu-id="e1983-119">İstemci proxy 'si, Visual Studio 'nun **hizmet başvurusu Ekle** özelliği kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e1983-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="e1983-120">Beş `Person` nesnesinden oluşan bir sosyal ağ oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e1983-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="e1983-121">İstemci, hizmette üç yöntemin her birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e1983-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1983-122">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e1983-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e1983-123">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e1983-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e1983-124">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e1983-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e1983-125">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e1983-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1983-126">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1983-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1983-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e1983-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e1983-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e1983-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1983-129">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e1983-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="e1983-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1983-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="e1983-131">Birlikte Çalışabilir Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="e1983-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
