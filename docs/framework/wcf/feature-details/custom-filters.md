---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489761"
---
# <a name="custom-filters"></a><span data-ttu-id="372b8-102">Özel Filtreler</span><span class="sxs-lookup"><span data-stu-id="372b8-102">Custom Filters</span></span>
<span data-ttu-id="372b8-103">Özel Filtreler, sistem tarafından sağlanan ileti filtreleri kullanılarak elde edemiyor eşleşen mantığı tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="372b8-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="372b8-104">Örneğin, belirli ileti öğesi karma hale getirir ve filtre doğru döndürme zorunluluğu olup olmadığını belirlemek için değeri inceler özel filtre veya yanlış oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="372b8-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="372b8-105">Uygulama</span><span class="sxs-lookup"><span data-stu-id="372b8-105">Implementation</span></span>  
 <span data-ttu-id="372b8-106">Özel filtre uygulamasıdır <xref:System.ServiceModel.Dispatcher.MessageFilter> soyut taban sınıfı.</span><span class="sxs-lookup"><span data-stu-id="372b8-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="372b8-107">Özel filtre uygularken Oluşturucusu isteğe bağlı olarak tek bir dize parametresi kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="372b8-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="372b8-108">Bu parametre, herhangi bir değer veya filtre gerçekleştirmek için çalışma zamanında gereken yapılandırma eşleşen sağlamak amacıyla MessageFilter oluşturucuya geçirilen yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="372b8-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="372b8-109">Örneğin, bu iletinin değerlendirilen içinde filtre arar bir değer sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="372b8-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="372b8-110">Aşağıdaki örnek, bir dize parametre kabul eden bir özel ileti filtresi temel uyarlamasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="372b8-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
>  <span data-ttu-id="372b8-111">Gerçek bir uygulama, bu ileti filtresi döndürmelidir belirlemek için ileti inceleyeceksiniz mantığı eşleşme yöntemleri içeren **true** veya **false**.</span><span class="sxs-lookup"><span data-stu-id="372b8-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="372b8-112">Performans</span><span class="sxs-lookup"><span data-stu-id="372b8-112">Performance</span></span>  
 <span data-ttu-id="372b8-113">Özel filtre uygularken, filtre bir ileti değerlendirmesini tamamlamak gereken en fazla süreyi dikkate önemlidir.</span><span class="sxs-lookup"><span data-stu-id="372b8-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="372b8-114">Bir eşleşme önce bir ileti birden çok filtreleriyle hesaplanan, tüm filtreleri değerlendirilmeden önce istemci isteği zaman aşımına yaptığından emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="372b8-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="372b8-115">Bu nedenle bir özel filtre yalnızca içeriği veya filtre ölçütünü eşleşip eşleşmediğini belirlemek için bir ileti özniteliklerini değerlendirmek için gereken kodu içermelidir.</span><span class="sxs-lookup"><span data-stu-id="372b8-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="372b8-116">Genel olarak, aşağıdaki özel filtre uygularken kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="372b8-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
-   <span data-ttu-id="372b8-117">GÇ, verileri diske veya bir veritabanına kaydetme gibi.</span><span class="sxs-lookup"><span data-stu-id="372b8-117">IO, such as saving data to disk or to a database.</span></span>  
  
-   <span data-ttu-id="372b8-118">İşlem, bir belge içinde birden çok kayıt üzerinden döngü gibi gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="372b8-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
-   <span data-ttu-id="372b8-119">Paylaşılan kaynaklar üzerinde bir kilit elde etme veya bir veritabanında aramalar gerçekleştiren çağrıları gibi işlemleri engelliyor.</span><span class="sxs-lookup"><span data-stu-id="372b8-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="372b8-120">Özel filtre bir üretim ortamında kullanmadan önce Filtre bir ileti değerlendirmek için geçen ortalama süreyi belirlemek için performans testlerini çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="372b8-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="372b8-121">Filtre tablosunda kullanılan diğer filtrelerle Ortalama işleme süresi ile birlikte kullanıldığında, bu doğru şekilde istemci uygulaması tarafından belirtilen en büyük zaman aşımı değeri belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="372b8-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="372b8-122">Kullanım</span><span class="sxs-lookup"><span data-stu-id="372b8-122">Usage</span></span>  
 <span data-ttu-id="372b8-123">Özel filtre yönlendirme hizmeti ile kullanabilmeniz için onu filtre tabloya yeni bir filtre giriş türü belirterek "Özel," İleti Filtresi tam olarak nitelenmiş tür adını ve derlemenizi adını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="372b8-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="372b8-124">Diğer bir MessageFilters olduğu gibi ile özel filtrenin oluşturucuya geçirilen dize filterData belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="372b8-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="372b8-125">Aşağıdaki örnekler, yönlendirme hizmeti ile özel bir filtre kullanarak göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="372b8-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
