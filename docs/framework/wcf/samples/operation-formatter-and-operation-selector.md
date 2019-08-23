---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 977a759b2c3f6d803879fc640439cd0b3465ffbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965584"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="5e701-102">İşlem Biçimlendirici ve İşlem Seçici</span><span class="sxs-lookup"><span data-stu-id="5e701-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="5e701-103">Bu örnek, WCF 'nin beklediği farklı biçimdeki ileti verilerine izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktalarının nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e701-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="5e701-104">Varsayılan olarak, WCF biçimleri `soap:body` öğesi altına eklenecek yöntem parametrelerini bekler.</span><span class="sxs-lookup"><span data-stu-id="5e701-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="5e701-105">Örnek, bunun yerine bir HTTP GET sorgu dizesinden parametre verilerini çözümleyen ve bu verileri kullanarak yöntemleri çağıran özel bir işlem biçimlendiricinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e701-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="5e701-106">Örnek, `ICalculator` hizmet sözleşmesini uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="5e701-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5e701-107">Ekleme, çıkarma, çarpma ve bölme iletilerinin, sunucudan istemciye yanıtlara yönelik POX iletileri ile istemci-sunucu istekleri ve HTTP POST için HTTP GET kullanmak üzere nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e701-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="5e701-108">Bunu yapmak için örnek şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="5e701-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="5e701-109">`QueryStringFormatter`, sırasıyla istemci <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> sunucu uygulayan ve sorgu dizesindeki verileri işleyen.</span><span class="sxs-lookup"><span data-stu-id="5e701-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="5e701-110">`UriOperationSelector`Bu, Get <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> isteğindeki işlem adına göre işlem gönderimi gerçekleştirmek için sunucusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="5e701-111">`EnableHttpGetRequestsBehavior`gerekli işlem seçiciyi çalışma zamanına ekleyen uç nokta davranışı (ve karşılık gelen yapılandırma).</span><span class="sxs-lookup"><span data-stu-id="5e701-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="5e701-112">Çalışma zamanına nasıl yeni bir işlem biçimlendirici ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e701-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="5e701-113">Bu örnekte, hem istemci hem de hizmet konsol uygulamalardır (. exe).</span><span class="sxs-lookup"><span data-stu-id="5e701-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e701-114">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5e701-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="5e701-115">Temel Kavramlar</span><span class="sxs-lookup"><span data-stu-id="5e701-115">Key Concepts</span></span>  
 <span data-ttu-id="5e701-116">`QueryStringFormatter`-İşlem biçimlendirici, bir iletiyi bir parametre nesneleri dizisine ve bir dizi parametre nesnesine dönüştürmekten sorumlu olan WCF 'deki bileşendir.</span><span class="sxs-lookup"><span data-stu-id="5e701-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="5e701-117">Bu, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi kullanılarak ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi ile sunucusunda yapılır.</span><span class="sxs-lookup"><span data-stu-id="5e701-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="5e701-118">Bu arabirimler, `Serialize` kullanıcıların ve `Deserialize` yöntemlerinden istek ve yanıt iletilerini almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e701-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="5e701-119">Bu örnekte, `QueryStringFormatter` bu arabirimlerin her ikisini de uygular ve istemci ve sunucu üzerinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="5e701-120">İsteyen</span><span class="sxs-lookup"><span data-stu-id="5e701-120">Request:</span></span>  
  
- <span data-ttu-id="5e701-121">Örnek, istek iletisindeki <xref:System.ComponentModel.TypeConverter> parametre verilerini dizeden ve dizeden dönüştürmek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="5e701-122">Belirli bir <xref:System.ComponentModel.TypeConverter> tür için kullanılabilir değilse, örnek biçimlendirici bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e701-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="5e701-123">İstemci üzerindeki `IClientMessageFormatter.SerializeRequest` yönteminde, biçimlendirici uygun bir URI oluşturur ve işlem adını bir sonek olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="5e701-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="5e701-124">Bu ad, sunucuda uygun işleme göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e701-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="5e701-125">Daha sonra parametre nesnelerinin dizisini alır ve parametre adlarını ve <xref:System.ComponentModel.TypeConverter> sınıf tarafından dönüştürülen değerleri kullanarak parametre verilerini URI sorgu dizesine dizleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e701-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="5e701-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Ve<xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri bu URI 'ye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="5e701-127"><xref:System.ServiceModel.Channels.MessageProperties><xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği aracılığıyla erişilir.</span><span class="sxs-lookup"><span data-stu-id="5e701-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="5e701-128">Sunucusundaki yönteminde, biçimlendirici gelen istek iletisi özelliklerindeki `Via` URI 'yi alır. `IDispatchMessageFormatter.DeserializeRequest`</span><span class="sxs-lookup"><span data-stu-id="5e701-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="5e701-129">URI sorgu dizesindeki ad-değer çiftlerini parametre adları ve değerleri olarak ayrıştırır ve yönteme geçirilen parametrelerin dizisini doldurmak için parametre adlarını ve değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="5e701-130">İşlem dağıtımının zaten gerçekleştiğini, bu nedenle işlem adı son ekinin bu yöntemde yoksayıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5e701-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="5e701-131">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="5e701-131">Response:</span></span>  
  
- <span data-ttu-id="5e701-132">Bu örnekte, HTTP GET yalnızca istek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e701-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="5e701-133">Biçimlendirici, yanıtın bir XML iletisi oluşturmak için kullanılan özgün biçimlendirici öğesine gönderilmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="5e701-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="5e701-134">Bu örneğin hedeflerinden biri, bu tür bir temsilci seçme biçimlendiricisi nasıl uygulankullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e701-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="5e701-135">Urıthsonson Fixoperationselector sınıfı</span><span class="sxs-lookup"><span data-stu-id="5e701-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="5e701-136">Arabirim <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> , kullanıcıların belirli bir ileti dağıtılması için kendi mantığını uygulamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e701-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="5e701-137">Bu örnekte, işlem `UriPathSuffixOperationSelector` adı iletideki bir eylem üst bilgisi yerine http get URI 'sine dahil edildiğinden, uygun işlemi seçmek için sunucuda uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="5e701-138">Örnek yalnızca büyük/küçük harf duyarsız işlem adlarına izin verecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="5e701-139">Yöntemi gelen iletiyi alır ve kendi ileti özelliklerinde `Via` URI 'yi arar. `SelectOperation`</span><span class="sxs-lookup"><span data-stu-id="5e701-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="5e701-140">URI 'den işlem adı sonekini ayıklar, iletinin dağıtılması gereken işlem adını almak için bir iç tablo arar ve bu işlem adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e701-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="5e701-141">EnableHttpGetRequestsBehavior sınıfı</span><span class="sxs-lookup"><span data-stu-id="5e701-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="5e701-142">`UriPathSuffixOperationSelector` Bileşen program aracılığıyla veya bir uç nokta davranışı aracılığıyla ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5e701-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="5e701-143">Örnek, hizmetin uygulama `EnableHttpGetRequestsBehavior` yapılandırma dosyasında belirtilen davranışı uygular.</span><span class="sxs-lookup"><span data-stu-id="5e701-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="5e701-144">Sunucusunda:</span><span class="sxs-lookup"><span data-stu-id="5e701-144">On the server:</span></span>  
  
 <span data-ttu-id="5e701-145">, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Uygulama<xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="5e701-146">Varsayılan olarak, WCF tam eşleşme adresi filtresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="5e701-147">Gelen iletideki URI, bir işlem adı soneki ve ardından parametre verilerini içeren bir sorgu dizesi içerir, bu nedenle uç nokta davranışı da adres filtresini önek eşleşme filtresi olacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5e701-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="5e701-148">Bu amaçla WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="5e701-149">İşlem formatlayıcıları yükleniyor</span><span class="sxs-lookup"><span data-stu-id="5e701-149">Installing operation formatters</span></span>  
 <span data-ttu-id="5e701-150">Formatlayıcıları belirten işlem davranışları benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="5e701-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="5e701-151">Bu tür bir davranış, her zaman gerekli işlem biçimlendirici oluşturmak için her işlem için varsayılan olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5e701-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="5e701-152">Ancak, bu davranışlar yalnızca başka bir işlem davranışı gibi görünür; Bunlar başka bir öznitelik tarafından tanımlanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="5e701-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="5e701-153">Değiştirme davranışı yüklemek için, uygulamanın varsayılan olarak WCF türü yükleyici tarafından yüklenen belirli biçimlendirici davranışlarını araması ve bunu değiştirmesi ya da varsayılan davranışından sonra çalışacak uyumlu bir davranış eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="5e701-154">Bu işlem biçimlendiricileri davranışları, çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> önce veya varsayılan bir işlemden sonra yürütülen bir işlem davranışı belirtilerek program aracılığıyla ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5e701-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="5e701-155">Ancak, davranış modeli bir davranışın diğer davranışları değiştirmesine izin vermediğinden veya açıklama ağacını değiştiremediğinden, bir uç nokta davranışı (ve dolayısıyla yapılandırmaya göre) kolayca ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="5e701-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="5e701-156">İstemcide:</span><span class="sxs-lookup"><span data-stu-id="5e701-156">On the client:</span></span>  
  
 <span data-ttu-id="5e701-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Uygulamanın istekleri HTTP GET isteklerine dönüştürebilmesi ve yanıtlar için özgün biçimlendirici için temsilci olarak uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="5e701-158">Bu, `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="5e701-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="5e701-159">Çağrılmadan `CreateChannel`önce bunun yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="5e701-160">Sunucusunda:</span><span class="sxs-lookup"><span data-stu-id="5e701-160">On the server:</span></span>  
  
- <span data-ttu-id="5e701-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimin http get isteklerini okuyabilmesi ve yanıtları yazmak için özgün biçimlendirici için temsilci olarak uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="5e701-162">Bu, istemcisiyle aynı `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır (önceki kod örneğine bakın).</span><span class="sxs-lookup"><span data-stu-id="5e701-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="5e701-163">Çağrılmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> bunun yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="5e701-164">Bu örnekte, bir biçimlendirici çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce el ile nasıl değiştirildiğini gösteririz.</span><span class="sxs-lookup"><span data-stu-id="5e701-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="5e701-165">Aynı şeyi elde etmenin bir diğer yolu da, açmadan <xref:System.ServiceModel.ServiceHost> `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` önce çağrıları yapan öğesinden bir sınıf türetmektir (lütfen bkz. barındırma belgeleri ve örnekler için örnekler).</span><span class="sxs-lookup"><span data-stu-id="5e701-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="5e701-166">Kullanıcı deneyimleri</span><span class="sxs-lookup"><span data-stu-id="5e701-166">User experience</span></span>  
 <span data-ttu-id="5e701-167">Sunucusunda:</span><span class="sxs-lookup"><span data-stu-id="5e701-167">On the server:</span></span>  
  
- <span data-ttu-id="5e701-168">Sunucu `ICalculator` uygulamasının değiştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5e701-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="5e701-169">Hizmetin App. config `messageVersion` `textMessageEncoding` öğesinin özniteliğini olarak `None`ayarlayan özel bir POX bağlaması kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="5e701-170">Hizmetin App. config dosyası, davranış uzantıları bölümüne ekleyerek ve onu `EnableHttpGetRequestsBehavior` kullanarak özel olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5e701-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- <span data-ttu-id="5e701-171">Çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce işlem formatlayıcıları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e701-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="5e701-172">İstemcide:</span><span class="sxs-lookup"><span data-stu-id="5e701-172">On the client:</span></span>  
  
- <span data-ttu-id="5e701-173">İstemci uygulamasının değiştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5e701-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="5e701-174">İstemci için App. config `messageVersion` `textMessageEncoding` öğesinin özniteliğini olarak `None`ayarlayan özel bir POX bağlaması kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e701-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="5e701-175">Hizmetin bir farkı, istemcinin el ile adreslemeyi etkinleştirmek zorunda olduğundan, giden adresinin değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e701-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="5e701-176">İstemci için App. config, sunucu ile aynı özel `EnableHttpGetRequestsBehavior` öğesini belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="5e701-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="5e701-177">Çağrılmadan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>önce işlem formatlayıcıları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e701-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="5e701-178">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5e701-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5e701-179">Dört işlemin tümü (Ekle, çıkart, çarp ve Böl) başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e701-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e701-180">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e701-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e701-181">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5e701-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e701-182">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="5e701-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e701-183">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5e701-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e701-184">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5e701-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5e701-185">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e701-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5e701-186">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e701-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5e701-187">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e701-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
