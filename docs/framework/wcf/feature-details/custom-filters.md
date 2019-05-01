---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857226"
---
# <a name="custom-filters"></a><span data-ttu-id="2a770-102">Özel Filtreler</span><span class="sxs-lookup"><span data-stu-id="2a770-102">Custom Filters</span></span>
<span data-ttu-id="2a770-103">Özel Filtreler sistem tarafından sağlanan ileti filtreleri kullanarak elde edemiyor eşleşen mantığı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a770-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="2a770-104">Örneğin, bir özel ileti öğesi karma hale getirir ve ardından filtrenin doğru döndürme zorunluluğu olup olmadığını belirlemek için değer inceler özel filtre ya da yanlış oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a770-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="2a770-105">Uygulama</span><span class="sxs-lookup"><span data-stu-id="2a770-105">Implementation</span></span>  
 <span data-ttu-id="2a770-106">Özel bir filtre uygulamasıdır <xref:System.ServiceModel.Dispatcher.MessageFilter> soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="2a770-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="2a770-107">Özel filtrenizle uygularken Oluşturucusu isteğe bağlı olarak tek bir dize parametresi kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="2a770-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="2a770-108">Bu parametre, herhangi bir değer veya filtre gerçekleştirmek için çalışma zamanında gereken yapılandırma eşleşen sağlamak amacıyla MessageFilter oluşturucuya geçirilen yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2a770-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="2a770-109">Örneğin, bu filtre değerlendirilen ileti içinde arar bir değer sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a770-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="2a770-110">Aşağıdaki örnek, bir dize parametresi kabul eden bir özel ileti filtresi uygulaması gösterir:</span><span class="sxs-lookup"><span data-stu-id="2a770-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="2a770-111">Gerçek bir uygulamada eşleştirme yöntemleri bu ileti filtresi döndürmelidir belirlemek için ileti inceleyeceği mantığı içeren **true** veya **false**.</span><span class="sxs-lookup"><span data-stu-id="2a770-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="2a770-112">Performans</span><span class="sxs-lookup"><span data-stu-id="2a770-112">Performance</span></span>  
 <span data-ttu-id="2a770-113">Özel filtre uygulanırken, filtre bir ileti değerlendirmesini tamamlamak gereken süre uzunluğu en fazla dikkate önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2a770-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="2a770-114">Önce bir eşleşme bulunduğu bir ileti birden çok filtrelere göre değerlendirilebilir beri tüm filtreleri değerlendirilmeden önce istemci isteğinin zaman aşımına uğramaz sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2a770-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="2a770-115">Bu nedenle özel filtre yalnızca içeriğini veya özniteliklerini filtre ölçütlerini eşleşip eşleşmediğini belirlemek için bir ileti değerlendirmek için gereken kodu içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a770-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="2a770-116">Genel olarak, aşağıdaki özel filtre uygularken kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2a770-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="2a770-117">GÇ, verileri diske veya bir veritabanına kaydetme gibi.</span><span class="sxs-lookup"><span data-stu-id="2a770-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="2a770-118">İşlem, bir belge içinde birden çok kayıt üzerinde döngü gibi gereksiz.</span><span class="sxs-lookup"><span data-stu-id="2a770-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="2a770-119">Paylaşılan kaynaklar üzerinde bir kilit alma veya bir veritabanında aramalar gerçekleştiren çağrıları gibi işlemleri engelliyor.</span><span class="sxs-lookup"><span data-stu-id="2a770-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="2a770-120">Özel filtre bir üretim ortamında kullanmadan önce Filtre bir ileti değerlendirmek için gereken ortalama süreyi belirlemek için performans testleri çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a770-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="2a770-121">Ortalama işlem süresi filtre tablosunda kullanılan bir filtre ile birlikte kullanıldığında, bu istemci uygulaması tarafından belirtilen en uzun zaman aşımı değeri doğru bir şekilde belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2a770-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="2a770-122">Kullanım</span><span class="sxs-lookup"><span data-stu-id="2a770-122">Usage</span></span>  
 <span data-ttu-id="2a770-123">Özel filtrenizle yönlendirme hizmeti ile kullanmak için filtre tabloya yeni bir filtre giriş türü belirterek "Özel," İleti Filtresi tam olarak nitelenmiş tür adını ve derlemenizin adını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a770-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="2a770-124">İle diğer MessageFilters olduğu gibi özel filtrenin oluşturucuya geçirilen dize filterData belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a770-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="2a770-125">Aşağıdaki örnekler yönlendirme hizmeti ile özel bir filtre kullanarak göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2a770-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
