---
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185204"
---
# <a name="custom-filters"></a><span data-ttu-id="3ef53-102">Özel Filtreler</span><span class="sxs-lookup"><span data-stu-id="3ef53-102">Custom Filters</span></span>
<span data-ttu-id="3ef53-103">Özel filtreler, sistem tarafından sağlanan ileti filtreleri kullanılarak gerçekleştirilemeyen eşleşen mantığı tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ef53-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="3ef53-104">Örneğin, belirli bir ileti öğesini eleman olarak eleman olarak eleman olarak eleman olarak eleman olarak eleman olarak döndürecek ve filtrenin doğru mu yoksa yanlış mı döndüreceğini belirlemek için değeri inceleyen özel bir filtre oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ef53-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="3ef53-105">Uygulama</span><span class="sxs-lookup"><span data-stu-id="3ef53-105">Implementation</span></span>  
 <span data-ttu-id="3ef53-106">Özel bir filtre soyut <xref:System.ServiceModel.Dispatcher.MessageFilter> taban sınıfının bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3ef53-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="3ef53-107">Özel filtrenizi uygularken, oluşturucu isteğe bağlı olarak tek bir dize parametresini kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="3ef53-108">Bu parametre, filtrenin eşleşmeleri gerçekleştirmek için çalışma zamanında ihtiyaç duyduğu değerleri veya yapılandırmayı sağlamak için MessageFilter oluşturucusuna aktarılan yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="3ef53-109">Örneğin, bu, filtrenin değerlendirilmekte olan ileti içinde aradığı bir değeri sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="3ef53-110">Aşağıdaki örnek, dize parametresi kabul eden özel bir ileti filtresinin temel uygulamasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3ef53-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
> <span data-ttu-id="3ef53-111">Gerçek bir uygulamada, Eşleme yöntemi(ler) bu ileti filtresinin **doğru** mu yoksa **yanlış**mı döndüreceğini belirlemek için iletiyi inceleyecek mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="3ef53-112">Performans</span><span class="sxs-lookup"><span data-stu-id="3ef53-112">Performance</span></span>  
 <span data-ttu-id="3ef53-113">Özel bir filtre uygularken, filtrenin iletinin değerlendirmesini tamamlaması için gereken maksimum süreyi göz önünde bulundurmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="3ef53-114">Bir ileti eşleşme bulunmadan önce birden çok filtreye karşı değerlendirilebileceğinden, tüm filtreler değerlendirilmeden önce istemci isteğinin zaman ödemediğinden emin olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="3ef53-115">Bu nedenle, özel bir filtre, filtre ölçütlerine uygun olup olmadığını belirlemek için iletinin içeriğini veya özniteliklerini değerlendirmek için yalnızca gerekli kodu içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="3ef53-116">Genel olarak, özel bir filtre uygularken aşağıdakilerden kaçınmalısınız:</span><span class="sxs-lookup"><span data-stu-id="3ef53-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="3ef53-117">IO, diske veya veritabanına veri kaydetme gibi.</span><span class="sxs-lookup"><span data-stu-id="3ef53-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="3ef53-118">Bir belgedeki birden çok kaydın üzerinden döngü gibi gereksiz işleme.</span><span class="sxs-lookup"><span data-stu-id="3ef53-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="3ef53-119">Paylaşılan kaynaklarda kilit alma veya veritabanına karşı arama lar gerçekleştirme gibi işlemleri engelleme.</span><span class="sxs-lookup"><span data-stu-id="3ef53-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="3ef53-120">Üretim ortamında özel bir filtre kullanmadan önce, filtrenin bir iletiyi değerlendirmek için gereken ortalama süreyi belirlemek için performans testleri çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="3ef53-121">Filtre tablosunda kullanılan diğer filtrelerin ortalama işlem süresiyle birleştirildiğinde, bu, istemci uygulaması tarafından belirtilmesi gereken maksimum zaman aşım değerini doğru bir şekilde belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ef53-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3ef53-122">Kullanım</span><span class="sxs-lookup"><span data-stu-id="3ef53-122">Usage</span></span>  
 <span data-ttu-id="3ef53-123">Yönlendirme Hizmeti ile özel filtrenizi kullanmak için, "Özel" türünde yeni bir filtre girişi, ileti filtresinin tam nitelikli tür adı ve derlemenizin adını belirterek filtre tablosuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ef53-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="3ef53-124">Diğer MessageFilters'larda olduğu gibi, özel filtrenizin oluşturucusuna aktaredilecek dize filtresiVerileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ef53-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="3ef53-125">Aşağıdaki örnekler, Yönlendirme Hizmeti ile özel bir filtre kullanarak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3ef53-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
