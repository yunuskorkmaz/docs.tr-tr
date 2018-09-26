---
title: Filtre Seçme
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 377d4f5c221ad37acf954b1dafc8712a388122ff
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108812"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="96cd0-102">Filtre Seçme</span><span class="sxs-lookup"><span data-stu-id="96cd0-102">Choosing a Filter</span></span>
<span data-ttu-id="96cd0-103">Yönlendirme hizmeti yapılandırırken, doğru ileti filtreleri seçin ve bunları tam eşleşme aldığınız mesajlarına karşı yapmanıza izin verecek şekilde yapılandırmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="96cd0-104">Seçtiğiniz filtreler kendi eşleşmelerin aşırı geniş kapsamlı veya yanlış yapılandırılırsa, iletiler yanlış yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="96cd0-105">Filtreleri çok fazla kısıtlayıcıysa, kullanılabilir tüm geçerli rotalar iletilerinizi bazıları için sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="96cd0-106">Filtre türleri</span><span class="sxs-lookup"><span data-stu-id="96cd0-106">Filter Types</span></span>  
 <span data-ttu-id="96cd0-107">Yönlendirme hizmeti tarafından kullanılan filtreler seçerken, hangi bilgilerin kullanılabilir yanı sıra her bir filtrenin nasıl çalıştığını anlamanız önemli gelen iletiler bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="96cd0-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="96cd0-108">Tüm iletiler aynı uç noktası üzerinden alınırsa, tüm iletileri bu filtrelerle eşleşen örneği için adres ve Uçnoktaadı filtreleri kullanışlı değildir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="96cd0-109">Eylem</span><span class="sxs-lookup"><span data-stu-id="96cd0-109">Action</span></span>  
 <span data-ttu-id="96cd0-110">Eylem filtresi inceler <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="96cd0-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="96cd0-111">İleti eylem başlığında içeriğini filtre yapılandırmasında belirtilen filtre veri değeri eşleşen ardından bu filtre döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="96cd0-112">Aşağıdaki örnekte tanımlayan bir `FilterElement` iletileri değerini içeren bir eylem üst bilgisi ile eşleşecek şekilde eylem filtresi kullanan `http://namespace/contract/operation/`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="96cd0-113">Bu filtre, benzersiz bir eylem üst bilgisi içeren iletileri yönlendirme kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="96cd0-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="96cd0-114">EndpointAddress</span></span>  
 <span data-ttu-id="96cd0-115">EndpointAddress filtre iletisi alındı EndpointAddress inceler.</span><span class="sxs-lookup"><span data-stu-id="96cd0-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="96cd0-116">İleti tam olarak ulaştığında adres filtresi yapılandırmasında belirtilen filtre adresi eşleşen ardından bu filtre döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="96cd0-117">Aşağıdaki örnekte tanımlayan bir `FilterElement` gönderilen iletileri eşleşmesi için adres filtresi kullanan "http://\<ana bilgisayar adı > / vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="96cd0-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="96cd0-118">Bir adresi konak adı kısmı istemci tam etki alanı adı, NetBIOS adı, IP adresi veya diğer adı kullanıp kullanmadığını göre değişebilir dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="96cd0-119">Farklı değerleri de aynı konağa başvurabilir olduğundan, bu karşılaştırma için varsayılan davranış adresi konak adı kısmı eşleşme gerçekleştirirken değil kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="96cd0-120">Bu davranışı, ana bilgisayar adı, yönlendirme hizmeti programlı bir şekilde yapılandırırken değerlendirmek karşılaştırma izin verecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="96cd0-121">Bu filtre benzersiz bir adrese gönderilen gelen iletiler kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="96cd0-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="96cd0-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="96cd0-123">EndpointAddressPrefix filtre EndpointAddress filtreye benzerdir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="96cd0-124">EndpointAddressPrefix filtre iletisi alındı EndpointAddress inceler.</span><span class="sxs-lookup"><span data-stu-id="96cd0-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="96cd0-125">Ancak EndpointAddressPrefix filtre, filtre yapılandırmasında belirtilen değerle başlayan adresler eşleşen bir joker karakter olarak görür.</span><span class="sxs-lookup"><span data-stu-id="96cd0-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="96cd0-126">Aşağıdaki örnekte tanımlayan bir `FilterElement` gönderilen iletileri eşleştirilecek EndpointAddressPrefix filtresi kullanan `http://<hostname>/vdir*`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="96cd0-127">Bir adresi konak adı kısmı istemci tam etki alanı adı, NetBIOS adı, IP adresi veya diğer adı kullanıp kullanmadığını göre değişebilir dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="96cd0-128">Farklı değerleri de aynı konağa başvurabilir olduğundan, bu karşılaştırma için varsayılan davranış adresi konak adı kısmı eşleşme gerçekleştirirken değil kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="96cd0-129">Bu filtre, ortak bir adres öneki paylaşan gelen iletileri yönlendirme kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="96cd0-130">AND</span><span class="sxs-lookup"><span data-stu-id="96cd0-130">AND</span></span>  
 <span data-ttu-id="96cd0-131">VE filtre doğrudan bir ileti içindeki bir değerin üzerinde filtre, ancak oluşturmak için iki filtre birleştirmenizi sağlar bir `AND` burada her iki filtreleri eşleşmelidir ileti ve filtresinin önce koşul `true`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="96cd0-132">Bu, tüm alt filtrelerle eşleşen, yalnızca eşleşen karmaşık filtreler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="96cd0-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="96cd0-133">Aşağıdaki örnek, bir adres filtresi ve bir eylem filtresi tanımlar ve sonra bir ileti adresi ve eylem filtreleriyle değerlendiren bir ve filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="96cd0-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="96cd0-134">VE filtre verir hem adresi hem de eylem filtreleri, eşleşiyorsa `true`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
```xml  
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>  
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);  
```  
  
 <span data-ttu-id="96cd0-135">Bir eşleşme olduğunda yapılması gerektiğini belirlemek için birden çok filtre mantığından birleştirdiğinizde gerekir, bu filtre kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="96cd0-136">Örneğin, yalnızca belirli birleşimleri Eylemler ve iletileri belirli adresleri için almaları gerekir birden çok hedefe sahip, gerekli eylem ve adresi filtrelerini birleştirmeye ve filtre kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96cd0-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="96cd0-137">Özel</span><span class="sxs-lookup"><span data-stu-id="96cd0-137">Custom</span></span>  
 <span data-ttu-id="96cd0-138">Özel filtre türü seçerken içeren bütünleştirilmiş kodun türünü içeren customType değeri sağlamalısınız **MessageFilter** Bu filtre için kullanılacak uygulama.</span><span class="sxs-lookup"><span data-stu-id="96cd0-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="96cd0-139">Ayrıca, filtre veri iletileri kendi değerlendirmesinde özel filtre gerektirebilecek herhangi bir değeri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="96cd0-140">Aşağıdaki örnekte tanımlayan bir `FilterElement` kullanan `CustomAssembly.MyCustomMsgFilter` MessageFilter uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96cd0-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="96cd0-141">İle sağlanan filtreler tarafından kapsanmayan bir ileti karşı özel eşleşen mantıksal gerçekleştirmek gereken [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], özel bir filtre uygulamasıdır oluşturmalısınız **MessageFilter** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="96cd0-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="96cd0-142">Örneğin, bir alana filtre yapılandırması için verilen bilinen değer listesiyle gelen ileti karşılaştırır veya belirli ileti öğesi karma hale getirir ve sonra bu değeri belirlemek için inceler özel filtre oluşturabilirsiniz olmadığını filtresi döndürmelidir `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="96cd0-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="96cd0-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="96cd0-143">EndpointName</span></span>  
 <span data-ttu-id="96cd0-144">Uçnoktaadı filtre ileti alındı. uç nokta adı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="96cd0-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="96cd0-145">Aşağıdaki örnekte tanımlayan bir `FilterElement` Uçnoktaadı filtre "SvcEndpoint" alınan iletileri yönlendirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="96cd0-146">Bu filtre, birden fazla adlandırılmış hizmet uç noktası yönlendirme hizmeti sunan yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="96cd0-147">Örneğin, yönlendirme hizmeti, iletileri almak için kullanır. iki uç noktalarını kullanıma; gerçek zamanlı başka bir uç noktası hata iletilerinin işlenmesini duyarlı saat değil iletileri alan isteyen öncelik müşteriler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="96cd0-148">Genellikle tam kullanabilirsiniz, ancak adresine bir ileti, tanımlı bir uç nokta adı kullanmayı alındı hangi uç noktaya belirlemek için eşleşen, genellikle daha az hata yapmaya açık, özellikle bir Yapılandırması'nı kullanarak bir yönlendirme hizmeti yapılandırırken olan uygun bir kısayol bulunur. (uç nokta adları gerekli bir öznitelik olduğu) dosyası.</span><span class="sxs-lookup"><span data-stu-id="96cd0-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="96cd0-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="96cd0-149">MatchAll</span></span>  
 <span data-ttu-id="96cd0-150">MatchAll filtre herhangi bir alınan ileti ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="96cd0-151">Alınan iletilerin tümünü bir kopyasını depolayan bir günlüğe kaydetme hizmeti gibi belirli bir uç noktası için tüm alınan iletileri yönlendirmek her zaman gerekir, yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="96cd0-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="96cd0-152">Aşağıdaki örnekte tanımlayan bir `FilterElement` MatchAll filtresi kullanan.</span><span class="sxs-lookup"><span data-stu-id="96cd0-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="96cd0-153">XPath</span><span class="sxs-lookup"><span data-stu-id="96cd0-153">XPath</span></span>  
 <span data-ttu-id="96cd0-154">XPath filtresi ileti içinde belirli bir öğeyi incelemek için kullanılan bir XPath sorgusu belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="96cd0-155">XPath filtresi doğrudan herhangi bir XML adreslenebilir giriş iletisi içinde incelemek izin veren bir güçlü filtreleme seçeneğidir; Ancak, aldığınız iletileri yapısının olan özel bilgilere sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="96cd0-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="96cd0-156">Aşağıdaki örnekte tanımlayan bir `FilterElement` ileti "ns" ad alanı öneki'tarafından başvurulan ad alanı içinde "öğesi" adlı bir öğe için incelemek için XPath filtresi kullanan.</span><span class="sxs-lookup"><span data-stu-id="96cd0-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="96cd0-157">Bu filtre, aldığınız iletileri belirli bir değer içeren biliyorsanız, kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="96cd0-158">Örneğin, iki sürümü aynı hizmet barındırıyorsanız ve bildiğiniz hizmetinin daha yeni sürümü için gönderilen iletiler gelmeyecek özel bir başlık içinde benzersiz bir değer içeren bu başlığına giderek XPath kullanır ve değer SrktTanıt karşılaştıran filtre oluşturabilirsiniz başka bir filtre eşleşip eşleşmediğini belirlemek için filtre yapılandırmasında belirtilen üst bilgisindeki ent.</span><span class="sxs-lookup"><span data-stu-id="96cd0-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="96cd0-159">XPath genellikle sorguladığından genellikle uzun benzersiz ad alanlarında bulunur veya karmaşık dize değerleri, XPath filtresi ad tablosu, ad alanları için benzersiz önekleri tanımlamak için kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="96cd0-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="96cd0-160">Ad alanı tablosu hakkında daha fazla bilgi için bkz. [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="96cd0-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="96cd0-161">XPath sorguları tasarlama hakkında daha fazla bilgi için bkz. [XPath sözdizimi](https://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="96cd0-161">For more information about designing XPath queries, see [XPath Syntax](https://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cd0-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96cd0-162">See Also</span></span>  
 [<span data-ttu-id="96cd0-163">İleti Filtreleri</span><span class="sxs-lookup"><span data-stu-id="96cd0-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="96cd0-164">Nasıl yapılır: Filtreleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="96cd0-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
