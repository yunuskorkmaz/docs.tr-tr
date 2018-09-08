---
title: İşlem Biçimlendirici ve İşlem Seçici
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189942"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="06abc-102">İşlem Biçimlendirici ve İşlem Seçici</span><span class="sxs-lookup"><span data-stu-id="06abc-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="06abc-103">Bu örnek ileti verilerini ne WCF bekliyor farklı bir biçimde izin vermek için Windows Communication Foundation (WCF) genişletilebilirlik noktaları'nın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06abc-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="06abc-104">Varsayılan olarak, WCF biçimlendiricileri altında dahil edilecek yöntem parametreleri beklediğiniz `soap:body` öğesi.</span><span class="sxs-lookup"><span data-stu-id="06abc-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="06abc-105">Örnek uygulama, bunun yerine bir HTTP GET sorgu dizesi parametresi verileri ayrıştırır ve bu verileri kullanarak yöntemleri çağıran bir özel işlem biçimlendirici gösterir.</span><span class="sxs-lookup"><span data-stu-id="06abc-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="06abc-106">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="06abc-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="06abc-107">Bunu nasıl gösterir ekleme, çıkarma, birden çok kez ve bölme iletileri, istemci-sunucu isteği için HTTP GET kullanmak için değiştirilebilir ve POX ile HTTP POST için sunucu istemciye yanıt iletileri.</span><span class="sxs-lookup"><span data-stu-id="06abc-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="06abc-108">Bunu yapmak için örnek aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="06abc-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="06abc-109">`QueryStringFormatter`, uygulayan <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> istemci ve sunucu için sırasıyla ve sorgu dizesi verileri işler.</span><span class="sxs-lookup"><span data-stu-id="06abc-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="06abc-110">`UriOperationSelector`, uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> GET isteği işlem adına göre işlem gönderme gerçekleştirmek için sunucu üzerinde.</span><span class="sxs-lookup"><span data-stu-id="06abc-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="06abc-111">`EnableHttpGetRequestsBehavior` uç nokta davranışı (ve karşılık gelen yapılandırma), çalışma zamanı için gerekli işlem Seçici ekler.</span><span class="sxs-lookup"><span data-stu-id="06abc-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="06abc-112">Yeni bir işlem biçimlendirici çalışma zamanına nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06abc-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="06abc-113">Bu örnekte, hem istemci hem de hizmet Konsolu (.exe) uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="06abc-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06abc-114">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="06abc-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="06abc-115">Temel Kavramlar</span><span class="sxs-lookup"><span data-stu-id="06abc-115">Key Concepts</span></span>  
 <span data-ttu-id="06abc-116">`QueryStringFormatter` -İşlem biçimlendirici parametresi nesnelerinin bir dizisi ve bir iletiye parametresi nesneleri içeren bir dizi ileti oluşturmaktan sorumludur wcf'de bileşendir.</span><span class="sxs-lookup"><span data-stu-id="06abc-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="06abc-117">Bu istemciyi kullanarak gerçekleştirilir <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> arabirimi hem de sunucu ile <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="06abc-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="06abc-118">Bu arabirimler, istek ve yanıt iletilerin alınacağı açabileceğinizi `Serialize` ve `Deserialize` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="06abc-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="06abc-119">Bu örnekte `QueryStringFormatter` hem de bu arabirimleri uygulayan ve istemci ve sunucu üzerinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="06abc-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="06abc-120">İstek:</span><span class="sxs-lookup"><span data-stu-id="06abc-120">Request:</span></span>  
  
-   <span data-ttu-id="06abc-121">Örnek kullanır <xref:System.ComponentModel.TypeConverter> dizeleri gelen ve giden istek iletisi parametre verileri dönüştürmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="06abc-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="06abc-122">Varsa bir <xref:System.ComponentModel.TypeConverter> örnek biçimlendirici oluşturur bir özel durumu belirli bir tür için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06abc-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="06abc-123">İçinde `IClientMessageFormatter.SerializeRequest` istemcisinde, biçimlendirici yöntemi adresi uygun bir URI oluşturur ve işlem adı soneki olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="06abc-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="06abc-124">Bu ad, sunucudaki uygun işlemini gönderileceği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06abc-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="06abc-125">Ardından parametresi nesneleri dizisi alır ve parametre adları ve dönüştürülen değerler kullanarak URI sorgu dizesi parametresi verileri serileştirir <xref:System.ComponentModel.TypeConverter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06abc-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="06abc-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Ve <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> özellikleri daha sonra bu URI'ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06abc-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="06abc-127"><xref:System.ServiceModel.Channels.MessageProperties> üzerinden erişilen <xref:System.ServiceModel.Channels.Message.Properties%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="06abc-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="06abc-128">İçinde `IDispatchMessageFormatter.DeserializeRequest` yöntemi sunucuda biçimlendiriciyi alır `Via` gelen istek ileti özelliklerinde bir URI.</span><span class="sxs-lookup"><span data-stu-id="06abc-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="06abc-129">Ad-değer çiftlerini URI sorgu dizesinde, parametre adları ve değerlerine ayrıştırır ve parametre adları ve değerleri, yönteme geçirilen parametreler dizisi doldurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="06abc-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="06abc-130">Bu yöntemde işlem adı soneki göz ardı edilir şekilde gönderme işlemi zaten oluştu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06abc-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="06abc-131">Yanıt:</span><span class="sxs-lookup"><span data-stu-id="06abc-131">Response:</span></span>  
  
-   <span data-ttu-id="06abc-132">Bu örnekte, HTTP GET isteği yalnızca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06abc-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="06abc-133">Biçimlendirici bir XML iletisi oluşturmak için kullanılanla özgün biçimlendirici yanıtı gönderen atar.</span><span class="sxs-lookup"><span data-stu-id="06abc-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="06abc-134">Bu örnek hedeflerinden temsilci bir biçimlendirici nasıl uygulanabileceği göstermektir.</span><span class="sxs-lookup"><span data-stu-id="06abc-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="06abc-135">UriPathSuffixOperationSelector sınıfı</span><span class="sxs-lookup"><span data-stu-id="06abc-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="06abc-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Arabirimi kullanıcıların kendi mantığını hangi işlem için belirli bir ileti gönderilen sağlar.</span><span class="sxs-lookup"><span data-stu-id="06abc-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="06abc-137">Bu örnekte `UriPathSuffixOperationSelector` işlem adı bir eylem üst bilgi iletisi yerine HTTP almak URI'ye dahil olduğundan uygun işlemi seçmek için sunucuda uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06abc-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="06abc-138">Örnek yalnızca büyük küçük harf duyarsız işlem adları izin verecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="06abc-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="06abc-139">`SelectOperation` Yöntemi gelen iletiyi alır ve şuna `Via` ileti özelliklerinde bir URI.</span><span class="sxs-lookup"><span data-stu-id="06abc-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="06abc-140">İşlem adı soneki URI'SİNDEN ayıklar, ileti için dağıtılması işlem adını almak için iç tablo arar ve bu işlem adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="06abc-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="06abc-141">EnableHttpGetRequestsBehavior sınıfı</span><span class="sxs-lookup"><span data-stu-id="06abc-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="06abc-142">`UriPathSuffixOperationSelector` Bileşen ayarlanabilir programlı olarak veya bir uç nokta davranışı.</span><span class="sxs-lookup"><span data-stu-id="06abc-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="06abc-143">Örnek uygulayan `EnableHttpGetRequestsBehavior` hizmetin uygulama yapılandırma dosyasında belirtilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="06abc-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="06abc-144">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="06abc-144">On the server:</span></span>  
  
 <span data-ttu-id="06abc-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ayarlanır <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="06abc-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="06abc-146">Varsayılan olarak, bir tam eşleşme adresi filtresi WCF kullanır.</span><span class="sxs-lookup"><span data-stu-id="06abc-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="06abc-147">Gelen ileti URİ'SİNDE parametre verisi içeren bir sorgu dize tarafından izlenen bir işlem adı soneki içeriyor, uç nokta davranışı olmasını adresi filtresi de değişiklikler filtresi eşleşen bir önek.</span><span class="sxs-lookup"><span data-stu-id="06abc-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="06abc-148">WCF kullanan<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="06abc-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="06abc-149">Yükleme işlemi biçimlendiricileri</span><span class="sxs-lookup"><span data-stu-id="06abc-149">Installing operation formatters</span></span>  
 <span data-ttu-id="06abc-150">Biçimlendiricileri belirtin işlem davranışları benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="06abc-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="06abc-151">Böyle bir davranış, her zaman gerekli işlem biçimlendirici oluşturmak her işlem için varsayılan olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="06abc-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="06abc-152">Ancak, bu davranışlar gibi başka bir işlem davranışı arar; Bunlar herhangi bir öznitelik tarafından tanımlanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="06abc-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="06abc-153">Değiştirme davranışı yüklemek için uygulama varsayılan ve ya da WCF türü yükleyicisi tarafından yüklenen belirli biçimlendirici davranışları değiştirmek arayın veya sonra varsayılan davranış çalıştırmak için uyumlu bir davranış ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06abc-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="06abc-154">Bu işlem biçimlendiricileri davranışların çağırmadan önce programlama yoluyla ayarlanabilir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> veya varsayılan bir sonra yürütülecek olan bir işlemi davranışı belirterek.</span><span class="sxs-lookup"><span data-stu-id="06abc-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="06abc-155">Ancak, bunu kolayca bir uç nokta davranışı ayarlanamıyor (ve bu nedenle yapılandırmaya göre) davranış modeli davranışları değiştirin veya aksi halde açıklama ağaç değiştirmek bir davranış izin vermediğinden.</span><span class="sxs-lookup"><span data-stu-id="06abc-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="06abc-156">İstemcide:</span><span class="sxs-lookup"><span data-stu-id="06abc-156">On the client:</span></span>  
  
 <span data-ttu-id="06abc-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Uygulama uygulanmalı, böylece istekler HTTP GET isteklerine dönüştüren ve yanıtlarının özgün biçimlendirici için temsilci.</span><span class="sxs-lookup"><span data-stu-id="06abc-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="06abc-158">Bu çağrılarak gerçekleştirilir `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06abc-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="06abc-159">Bu çağırmadan önce yapılmalıdır `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="06abc-159">This must be done before calling `CreateChannel`.</span></span>  
  
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
  
 <span data-ttu-id="06abc-160">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="06abc-160">On the server:</span></span>  
  
-   <span data-ttu-id="06abc-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Arabirimi uygulanmalı okuma HTTP GET istekleri ve yanıtları yazmak için temsilci seçme için özgün biçimlendirici.</span><span class="sxs-lookup"><span data-stu-id="06abc-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="06abc-162">Bu aynı çağrılarak gerçekleştirilir `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` yardımcı yöntemi istemci olarak (Yukarıdaki örnek kod bakın).</span><span class="sxs-lookup"><span data-stu-id="06abc-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="06abc-163">Bu, önce yapılmalıdır <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="06abc-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="06abc-164">Bu örnekte, biçimlendirici çağırmadan önce el ile nasıl değiştirilmiş olan göstereceğiz <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="06abc-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="06abc-165">Öğesinden bir sınıf türetmek için aynı şeyi elde etmek için başka bir yolu olan <xref:System.ServiceModel.ServiceHost> çağrıları yapar `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` açmadan önce (belgeler ve örnekler için örnekleri barındırma Lütfen bakın).</span><span class="sxs-lookup"><span data-stu-id="06abc-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="06abc-166">Kullanıcı deneyimleri</span><span class="sxs-lookup"><span data-stu-id="06abc-166">User experience</span></span>  
 <span data-ttu-id="06abc-167">Sunucuda:</span><span class="sxs-lookup"><span data-stu-id="06abc-167">On the server:</span></span>  
  
-   <span data-ttu-id="06abc-168">Sunucu `ICalculator` uygulama değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="06abc-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="06abc-169">App.config hizmeti için özel ayarlar bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`.</span><span class="sxs-lookup"><span data-stu-id="06abc-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
-   <span data-ttu-id="06abc-170">App.config hizmeti için özel de belirtmeniz gerekir `EnableHttpGetRequestsBehavior` davranış Uzantıları bölümüne ekleyerek ve onu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="06abc-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
-   <span data-ttu-id="06abc-171">Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="06abc-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="06abc-172">İstemcide:</span><span class="sxs-lookup"><span data-stu-id="06abc-172">On the client:</span></span>  
  
-   <span data-ttu-id="06abc-173">İstemci uygulaması değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="06abc-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="06abc-174">İstemcisi için App.config ayarlar özel bir POX bağlama kullanmalısınız `messageVersion` özniteliği `textMessageEncoding` öğesine `None`.</span><span class="sxs-lookup"><span data-stu-id="06abc-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="06abc-175">Bir hizmetten istemci adresine giden değiştirilebilir böylece, el ile adresleme etkinleştirmelisiniz farktır.</span><span class="sxs-lookup"><span data-stu-id="06abc-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
-   <span data-ttu-id="06abc-176">App.config istemci için aynı özel belirtmelisiniz `EnableHttpGetRequestsBehavior` sunucusu.</span><span class="sxs-lookup"><span data-stu-id="06abc-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="06abc-177">Ekleme işlemi biçimlendiricileri çağırmadan önce <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="06abc-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="06abc-178">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06abc-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="06abc-179">Tüm dört işlemleri (ekleme, çıkarma, çarpma ve bölme) başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06abc-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06abc-180">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="06abc-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06abc-181">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="06abc-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06abc-182">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="06abc-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06abc-183">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="06abc-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06abc-184">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="06abc-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06abc-185">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06abc-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="06abc-186">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06abc-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="06abc-187">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06abc-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06abc-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06abc-188">See Also</span></span>
