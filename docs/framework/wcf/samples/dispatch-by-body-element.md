---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 58d505770a495e5e423104b9fb912d088ca56f86
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143167"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="b7af3-102">Gövde Öğesine göre Dağıt</span><span class="sxs-lookup"><span data-stu-id="b7af3-102">Dispatch by Body Element</span></span>
<span data-ttu-id="b7af3-103">Bu örnek nasıl gelen iletiler için işlemler atamak için başka bir algoritma uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="b7af3-104">Varsayılan olarak, hizmet modeli dağıtıcı iletinin WS-Addressing üzerinde temel gelen ileti için uygun işleme yöntemi seçer "Action" üst bilgi veya HTTP SOAP isteğinin eşdeğer bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b7af3-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="b7af3-105">WS izlemeyin yığınları bazı SOAP 1.1 Web Hizmetleri-ı Basic Profile 1.1 yönergeleri eylem URİ'SİNDE dayalı ancak bunun yerine SOAP gövdesi içindeki ilk öğeyi XML tam adı temel iletileri gönderme değil.</span><span class="sxs-lookup"><span data-stu-id="b7af3-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="b7af3-106">Benzer şekilde, istemci tarafı bu yığınlarının SOAP 1.1 belirtiminde verilmişti bir boş veya rastgele HTTP SoapAction başlık iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="b7af3-107">Yöntemlere iletileri gönderilen şeklini değiştirmek için örnek uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> genişletilebilirlik arabirimdeki `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="b7af3-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="b7af3-108">Bu sınıf operations ileti gövdesinin ilk öğeye göre seçer.</span><span class="sxs-lookup"><span data-stu-id="b7af3-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="b7af3-109">Sınıf oluşturucu çiftleri ile doldurulmuş bir sözlük bekliyor `XmlQualifiedName` ve dizeler yapabildiği nitelenmiş adlar SOAP gövdesi ilk alt adını belirtmek ve dizeleri eşleşen işlem adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7af3-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="b7af3-110">`defaultOperationName` Karşı bu sözlük eşleşen tüm iletiler alan işlem adıdır:</span><span class="sxs-lookup"><span data-stu-id="b7af3-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <span data-ttu-id="b7af3-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulamalarıdır arabirimde yalnızca bir yöntem olarak oluşturmak çok basittir: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="b7af3-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="b7af3-112">Bu yöntemin işi, bir gelen iletiyi incelemek ve geçerli uç nokta hizmet sözleşmesindeki yöntemin adı eşittir bir dize döndürecek şekilde silinir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="b7af3-113">Bu örnekte, işlem Seçici edinme bir <xref:System.Xml.XmlDictionaryReader> gelen ileti gövdesi kullanarak kullanıcının <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="b7af3-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="b7af3-114">Geçerli öğenin adını ve ad alanı URI almak ve bunları birleştirmek yeterlidir, böylece bu yöntem okuyucu zaten ileti gövdesinin ilk alt yerleştirir. bir `XmlQualifiedName` ardından kullanılan karşılık gelen işlemi bakmak işlem Seçici tarafından tutulan sözlüğü.</span><span class="sxs-lookup"><span data-stu-id="b7af3-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="b7af3-115">İleti gövdesi ile erişme <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> veya iletinin gövdesi içeriğe erişim neden olan iletiyi bir daha ayrıntılı işleme için geçersiz olduğu anlamına gelir "okundu" olarak işaretlenecek iletinin sağlayan diğer yöntemlerden herhangi birini.</span><span class="sxs-lookup"><span data-stu-id="b7af3-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="b7af3-116">Bu nedenle, işlem Seçici, aşağıdaki kodda gösterilen yöntemi ile gelen iletinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7af3-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="b7af3-117">Okuyucunun konumu denetim turu sırasında değiştirilmediğinden olduğundan, özgün iletinin tam bir kopyası sonuçları yeni oluşturulan ileti için ileti özelliklerinde ve ileti üst da kopyalanır, tarafından başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="b7af3-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```csharp
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="b7af3-118">Bir işlem Seçici için bir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="b7af3-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="b7af3-119">Hizmet dağıtma işlemi Seçici Windows Communication Foundation (WCF) dağıtıcısı uzantılarıdır.</span><span class="sxs-lookup"><span data-stu-id="b7af3-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="b7af3-120">Çift yönlü sözleşmeler geri çağırma kanalı yöntemlerini seçmek için de vardır çok gönderme işlemi Seçici burada açıklanan, ancak bu açıkça Bu örnekte kapsanmaz iş istemci işlemi seçicileri.</span><span class="sxs-lookup"><span data-stu-id="b7af3-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="b7af3-121">Çoğu hizmet modeli uzantıları gibi gönderme işlemi Seçici davranışları dağıtıcı eklenir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="b7af3-122">A *davranışı* gönderme çalışma zamanı (veya istemci çalışma zamanı) bir veya daha fazla uzantıları ekler ya da aksi takdirde ayarlarını değiştirir yapılandırma nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b7af3-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="b7af3-123">İşlem Seçici anlaşması kapsamında olduğundan, burada uygulamak için uygun bir davranıştır <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b7af3-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="b7af3-124">Arabirim üzerinde uygulandığından bir <xref:System.Attribute> türetilmiş sınıf aşağıdaki kodda gösterildiği gibi davranışı bildirimli olarak bir hizmet sözleşmeye eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="b7af3-125">Her bir <xref:System.ServiceModel.ServiceHost> açılır ve gönderme çalışma zamanı oluşturulmuştur, tüm davranışları sözleşmeleri, işlemler ve hizmet uygulamaları özniteliklerinde olarak veya hizmet yapılandırma öğesi olarak otomatik olarak eklenir ve daha sonra istenir bulunamadı Uzantıları katkıda bulunan veya varsayılan yapılandırmayı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7af3-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="b7af3-126">Konuyu uzatmamak amacıyla, aşağıdaki kod alıntı yöntemin uygulanmasını yalnızca gösterir <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, hangi etkiler yapılandırma değişikliklerini bu dağıtıcı için.</span><span class="sxs-lookup"><span data-stu-id="b7af3-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="b7af3-127">Bunlar herhangi bir iş yapmadan çağırana döndürmesi için diğer yöntemler gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="b7af3-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="b7af3-128">İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> işlem Seçici arama Sözlüğü'kurmak ayarlar üzerinden yineleme tarafından uygulama <xref:System.ServiceModel.Description.OperationDescription> service uç noktasının öğelerinde <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="b7af3-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="b7af3-129">Her bir işlem açıklaması varlığını ardından inceledi `DispatchBodyElementAttribute` davranışı, uygulaması <xref:System.ServiceModel.Description.IOperationBehavior> Ayrıca bu örnekte tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="b7af3-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="b7af3-130">Bu sınıf bir davranış da olsa da, pasif ve etkin bir şekilde gönderme çalışma zamanı yapılandırma değişiklikleri gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="b7af3-131">Tüm yöntemleri, çağırana tüm eylemleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7af3-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="b7af3-132">Böylece meta veriler için bir işlem seçildiğinde, oluşumunu ile ilgili işlemler ilişkilendirilebilir yeni dağıtım mekanizması, yani body öğesi üzerinde tam adı gerekli işlemi davranış yalnızca bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7af3-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="b7af3-133">Böyle bir davranış bulunursa, değer çifti oluşturulan XML tam adı (`QName` özelliği) ve işlem adı (`Name` özelliği) sözlüğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="b7af3-134">Sözlük, yeni bir doldurulduktan sonra `DispatchByBodyElementOperationSelector` bu bilgilerle oluşturulur ve gönderme zamanının işlem Seçici ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b7af3-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="b7af3-135">Uygulama hizmeti</span><span class="sxs-lookup"><span data-stu-id="b7af3-135">Implementing the Service</span></span>  
 <span data-ttu-id="b7af3-136">Bu örnekte doğrudan uygulanan davranışını nasıl kablo iletilerden yorumlanır ve gönderilen, hizmet sözleşmesinin bir işlev olan etkiler.</span><span class="sxs-lookup"><span data-stu-id="b7af3-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="b7af3-137">Sonuç olarak, davranışı kullanmak için seçtiği herhangi bir hizmet uygulaması, hizmet sözleşmesi düzeyinde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="b7af3-138">Örnek Proje hizmeti geçerli `DispatchByBodyElementBehaviorAttribute` sözleşme davranışa `IDispatchedByBody` hizmet sözleşmesi ve etiketleri her iki işlem `OperationForBodyA()` ve `OperationForBodyB()` ile bir `DispatchBodyElementAttribute` işlemi davranışı.</span><span class="sxs-lookup"><span data-stu-id="b7af3-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="b7af3-139">Bu sözleşme uygulayan bir hizmet için bir hizmet konağı açık olduğunda bu meta veriler daha önce anlatıldığı dağıtıcı oluşturucusu tarafından seçilir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="b7af3-140">İşlem Seçici ileti gövdesi öğesinde yalnızca temel gönderir ve "Action" yoksayar olduğundan, döndürülen yanıtı "Action" başlığındaki joker atayarak denetlemek için çalışma zamanı bildirmek için gereklidir "\*" için `ReplyAction` özelliği <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b7af3-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="b7af3-141">Ayrıca, "Action" özelliği için joker karakter olarak ayarlanmış bir varsayılan işlemi için gerekli olan "\*".</span><span class="sxs-lookup"><span data-stu-id="b7af3-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="b7af3-142">Varsayılan işlemi dağıtılamaz ve olmayan tüm iletiler alan bir `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="b7af3-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="b7af3-143">Örnek hizmet uygulaması oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="b7af3-144">Her yöntem alınan ileti bir yanıt iletisi sarmalar ve istemciye geri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="b7af3-145">Çalıştıran ve örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7af3-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="b7af3-146">Örneği çalıştırdığınızda, işlem yanıt gövdesi içeriğini (biçimlendirilmiş) aşağıdaki çıktıya benzer bir istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7af3-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="b7af3-147">İstemci hizmete üç iletileri, gövde öğesi adlandırılan içerik gönderir. `bodyA`, `bodyB`, ve `bodyX`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="b7af3-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="b7af3-148">Önceki Açıklama ve gösterilen hizmet sözleşmesini ertelenmiş olarak gelen ileti ile `bodyA` öğesi tekrarlanarak gönderilen `OperationForBodyA()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7af3-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="b7af3-149">İleti için hiçbir açık gönderim hedefi olduğundan `bodyX` body öğesi ileti gönderilen için `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="b7af3-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="b7af3-150">Her hizmet işlemleri yöntemi belirli bir öğenin içine alınan ileti gövdesi sarmalar ve, giriş ilişkilendirin ve bu örnek için açıkça iletileri çıkış yapılır döndürür:</span><span class="sxs-lookup"><span data-stu-id="b7af3-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7af3-151">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b7af3-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b7af3-152">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7af3-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b7af3-153">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7af3-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b7af3-154">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7af3-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7af3-155">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b7af3-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7af3-156">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b7af3-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b7af3-157">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b7af3-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7af3-158">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b7af3-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="b7af3-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7af3-159">See Also</span></span>
