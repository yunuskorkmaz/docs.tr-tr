---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 2a2da82d913d43aa9bc3ccfeb9f1f1eda12b0562
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300677"
---
# <a name="object-references"></a><span data-ttu-id="49aad-102">Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="49aad-102">Object References</span></span>
<span data-ttu-id="49aad-103">Bu örnek nesnesinin başvuruları göre sunucu ile istemci arasında nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="49aad-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="49aad-104">Benzetimli örnek kullandığı *sosyal ağlar*.</span><span class="sxs-lookup"><span data-stu-id="49aad-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="49aad-105">Bir sosyal ağ oluşan bir `Person` her arkadaş örneği olduğu arkadaş listesi içeren sınıf `Person` sınıfıyla kendi arkadaş listesi.</span><span class="sxs-lookup"><span data-stu-id="49aad-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="49aad-106">Bu nesne bir grafik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="49aad-106">This creates a graph of objects.</span></span> <span data-ttu-id="49aad-107">Hizmet, bu sosyal ağlarda işlemini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="49aad-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="49aad-108">Bu örnekte, Internet Information Services (IIS) tarafından barındırılan hizmet ve bir konsol uygulaması (.exe) istemcidir.</span><span class="sxs-lookup"><span data-stu-id="49aad-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49aad-109">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="49aad-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="49aad-110">Hizmet</span><span class="sxs-lookup"><span data-stu-id="49aad-110">Service</span></span>  
 <span data-ttu-id="49aad-111">`Person` Sınıfında <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulandı, ile <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alan kümesine `true` gibi bir başvuru türü bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="49aad-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="49aad-112">Tüm özelliklere sahip <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulandı.</span><span class="sxs-lookup"><span data-stu-id="49aad-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="49aad-113">`GetPeopleInNetwork` İşlemi türünde bir parametre alır `Person` ve tüm kişilerin ağdaki; döndürür. diğer bir deyişle, tüm kişiler `friends` listesi, arkadaşınızın arkadaşlarınız ve yinelemeleri olmadan benzeri.</span><span class="sxs-lookup"><span data-stu-id="49aad-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="49aad-114">`GetMutualFriends` İşlemi türünde bir parametre alır `Person` ve ayrıca bu kişinin sahip listesindeki tüm arkadaşlarını döndürür içinde kendi `friends` listesi.</span><span class="sxs-lookup"><span data-stu-id="49aad-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="49aad-115">`GetCommonFriends` İşlemi türü listesini alır `Person`.</span><span class="sxs-lookup"><span data-stu-id="49aad-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="49aad-116">Listeye iki olması beklenir `Person` içindeki nesneleri.</span><span class="sxs-lookup"><span data-stu-id="49aad-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="49aad-117">İşlem listesini döndürür `Person` bulunan nesneleri `friends` hem listelerini `Person` Giriş listesindeki nesneler.</span><span class="sxs-lookup"><span data-stu-id="49aad-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="49aad-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="49aad-118">Client</span></span>  
 <span data-ttu-id="49aad-119">İstemci proxy kullanılarak oluşturulan **hizmet Başvurusu Ekle** Visual Studio özelliği.</span><span class="sxs-lookup"><span data-stu-id="49aad-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="49aad-120">Beş oluşan bir sosyal ağ `Person` nesneleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="49aad-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="49aad-121">İstemci, her üç yöntemi hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="49aad-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="49aad-122">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="49aad-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="49aad-123">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49aad-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="49aad-124">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49aad-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="49aad-125">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49aad-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="49aad-126">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="49aad-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="49aad-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="49aad-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="49aad-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="49aad-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49aad-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="49aad-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="49aad-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49aad-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="49aad-131">Birlikte Çalışabilir Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="49aad-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
