---
title: "İşlem Biçimlendirici ve İşlem Seçici"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3fd8b59cd69807928b1a441d1bfb57f82d072288
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="d81bc-102">İşlem Biçimlendirici ve İşlem Seçici</span><span class="sxs-lookup"><span data-stu-id="d81bc-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="d81bc-103">Bu örnek gösterilmektedir nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] genişletilebilirlik noktaları, farklı bir biçimde ne gelen ileti veri sağlamak için kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bekliyor.</span><span class="sxs-lookup"><span data-stu-id="d81bc-103">This sample demonstrates how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extensibility points can be used to allow message data in a different format from what [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects.</span></span> <span data-ttu-id="d81bc-104">Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] biçimlendiricileri beklediğiniz altında dahil edilecek yöntem parametreleri `soap:body` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d81bc-104">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="d81bc-105">Örnek, bunun yerine bir HTTP GET sorgu dizesi parametre verilerini ayrıştırır ve bu verileri kullanarak yöntemlerini çağıran bir özel işlem biçimlendirici uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="d81bc-106">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d81bc-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="d81bc-107">Bunu gösterir nasıl eklenir, çıkarma, Çarp, bölme iletileri, HTTP GET istemci-sunucu istekleri için kullanılacak değiştirilebilir ve POX ile HTTP POST için sunucudan istemciye yanıt iletileri.</span><span class="sxs-lookup"><span data-stu-id="d81bc-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="d81bc-108">Bunu yapmak için örnek aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="d81bc-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="d81bc-109">`QueryStringFormatter`, hangi uygulayan <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> istemci ve sunucu için sırasıyla ve sorgu dizesi verileri işler.</span><span class="sxs-lookup"><span data-stu-id="d81bc-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="d81bc-110">`UriOperationSelector`, hangi uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> GET isteği işlemi adına dayalı gönderme işlemi gerçekleştirmek için sunucu üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d81bc-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="d81bc-111">`EnableHttpGetRequestsBehavior`uç noktası davranışı (ve karşılık gelen yapılandırma), çalışma zamanı için gerekli işlem Seçici ekler.</span><span class="sxs-lookup"><span data-stu-id="d81bc-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="d81bc-112">Nasıl yeni bir işlem biçimlendirici çalışma zamanına ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="d81bc-113">Bu örnekte, hem istemci hem de hizmet konsol (.exe) uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d81bc-114">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="d81bc-115">Temel Kavramlar</span><span class="sxs-lookup"><span data-stu-id="d81bc-115">Key Concepts</span></span>  
 <span data-ttu-id="d81bc-116">`QueryStringFormatter`-İşlemini biçimlendiricisi bileşenidir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] parametresi nesnelerinin bir dizisi ve bir iletisine parametre nesnelerinin bir dizisi için bir ileti dönüştürme sorumlu.</span><span class="sxs-lookup"><span data-stu-id="d81bc-116">`QueryStringFormatter` - The operation formatter is the component in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="d81bc-117">Bu istemciyi kullanarak yapılır <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi ve ile sunucuya <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d81bc-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="d81bc-118">Gelen istek ve yanıt iletileri almak kullanıcıların bu arabirimleri sağlamak `Serialize` ve `Deserialize` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d81bc-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="d81bc-119">Bu örnekte `QueryStringFormatter` hem de bu arabirimlerini uygular ve istemci ve sunucu üzerinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="d81bc-120">İsteği:</span><span class="sxs-lookup"><span data-stu-id="d81bc-120">Request:</span></span>  
  
-   <span data-ttu-id="d81bc-121">Örnek kullanır <xref:System.ComponentModel.TypeConverter> dizeleri gelen ve giden istek iletisindeki parametre veri dönüştürmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d81bc-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="d81bc-122">Varsa bir <xref:System.ComponentModel.TypeConverter> özel bir örnek biçimlendirici atar belirli bir türü için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d81bc-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="d81bc-123">İçinde `IClientMessageFormatter.SerializeRequest` yöntemi istemcisinde, biçimlendirici uygun adresine sahip bir URI oluşturur ve işlem adı soneki olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="d81bc-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="d81bc-124">Bu ad, sunucudaki uygun işlemini gönderilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="d81bc-125">Ardından parametre nesneler dizisi alır ve parametre adları ve dönüştürülen değerleri kullanarak URI sorgu dizesi parametresi verileri serileştirir <xref:System.ComponentModel.TypeConverter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d81bc-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="d81bc-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Ve <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri daha sonra bu URI ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d81bc-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="d81bc-127"><xref:System.ServiceModel.Channels.MessageProperties>üzerinden erişilen <xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d81bc-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="d81bc-128">İçinde `IDispatchMessageFormatter.DeserializeRequest` yöntemi sunucuda biçimlendirici alır `Via` gelen istek ileti özelliklerinde URI.</span><span class="sxs-lookup"><span data-stu-id="d81bc-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="d81bc-129">Ad-değer çiftleri URI sorgu dizesinde parametre adları ve değerlerine ayrıştırır ve yönteme geçirilen parametre dizisi doldurmak için parametre adları ve değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="d81bc-130">Bu nedenle bu yöntemi, işlem adı soneki yoksayıldı işlemi gönderme zaten oluştu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d81bc-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="d81bc-131">Yanıtı:</span><span class="sxs-lookup"><span data-stu-id="d81bc-131">Response:</span></span>  
  
-   <span data-ttu-id="d81bc-132">Bu örnekte, HTTP GET isteği yalnızca için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="d81bc-133">Biçimlendirici bir XML iletisi oluşturmak için kullanılanla özgün biçimlendirici yanıtı gönderilirken atar.</span><span class="sxs-lookup"><span data-stu-id="d81bc-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="d81bc-134">Bu örnek hedeflerinden temsilci bir biçimlendirici nasıl uygulanabilir göstermektir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="d81bc-135">UriPathSuffixOperationSelector sınıfı</span><span class="sxs-lookup"><span data-stu-id="d81bc-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="d81bc-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Arabirimi hangi işlemi için belirli bir ileti gönderilen kendi mantığını uygulamak kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="d81bc-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="d81bc-137">Bu örnekte `UriPathSuffixOperationSelector` işlem adı bir eylem üstbilgisi iletisi yerine HTTP GET URI bulunduğundan uygun işlemi seçmek için sunucuda uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="d81bc-138">Örnek adları yalnızca küçük harf işlemi izin verecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="d81bc-139">`SelectOperation` Yöntemi gelen iletiyi alır ve arayan `Via` ileti özelliklerinde URI.</span><span class="sxs-lookup"><span data-stu-id="d81bc-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="d81bc-140">URI'den işlemi ad soneki ayıklar, ileti gönderilen işlemi adını almak için bir iç tablosu arar ve bu işlemi adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d81bc-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="d81bc-141">EnableHttpGetRequestsBehavior sınıfı</span><span class="sxs-lookup"><span data-stu-id="d81bc-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="d81bc-142">`UriPathSuffixOperationSelector` Bileşen ayarlanabilir programlı olarak veya bir uç noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="d81bc-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="d81bc-143">Örnek uygulayan `EnableHttpGetRequestsBehavior` hizmetin uygulama yapılandırma dosyasında belirtilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="d81bc-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="d81bc-144">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="d81bc-144">On the server:</span></span>  
  
 <span data-ttu-id="d81bc-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ayarlanır <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d81bc-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="d81bc-146">Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir tam eşleşme adresi filtresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-146">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses an exact-match address filter.</span></span> <span data-ttu-id="d81bc-147">Uç noktası davranışı olmasını adresi Filtresi ayrıca değişiklikler filtre eşleşen bir önek, URI gelen ileti üzerinde parametre veri içeren bir sorgu dizesi tarafından izlenen bir işlemi ad soneki içerir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="d81bc-148">Kullandığı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="d81bc-148">It uses the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="d81bc-149">Yükleme işlemi biçimlendiricileri</span><span class="sxs-lookup"><span data-stu-id="d81bc-149">Installing operation formatters</span></span>  
 <span data-ttu-id="d81bc-150">Biçimlendiricileri belirtin işlemi davranışları benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="d81bc-151">Bu tür bir davranış her zaman gerekli işlemini biçimlendiricisi oluşturmak her işlem için varsayılan olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="d81bc-152">Ancak, bu davranışların gibi başka bir işlem davranışı arar; Bunlar herhangi bir öznitelik tarafından tanımlanabilen değildir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="d81bc-153">Değiştirme davranışı yüklemek için uygulama tarafından yüklenen belirli biçimlendirici davranışları aramanız gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan türü Yükleyicisi ve değiştirmek veya varsayılan davranışı sonra çalıştırmak için uyumlu bir davranış ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d81bc-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="d81bc-154">Bu işlemi biçimlendiricileri davranışları önce arama program aracılığıyla ayarlanabilir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> veya varsayılan sonra yürütülen bir işlem davranışı belirterek.</span><span class="sxs-lookup"><span data-stu-id="d81bc-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="d81bc-155">Ancak, bunu kolayca bir uç noktası davranışı tarafından ayarlanamaz (ve bu nedenle yapılandırmaya göre) davranış modeli davranışları değiştirin veya aksi halde açıklama ağaç değiştirmek bir davranış izin vermediğinden.</span><span class="sxs-lookup"><span data-stu-id="d81bc-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="d81bc-156">İstemci üzerinde:</span><span class="sxs-lookup"><span data-stu-id="d81bc-156">On the client:</span></span>  
  
 <span data-ttu-id="d81bc-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Uygulaması gerekir uygulanan isteklerini HTTP GET isteklerine dönüştürmek ve yanıtlarının özgün biçimlendirici için temsilci.</span><span class="sxs-lookup"><span data-stu-id="d81bc-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="d81bc-158">Bu çağırarak yapılır `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d81bc-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="d81bc-159">Bu çağırmadan önce yapılmalıdır `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="d81bc-159">This must be done before calling `CreateChannel`.</span></span>  
  
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
  
 <span data-ttu-id="d81bc-160">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="d81bc-160">On the server:</span></span>  
  
-   <span data-ttu-id="d81bc-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimi gerekir uygulanan böylece okuma HTTP GET istekleri ve yanıtlar yazmak için temsilci seçme için özgün biçimlendirici.</span><span class="sxs-lookup"><span data-stu-id="d81bc-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="d81bc-162">Bu aynı çağırarak yapılır `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi istemci olarak (Yukarıdaki örnek kod bakın).</span><span class="sxs-lookup"><span data-stu-id="d81bc-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="d81bc-163">Bu, önce yapılmalıdır <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="d81bc-164">Bu örnekte, biçimlendirici çağırmadan önce el ile nasıl değiştirilmiş olan gösteriyoruz <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="d81bc-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="d81bc-165">Aynı şey elde etmek için başka bir öğesinden bir sınıf türetin yoldur <xref:System.ServiceModel.ServiceHost> çağrı yapar `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` açmadan önce (belgeler ve örnekler için örnekler barındırma Lütfen bakın).</span><span class="sxs-lookup"><span data-stu-id="d81bc-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="d81bc-166">Kullanıcı deneyimleri</span><span class="sxs-lookup"><span data-stu-id="d81bc-166">User experience</span></span>  
 <span data-ttu-id="d81bc-167">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="d81bc-167">On the server:</span></span>  
  
-   <span data-ttu-id="d81bc-168">Sunucunun `ICalculator` uygulama değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d81bc-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="d81bc-169">Hizmeti için App.config ayarlar özel bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`.</span><span class="sxs-lookup"><span data-stu-id="d81bc-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
-   <span data-ttu-id="d81bc-170">Hizmeti için App.config özel de belirtmeniz gerekir `EnableHttpGetRequestsBehavior` davranışı Uzantıları bölümüne ekleyerek ve bunu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d81bc-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
-   <span data-ttu-id="d81bc-171">Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="d81bc-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="d81bc-172">İstemci üzerinde:</span><span class="sxs-lookup"><span data-stu-id="d81bc-172">On the client:</span></span>  
  
-   <span data-ttu-id="d81bc-173">İstemci uygulaması değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d81bc-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="d81bc-174">İstemci için App.config ayarlar özel bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`.</span><span class="sxs-lookup"><span data-stu-id="d81bc-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="d81bc-175">Bir hizmet istemci adresine giden değiştirilebilir böylece el ile adresleme etkinleştirmelisiniz farktır.</span><span class="sxs-lookup"><span data-stu-id="d81bc-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
-   <span data-ttu-id="d81bc-176">App.config istemci için aynı özel belirtmelisiniz `EnableHttpGetRequestsBehavior` sunucusu olarak.</span><span class="sxs-lookup"><span data-stu-id="d81bc-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="d81bc-177">Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="d81bc-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="d81bc-178">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d81bc-179">Tüm dört işlemleri (eklemek, çıkarma, çarpma ve bölme) başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d81bc-180">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d81bc-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d81bc-181">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d81bc-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d81bc-182">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d81bc-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d81bc-183">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d81bc-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d81bc-184">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d81bc-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d81bc-185">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d81bc-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d81bc-186">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d81bc-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d81bc-187">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d81bc-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d81bc-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d81bc-188">See Also</span></span>
