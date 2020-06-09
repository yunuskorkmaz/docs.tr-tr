---
title: Filtre Seçme
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: e951c472543239df0c01dcba3e46f120ced9e192
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587501"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="8bf5d-102">Filtre Seçme</span><span class="sxs-lookup"><span data-stu-id="8bf5d-102">Choosing a Filter</span></span>
<span data-ttu-id="8bf5d-103">Yönlendirme hizmetini yapılandırırken, doğru ileti filtrelerini seçmek ve bunları aldığınız iletilerle tam olarak eşleştirmenizi sağlamak için yapılandırmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="8bf5d-104">Seçtiğiniz filtreler, eşleşmelerinde çok geniş ise veya yanlış yapılandırıldıysa, iletiler hatalı yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="8bf5d-105">Filtreler çok kısıtlayıcıysa, bazı iletileriniz için geçerli bir yolunuz bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>

## <a name="filter-types"></a><span data-ttu-id="8bf5d-106">Filtre türleri</span><span class="sxs-lookup"><span data-stu-id="8bf5d-106">Filter Types</span></span>

<span data-ttu-id="8bf5d-107">Yönlendirme hizmeti tarafından kullanılan filtreleri seçerken, her bir filtrenin nasıl çalıştığını ve gelen iletilerin bir parçası olarak hangi bilgilerin kullanılabilir olduğunu anlamanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="8bf5d-108">Örneğin, tüm iletiler aynı uç nokta üzerinden alınmışsa, tüm iletiler bu filtrelerle eşleştiğinden adres ve EndpointName filtreleri yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>

### <a name="action"></a><span data-ttu-id="8bf5d-109">Eylem</span><span class="sxs-lookup"><span data-stu-id="8bf5d-109">Action</span></span>

<span data-ttu-id="8bf5d-110">Eylem filtresi, özelliği inceler <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="8bf5d-111">İletideki eylem üstbilgisinin içeriği, filtre yapılandırmasında belirtilen filtre verileri değeriyle eşleşiyorsa, bu filtre döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="8bf5d-112">Aşağıdaki örnek, bir `FilterElement` değeri içeren bir eylem üst bilgisine sahip iletileri eşleştirmek Için eylem filtresini kullanan bir tanımlar `http://namespace/contract/operation/` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

<span data-ttu-id="8bf5d-113">Bu filtre, benzersiz bir eylem üst bilgisi içeren iletileri yönlendirçalışırken kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-113">This filter should be used when routing messages that contain a unique Action header.</span></span>

### <a name="endpointaddress"></a><span data-ttu-id="8bf5d-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="8bf5d-114">EndpointAddress</span></span>

<span data-ttu-id="8bf5d-115">EndpointAddress filtresi, iletinin alındığı EndpointAddress öğesini inceler.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="8bf5d-116">İletinin ulaştığı adres, filtre yapılandırmasında belirtilen filtre adresiyle tam olarak eşleşiyorsa, bu filtre döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="8bf5d-117">Aşağıdaki örnek, `FilterElement` "http:///vdir/s.svc/b" ile adreslenen iletilerle eşleşmesi Için adres filtresini kullanan bir tanımlar \<hostname> .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="8bf5d-118">Bir adresin ana bilgisayar adı bölümünün, istemcinin tam etki alanı adı, NetBIOS adı, IP adresi veya başka bir ad kullanıp kullanmadığını dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="8bf5d-119">Farklı değerler aynı konağa başvurabileceğinden, bu karşılaştırma için varsayılan davranış, eşleşmeleri gerçekleştirirken adresin ana bilgisayar adı kısmını kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>
>
> <span data-ttu-id="8bf5d-120">Bu davranış, yönlendirme hizmetini programlı bir şekilde yapılandırırken karşılaştırmanın ana bilgisayar adını değerlendirmesi için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>

<span data-ttu-id="8bf5d-121">Gelen iletiler benzersiz bir adrese değinilmesi durumunda bu filtre kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>

### <a name="endpointaddressprefix"></a><span data-ttu-id="8bf5d-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="8bf5d-122">EndpointAddressPrefix</span></span>

<span data-ttu-id="8bf5d-123">EndpointAddressPrefix filtresi EndpointAddress filtresine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="8bf5d-124">EndpointAddressPrefix filtresi, iletinin alındığı EndpointAddress öğesini inceler.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="8bf5d-125">Ancak EndpointAddressPrefix filtresi, filtre yapılandırmasında belirtilen değerle başlayan adresleriyle eşleşen bir joker karakter görevi görür.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="8bf5d-126">Aşağıdaki örnek, ile bahsedilen `FilterElement` tüm iletileri eşleştirmek Için EndpointAddressPrefix filtresini kullanan bir tanımlar `http://<hostname>/vdir*` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="8bf5d-127">Bir adresin ana bilgisayar adı bölümünün, istemcinin tam etki alanı adı, NetBIOS adı, IP adresi veya başka bir ad kullanıp kullanmadığını dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="8bf5d-128">Farklı değerler aynı konağa başvurabileceğinden, bu karşılaştırma için varsayılan davranış, eşleşmeleri gerçekleştirirken adresin ana bilgisayar adı kısmını kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>

<span data-ttu-id="8bf5d-129">Bu filtre, ortak adres ön ekini paylaşan gelen iletileri yönlendirmesinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>

### <a name="and"></a><span data-ttu-id="8bf5d-130">AND</span><span class="sxs-lookup"><span data-stu-id="8bf5d-130">AND</span></span>

<span data-ttu-id="8bf5d-131">VE filtresi bir ileti içindeki bir değer üzerinde doğrudan filtrelemez, ancak `AND` her iki filtrenin de ve filtresi hesaplanmadan önce iletiyle eşleşmesi gereken bir koşul oluşturmak için iki diğer filtreyi birleştirmenize olanak tanır `true` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="8bf5d-132">Bu, yalnızca tüm alt filtreler eşleşiyorsa eşleşen karmaşık filtreler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="8bf5d-133">Aşağıdaki örnek bir adres filtresini ve bir eylem filtresini tanımlar ve ardından bir iletiyi hem adres hem de eylem filtrelerine karşı değerlendiren bir ve filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="8bf5d-134">Hem adres hem de eylem filtresi eşleşiyorsa, ve filtresi döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>

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

<span data-ttu-id="8bf5d-135">Bu filtre, bir eşleşmenin ne zaman yapılması gerektiğini öğrenmek için birden çok filtreden mantığı birleştirmeniz gerektiğinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="8bf5d-136">Örneğin, belirli adreslere yalnızca belirli eylem ve ileti birleşimlerini alması gereken birden çok hedef varsa, gerekli eylem ve adres filtrelerini birleştirmek için bir ve filtresi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>

### <a name="custom"></a><span data-ttu-id="8bf5d-137">Özel</span><span class="sxs-lookup"><span data-stu-id="8bf5d-137">Custom</span></span>

<span data-ttu-id="8bf5d-138">Özel filtre türünü seçerken, bu filtre için kullanılacak **MessageFilter** uygulamasını içeren derlemenin türünü Içeren bir CustomType değeri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="8bf5d-139">Ayrıca, filterData özel filtrenin ileti değerlendirmesi için ihtiyaç duyduğu herhangi bir değer içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="8bf5d-140">Aşağıdaki örnek, `FilterElement` `CustomAssembly.MyCustomMsgFilter` MessageFilter uygulamasını kullanan bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

<span data-ttu-id="8bf5d-141">İle birlikte sunulan filtrelerin kapsamına girmeyen bir iletiye karşı özel bir eşleştirme mantığı gerçekleştirmeniz gerekiyorsa [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] , **MessageFilter** sınıfının uygulanması olan özel bir filtre oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="8bf5d-142">Örneğin, gelen iletideki bir alanı, yapılandırmaya göre filtreye verilen bilinen değerler listesiyle veya belirli bir ileti öğesini karmalarını ve sonra filtrenin döneceğini veya bu değere inceleyerek, bu değeri inceleyerek bir özel filtre oluşturabilirsiniz `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="8bf5d-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>

### <a name="endpointname"></a><span data-ttu-id="8bf5d-143">Uçnoktaadı</span><span class="sxs-lookup"><span data-stu-id="8bf5d-143">EndpointName</span></span>

<span data-ttu-id="8bf5d-144">EndpointName filtresi, iletiyi alan uç noktanın adını inceler.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="8bf5d-145">Aşağıdaki örnek, `FilterElement` "SvcEndpoint" üzerinde alınan iletileri yönlendirmek Için EndpointName filtresini kullanan bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

<span data-ttu-id="8bf5d-146">Bu filtre, yönlendirme hizmeti birden fazla adlandırılmış hizmet uç noktası açığa çıkardığı zaman yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="8bf5d-147">Örneğin, yönlendirme hizmetinin iletileri almak için kullandığı iki uç noktayı kullanıma sunmanız gerekebilir; biri, iletilerinin gerçek zamanlı işlenmesini gerektiren öncelikli müşteriler tarafından kullanılır, diğer uç nokta zamana duyarlı olmayan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>

<span data-ttu-id="8bf5d-148">Genellikle bir iletinin hangi bitiş noktasına alındığını tespit etmek için tam adres eşleştirmeyi kullanabilirsiniz. bunun yerine, özellikle de bir yapılandırma dosyası (uç nokta adları gerekli bir özniteliktir) kullanılarak bir yönlendirme hizmeti yapılandırılırken, genellikle daha az hata durumunda olan kullanışlı bir kısayoldur.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>

### <a name="matchall"></a><span data-ttu-id="8bf5d-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="8bf5d-149">MatchAll</span></span>

<span data-ttu-id="8bf5d-150">MatchAll filtresi, alınan tüm iletiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="8bf5d-151">Alınan tüm iletilerin bir kopyasını depolayan günlüğe kaydetme hizmeti gibi, tüm alınan iletileri her zaman belirli bir uç noktasına yönlendirdiğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="8bf5d-152">Aşağıdaki örnek, `FilterElement` MatchAll filtresini kullanan bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a><span data-ttu-id="8bf5d-153">XPath</span><span class="sxs-lookup"><span data-stu-id="8bf5d-153">XPath</span></span>

<span data-ttu-id="8bf5d-154">XPath filtresi, ileti içinde belirli bir öğeyi denetlemek için kullanılan bir XPath sorgusu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="8bf5d-155">XPath filtreleme, ileti içinde herhangi bir XML adreslenebilir girişi doğrudan incelemenize olanak tanıyan güçlü bir filtreleme seçeneğidir; Ancak, aldığınız iletilerin yapısına özgü bir bilginiz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="8bf5d-156">Aşağıdaki örnek, `FilterElement` "NS" ad alanı öneki tarafından başvurulan ad alanı içinde "element" adlı bir öğenin iletisini incelemek Için XPath filtresini kullanan bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

<span data-ttu-id="8bf5d-157">Bu filtre, aldığınız iletilerin belirli bir değer içerdiğini biliyorsanız yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="8bf5d-158">Örneğin, aynı hizmetin iki sürümünü barındırıyorsanız ve hizmetin yeni sürümüne ait olan iletilerin özel bir üst bilgide benzersiz bir değer içerdiğini biliyorsanız, bu üstbilgiye gitmek için XPath kullanan bir filtre oluşturabilir ve filtrenin eşleşip eşleşmediğini öğrenmek için üst bilgide bulunan değeri filtre yapılandırmasında başka bir şekilde karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>

<span data-ttu-id="8bf5d-159">XPath sorguları genellikle uzun veya karmaşık dize değerleri olan benzersiz ad alanları içerdiğinden, XPath filtresi, ad alanlarınızın benzersiz öneklerini tanımlamak için ad alanı tablosunu kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="8bf5d-160">Ad alanı tablosu hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="8bf5d-160">For more information about the namespace table, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="8bf5d-161">XPath sorguları tasarlama hakkında daha fazla bilgi için bkz. [XPath sözdizimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8bf5d-161">For more information about designing XPath queries, see [XPath Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="8bf5d-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bf5d-162">See also</span></span>

- [<span data-ttu-id="8bf5d-163">İleti Filtreleri</span><span class="sxs-lookup"><span data-stu-id="8bf5d-163">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="8bf5d-164">Nasıl yapılır: Filtreleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="8bf5d-164">How To: Use Filters</span></span>](how-to-use-filters.md)
