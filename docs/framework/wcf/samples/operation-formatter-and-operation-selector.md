---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144285"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="3de5e-102">İşlem Biçimlendirici ve İşlem Seçici</span><span class="sxs-lookup"><span data-stu-id="3de5e-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="3de5e-103">Bu örnek, Windows Communication Foundation (WCF) genişletilebilirlik noktalarının, ileti verilerine WCF'nin beklediğinden farklı bir biçimde izin vermek için nasıl kullanılabileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="3de5e-104">Varsayılan olarak, WCF formatters yöntem parametrelerinin `soap:body` öğenin altına dahil olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="3de5e-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="3de5e-105">Örnek, parametre verilerini bir HTTP GET sorgu dizesinden ayrıştıran ve bu verileri kullanarak yöntemler çağıran özel bir işlem formatter'ın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="3de5e-106">Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="3de5e-107">İletileri Ekle, Çıkar, Çarpve Böl'ün istemciden sunucuya istekler için HTTP GET'i ve sunucudan istemciye yanıtlar için POX iletileriyle HTTP POST'u kullanmak üzere nasıl değiştirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="3de5e-108">Bunu yapmak için, örnek aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="3de5e-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="3de5e-109">`QueryStringFormatter`, sırasıyla <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> istemci ve sunucu için uygular ve sorgu dizesindeki verileri işler.</span><span class="sxs-lookup"><span data-stu-id="3de5e-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="3de5e-110">`UriOperationSelector`, GET <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> isteğindeki işlem adına göre işlem gönderme gerçekleştirmek için sunucuda uygular.</span><span class="sxs-lookup"><span data-stu-id="3de5e-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="3de5e-111">`EnableHttpGetRequestsBehavior`çalışma süresine gerekli işlem seçicisini ekleyen uç nokta davranışı (ve buna karşılık gelen yapılandırma).</span><span class="sxs-lookup"><span data-stu-id="3de5e-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="3de5e-112">Çalışma süresine yeni bir işlem için nasıl ekilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="3de5e-113">Bu örnekte, hem istemci hem de hizmet konsol uygulamaları (.exe) vardır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3de5e-114">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="3de5e-115">Önemli Kavramlar</span><span class="sxs-lookup"><span data-stu-id="3de5e-115">Key Concepts</span></span>  
 <span data-ttu-id="3de5e-116">`QueryStringFormatter`- Formatter işlemi, WCF'de bir iletiyi parametre nesnelerine ve bir dizi parametre nesnesine bir iletiye dönüştürmekten sorumlu olan bileşendir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="3de5e-117">Bu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirim kullanılarak istemci ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirim ile sunucuda yapılır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="3de5e-118">Bu arabirimler, kullanıcıların istek ve yanıt `Serialize` iletilerini `Deserialize` yöntem ve yöntemlerden almalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3de5e-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="3de5e-119">Bu örnekte, `QueryStringFormatter` bu arabirimlerin her ikisini de uygular ve istemci ve sunucu üzerinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="3de5e-120">İstek:</span><span class="sxs-lookup"><span data-stu-id="3de5e-120">Request:</span></span>  
  
- <span data-ttu-id="3de5e-121">Örnek, istek <xref:System.ComponentModel.TypeConverter> iletisindeki parametre verilerini dizeleri dizeleri ve dizeleri dönüştürmek için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="3de5e-122">Belirli <xref:System.ComponentModel.TypeConverter> bir tür için a kullanılamıyorsa, örnek madde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3de5e-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="3de5e-123">İstemci `IClientMessageFormatter.SerializeRequest` üzerindeki yöntemde, formatter uygun Adres ile bir URI oluşturur ve bir sonek olarak işlem adı ekler.</span><span class="sxs-lookup"><span data-stu-id="3de5e-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="3de5e-124">Bu ad, sunucudaki uygun işlemi göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="3de5e-125">Daha sonra parametre nesneleri dizialır ve parametre adları ve <xref:System.ComponentModel.TypeConverter> sınıf tarafından dönüştürülen değerleri kullanarak URI sorgu dizepara verileri serileştirir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="3de5e-126">Ve <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri daha sonra bu URI ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="3de5e-127"><xref:System.ServiceModel.Channels.MessageProperties><xref:System.ServiceModel.Channels.Message.Properties%2A> tesis üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="3de5e-128">Sunucudaki `IDispatchMessageFormatter.DeserializeRequest` yöntemde, formatter gelen istek `Via` iletisi özelliklerinde URI'yi alır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="3de5e-129">URI sorgu dizesindeki ad-değer çiftlerini parametre adları ve değerleri olarak parlar ve yönteme geçirilen parametre dizisini doldurmak için parametre adlarını ve değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="3de5e-130">Bu yöntemde işlem adı sonek lerinin yoksayıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3de5e-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="3de5e-131">Yanıt:</span><span class="sxs-lookup"><span data-stu-id="3de5e-131">Response:</span></span>  
  
- <span data-ttu-id="3de5e-132">Bu örnekte, HTTP GET yalnızca istek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="3de5e-133">Formatter, xml iletisi oluşturmak için kullanılan orijinal maddeye yanıt gönderilmesini delege eder.</span><span class="sxs-lookup"><span data-stu-id="3de5e-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="3de5e-134">Bu örneğin amaçlarından biri, böyle bir yasal maddenin nasıl uygulanabileceğini göstermektir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="3de5e-135">UriPathSuffixOperationSeçici Sınıf</span><span class="sxs-lookup"><span data-stu-id="3de5e-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="3de5e-136">Arabirim, <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> kullanıcıların belirli bir iletinin gönderilmesi için kendi mantıklarını uygulamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3de5e-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="3de5e-137">Bu örnekte, işlem adı iletide bir eylem üstbilgisi yerine HTTP GET URI'ye dahil olduğundan, `UriPathSuffixOperationSelector` uygun işlemi seçmek için sunucuda uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="3de5e-138">Örnek, yalnızca büyük/küçük harf duyarlı işlem adlarına izin verecek şekilde ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="3de5e-139">Yöntem `SelectOperation` gelen iletiyi alır ve `Via` ileti özelliklerinde URI'yi arar.</span><span class="sxs-lookup"><span data-stu-id="3de5e-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="3de5e-140">URI'den işlem adı soneki ayıklar, iletinin gönderilmesi gereken işlem adını almak için dahili bir tabloya bakar ve bu işlem adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3de5e-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="3de5e-141">EnablehttpGetRequestsBehavior Sınıfı</span><span class="sxs-lookup"><span data-stu-id="3de5e-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="3de5e-142">Bileşen `UriPathSuffixOperationSelector` programlı olarak veya bir bitiş noktası davranışı ile ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="3de5e-143">Örnek, hizmetin `EnableHttpGetRequestsBehavior` uygulama yapılandırma dosyasında belirtilen davranışı uygular.</span><span class="sxs-lookup"><span data-stu-id="3de5e-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="3de5e-144">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="3de5e-144">On the server:</span></span>  
  
 <span data-ttu-id="3de5e-145">Uygulama <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> için <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="3de5e-146">Varsayılan olarak, WCF tam eşleme adresi filtresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="3de5e-147">Gelen iletideki URI, parametre verileri içeren bir sorgu dizesi tarafından izlenen bir işlem adı eki içerir, bu nedenle bitiş noktası davranışı adres filtresini önek eşleme filtresi olarak da değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="3de5e-148">Bu amaç için<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF kullanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="3de5e-149">Formatters operasyonun yüklenmesi</span><span class="sxs-lookup"><span data-stu-id="3de5e-149">Installing operation formatters</span></span>  
 <span data-ttu-id="3de5e-150">Formatters belirten işlem davranışları benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="3de5e-151">Bu tür davranışlardan biri, her işlem için varsayılan olarak, gerekli işlemi oluşturmak için her zaman uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="3de5e-152">Ancak, bu davranışlar sadece başka bir işlem davranışı gibi görünür; başka bir öznitelik tarafından tanımlanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="3de5e-153">Bir yedek davranış yüklemek için, uygulama varsayılan olarak WCF türü yükleyici tarafından yüklenen belirli madde davranışları aramak gerekir ve ya değiştirmek ya da varsayılan davranış tan sonra çalıştırmak için uyumlu bir davranış eklemek.</span><span class="sxs-lookup"><span data-stu-id="3de5e-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="3de5e-154">Bu işlem formatters davranışları çağırmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> önce veya varsayılan bir sonra yürütülen bir işlem davranışı belirterek programlı olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="3de5e-155">Ancak, davranış modeli bir davranışın diğer davranışları değiştirmesine veya açıklama ağacını başka bir şekilde değiştirmesine izin vermedığından, bir bitiş noktası davranışı (ve bu nedenle yapılandırma) tarafından kolayca ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="3de5e-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="3de5e-156">İstemci üzerinde:</span><span class="sxs-lookup"><span data-stu-id="3de5e-156">On the client:</span></span>  
  
 <span data-ttu-id="3de5e-157">Uygulama, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> istekleri HTTP GET isteklerine dönüştürebilmek ve yanıtlar için orijinal maddeye temsilci olarak uygulayabilmesi için uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="3de5e-158">Bu `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi çağırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="3de5e-159">Bu aramadan `CreateChannel`önce yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-159">This must be done before calling `CreateChannel`.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="3de5e-160">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="3de5e-160">On the server:</span></span>  
  
- <span data-ttu-id="3de5e-161">Arayüz, <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> HTTP GET isteklerini okuyabilmesi ve yanıt ları yazmak için orijinal formatter'a temsilci olarak uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="3de5e-162">Bu, istemciyle aynı `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi ni arayarak yapılır (önceki kod örneğine bakın).</span><span class="sxs-lookup"><span data-stu-id="3de5e-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="3de5e-163">Bu çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> önce yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="3de5e-164">Bu örnekte, formatter'ı aramadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce el ile nasıl değiştirildiğini gösteririz.</span><span class="sxs-lookup"><span data-stu-id="3de5e-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="3de5e-165">Aynı şeyi elde etmenin başka bir yolu <xref:System.ServiceModel.ServiceHost> da, açmadan `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` önce aramaları yapan bir sınıf elde etmektir (lütfen örnekler için barındırma belgelerine ve örneklerine bakın).</span><span class="sxs-lookup"><span data-stu-id="3de5e-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="3de5e-166">Kullanıcı deneyimleri</span><span class="sxs-lookup"><span data-stu-id="3de5e-166">User experience</span></span>  
 <span data-ttu-id="3de5e-167">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="3de5e-167">On the server:</span></span>  
  
- <span data-ttu-id="3de5e-168">Sunucu `ICalculator` uygulamasının değişmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3de5e-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="3de5e-169">Hizmet için App.config `messageVersion` `textMessageEncoding` öğenin özniteliğini ayarlayan özel bir POX bağlama kullanmanız `None`gerekir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
- <span data-ttu-id="3de5e-170">Hizmet için App.config de davranış `EnableHttpGetRequestsBehavior` uzantıları bölümüne ekleyerek ve kullanarak özel belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
- <span data-ttu-id="3de5e-171">Aramadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>önce işlem formatters ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3de5e-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="3de5e-172">İstemci üzerinde:</span><span class="sxs-lookup"><span data-stu-id="3de5e-172">On the client:</span></span>  
  
- <span data-ttu-id="3de5e-173">İstemci uygulamasının değişmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3de5e-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="3de5e-174">İstemci için `messageVersion` `textMessageEncoding` App.config, öğenin özniteliğini ayarlayan özel `None`bir POX bağlama sı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="3de5e-175">Hizmetten bir fark, giden To adresinin değiştirilebilmesini sağlamak için istemcinin el ile ele alınmasını sağlaması dır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
- <span data-ttu-id="3de5e-176">İstemci için App.config sunucu `EnableHttpGetRequestsBehavior` ile aynı özel belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="3de5e-177">Aramadan <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>önce işlem formatters ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3de5e-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="3de5e-178">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3de5e-179">Dört işlem (Ekle, Çıkar, Çarp ve Böl) başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3de5e-180">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="3de5e-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3de5e-181">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3de5e-181">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3de5e-182">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="3de5e-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3de5e-183">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3de5e-183">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3de5e-184">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3de5e-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3de5e-185">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="3de5e-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3de5e-186">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3de5e-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3de5e-187">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3de5e-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
