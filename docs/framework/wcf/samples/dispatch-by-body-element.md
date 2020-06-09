---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 19913cdaa47d766f62a313e216a653ac69633a99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594705"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="9c5fb-102">Gövde Öğesine göre Dağıt</span><span class="sxs-lookup"><span data-stu-id="9c5fb-102">Dispatch by Body Element</span></span>
<span data-ttu-id="9c5fb-103">Bu örnek, işlemler için gelen iletileri atamaya yönelik alternatif algoritmanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="9c5fb-104">Varsayılan olarak, hizmet modeli dağıtıcısı iletinin WS-Addressing "Action" başlığına veya HTTP SOAP isteğindeki eşdeğer bilgilere göre gelen bir ileti için uygun işleme yöntemini seçer.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="9c5fb-105">WS-ı temel 1,1 profilini izleyen bazı SOAP 1,1 Web Hizmetleri yığınları, Işlem URI 'sine bağlı olarak ileti göndermez, bunun yerine SOAP gövdesinin içindeki ilk öğenin XML nitelenmiş adına göre.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="9c5fb-106">Benzer şekilde, bu yığınların istemci tarafı, SOAP 1,1 belirtiminin izin verdiği boş veya rastgele bir HTTP SoapAction üst bilgisine sahip iletiler gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="9c5fb-107">İletilerin yöntemlere nasıl dağıtıldığı şeklini değiştirmek için örnek <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> üzerinde genişletilebilirlik arabirimini uygular `DispatchByBodyElementOperationSelector` .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="9c5fb-108">Bu sınıf, ileti gövdesinin ilk öğesine göre işlemleri seçer.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="9c5fb-109">Sınıf oluşturucusu, ve dizeleri çiftleriyle doldurulmuş bir sözlük bekler `XmlQualifiedName` ve nitelenmiş adların, SOAP gövdesinin ilk alt öğesinin adını ve dizeler eşleşen işlem adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="9c5fb-110">, `defaultOperationName` Bu sözlükte eşleştirilemez tüm iletileri alan işlemin adıdır:</span><span class="sxs-lookup"><span data-stu-id="9c5fb-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="9c5fb-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>arabirim üzerinde yalnızca bir yöntem olduğundan, uygulamalar derleme için oldukça basittir: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="9c5fb-112">Bu yöntemin işi, gelen bir iletiyi incelemek ve geçerli uç nokta için hizmet sözleşmesindeki bir yöntemin adına eşit olan bir dize döndürmek içindir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="9c5fb-113">Bu örnekte, işlem Seçici, <xref:System.Xml.XmlDictionaryReader> kullanarak gelen iletinin gövdesini alır <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="9c5fb-114">Bu yöntem, geçerli öğenin adı ve ad alanı URI 'sini almak için yeterli olması ve `XmlQualifiedName` daha sonra işlem seçicisine sahip olan sözlükten karşılık gelen işlemi aramak için kullanılan bir ' a birleştirmek üzere ileti gövdesinin ilk alt öğesi üzerindeki okuyucuyu zaten konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="9c5fb-115">İleti gövdesine <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> veya iletinin gövde içeriğine erişim sağlayan diğer yöntemlerden birine erişmek iletinin "okuma" olarak işaretlenmesine neden olur, bu da iletinin daha fazla işlem için geçersiz olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="9c5fb-116">Bu nedenle, işlem Seçicisi aşağıdaki kodda gösterilen yöntemiyle gelen iletinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="9c5fb-117">İnceleme sırasında okuyucunun konumu değişmediğinden, ileti özelliklerinin ve ileti üstbilgilerinin de kopyalandığı yeni oluşturulan ileti tarafından başvuru yapılabilir ve bu durum özgün iletinin tam bir kopyasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="9c5fb-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="9c5fb-118">Bir hizmete Işlem seçici ekleme</span><span class="sxs-lookup"><span data-stu-id="9c5fb-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="9c5fb-119">Hizmet gönderme işlemi seçicileri Windows Communication Foundation (WCF) dağıtıcısına yönelik uzantılardır.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="9c5fb-120">Çift yönlü sözleşmelerin geri çağırma kanalında Yöntemler seçmek için, burada açıklanan gönderme işlemi seçicileri gibi çok daha fazla çalışan ancak bu örnekte açıkça kapsanmayan istemci işlem seçicileri de vardır.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="9c5fb-121">Çoğu hizmet modeli uzantısı gibi, dağıtım işlemi seçicileri, davranışlar kullanılarak dağıtıcıya eklenir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="9c5fb-122">*Davranış* , dağıtım çalışma zamanına (veya istemci çalışma zamanına) bir veya daha fazla uzantı ekleyen veya ayarlarını değiştiren bir yapılandırma nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="9c5fb-123">İşlem seçicileri sözleşme kapsamı içerdiğinden, burada uygulanacak uygun davranış ' dır <xref:System.ServiceModel.Description.IContractBehavior> .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="9c5fb-124"><xref:System.Attribute>Aşağıdaki kodda gösterildiği gibi arabirim türetilmiş bir sınıfta uygulandığından, davranış herhangi bir hizmet sözleşmesine bildirimli olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="9c5fb-125">Her <xref:System.ServiceModel.ServiceHost> açıldığında ve dağıtım çalışma zamanı yapılandırıldığında, sözleşmeler, işlemler ve hizmet uygulamalarında öznitelik olarak bulunan veya hizmet yapılandırmasındaki öğe olarak bulunan tüm davranışlar otomatik olarak eklenir ve daha sonra uzantılara katkıda bulunmak veya varsayılan yapılandırmayı değiştirmek isteyip istemediğiniz sorulur.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="9c5fb-126">Kısaltma için aşağıdaki kod alıntısı yalnızca yönteminin uygulanmasını gösterir <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> ve bu örnekteki dağıtıcı için yapılandırma değişikliklerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="9c5fb-127">Diğer yöntemler, hiçbir iş yapmadan arayan tarafa döntiğinden gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="9c5fb-128">İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> uygulama, <xref:System.ServiceModel.Description.OperationDescription> hizmet uç noktasındaki öğeler üzerinde yineleme yaparak, işlem seçicisinin arama sözlüğünü ayarlar <xref:System.ServiceModel.Description.ContractDescription> .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="9c5fb-129">Ardından, her işlem açıklaması davranışın varlığı için incelenir `DispatchBodyElementAttribute` , <xref:System.ServiceModel.Description.IOperationBehavior> Bu örnekte de bir uygulama da tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="9c5fb-130">Bu sınıf aynı zamanda bir davranış olsa da pasif olur ve dağıtım çalışma zamanında hiçbir yapılandırma değişikliğini etkin bir şekilde katkıda bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="9c5fb-131">Tüm yöntemleri herhangi bir eylem yapmadan çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="9c5fb-132">İşlem davranışı yalnızca yeni dağıtım mekanizması için gerekli olan meta verilerin, yani örneğin bir işlem yerine geçen gövde öğesinin tam adı seçildiğinde ilgili işlemlerle ilişkilendirilebilen şekilde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="9c5fb-133">Böyle bir davranış bulunursa, XML nitelenmiş adından ( `QName` özellik) ve işlem adından (özellik) oluşturulan bir değer çifti `Name` sözlüğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="9c5fb-134">Sözlük doldurulduktan sonra, `DispatchByBodyElementOperationSelector` Bu bilgilerle yeni bir oluşturulur ve dağıtım çalışma zamanının işlem Seçicisi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="9c5fb-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="9c5fb-135">Hizmeti uygulama</span><span class="sxs-lookup"><span data-stu-id="9c5fb-135">Implementing the Service</span></span>  
 <span data-ttu-id="9c5fb-136">Bu örnekte uygulanan davranış, hizmet sözleşmesinin bir işlevi olan, iletişimdeki iletilerin nasıl yorumlandığını ve yapıldığını doğrudan etkiler.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="9c5fb-137">Sonuç olarak, davranışı kullanmayı seçen hizmet uygulamalarında hizmet sözleşmesi düzeyinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="9c5fb-138">Örnek proje hizmeti, `DispatchByBodyElementBehaviorAttribute` sözleşme davranışını `IDispatchedByBody` hizmet sözleşmesine uygular ve iki işlemin her birini `OperationForBodyA()` ve `OperationForBodyB()` bir `DispatchBodyElementAttribute` işlem davranışını Etiketler.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="9c5fb-139">Bu sözleşmeyi uygulayan bir hizmetin hizmet ana bilgisayarı açıldığında, bu meta veriler, daha önce açıklandığı gibi dağıtıcı Oluşturucusu tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="9c5fb-140">İşlem Seçici yalnızca ileti gövdesi öğesine bağlı olarak ve "eylem" öğesini yok saydığından, çalışma zamanına "\*" joker karakterini ' a atayarak döndürülen yanıtlara "eylem" üstbilgisini denetlemesinin söylemek gerekir `ReplyAction` <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="9c5fb-141">Ayrıca, "" joker karakterine ayarlanmış "Action" özelliği olan bir varsayılan işlem olması gerekir \* .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="9c5fb-142">Varsayılan işlem, iletilemez ve ' a sahip olmayan tüm iletileri alır `DispatchBodyElementAttribute` :</span><span class="sxs-lookup"><span data-stu-id="9c5fb-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="9c5fb-143">Örnek hizmet uygulamasının kullanımı basittir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="9c5fb-144">Her yöntem alınan iletiyi bir yanıt iletisine sarar ve istemciye geri bildirir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="9c5fb-145">Örnek çalıştırma ve oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c5fb-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="9c5fb-146">Örneği çalıştırdığınızda, işlem yanıtlarının gövde içeriği, istemci konsolu penceresinde aşağıdaki (biçimlendirilen) çıktıya benzer şekilde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="9c5fb-147">İstemci, gövde içeriği öğesi `bodyA` sırasıyla,, ve olarak adlandırılan hizmete üç ileti gönderir `bodyB` `bodyX` .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="9c5fb-148">Önceki açıklamadan ve hizmet sözleşmesinden ertelenebilir, öğesine sahip gelen ileti `bodyA` `OperationForBodyA()` yöntemine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="9c5fb-149">Gövde öğesi olan ileti için açık bir dağıtım hedefi olmadığından `bodyX` ileti öğesine gönderilir `DefaultOperation()` .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="9c5fb-150">Hizmet işlemlerinin her biri, alınan ileti gövdesini yönteme özel bir öğeye sarar ve bu örnek için giriş ve çıkış iletilerini açıkça ilişkilendirmek için yapılır.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9c5fb-151">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9c5fb-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9c5fb-152">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9c5fb-153">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9c5fb-154">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9c5fb-155">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c5fb-156">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9c5fb-157">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9c5fb-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c5fb-158">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9c5fb-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
