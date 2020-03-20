---
title: Gövde Öğesine göre Dağıt
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183720"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="6f528-102">Gövde Öğesine göre Dağıt</span><span class="sxs-lookup"><span data-stu-id="6f528-102">Dispatch by Body Element</span></span>
<span data-ttu-id="6f528-103">Bu örnek, gelen iletileri işlemlere atamak için alternatif bir algoritmanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f528-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="6f528-104">Varsayılan olarak, hizmet modeli gönderici, iletinin WS Adresleme "Eylem" üstbilgisini veya HTTP SOAP isteğindeki eşdeğer bilgileri temel alan gelen ileti için uygun işleme yöntemini seçer.</span><span class="sxs-lookup"><span data-stu-id="6f528-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="6f528-105">WS-I Temel Profil 1.1 yönergelerine uymayan bazı SOAP 1.1 Web hizmetleri yığınları, Action URI'ye dayalı iletiler göndermez, daha çok SOAP gövdesi içindeki ilk öğenin XML nitelikli adını temel eder.</span><span class="sxs-lookup"><span data-stu-id="6f528-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="6f528-106">Aynı şekilde, bu yığınların istemci tarafı, SOAP 1.1 belirtimi tarafından izin verilen boş veya rasgele http SoapAction üstbilgisini içeren iletiler gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="6f528-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="6f528-107">İletilerin yöntemlere gönderilme biçimini değiştirmek için, örnek. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> `DispatchByBodyElementOperationSelector`</span><span class="sxs-lookup"><span data-stu-id="6f528-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="6f528-108">Bu sınıf, ileti gövdesinin ilk öğesini temel alan işlemleri seçer.</span><span class="sxs-lookup"><span data-stu-id="6f528-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="6f528-109">Sınıf oluşturucu, nitelikli adlar SOAP `XmlQualifiedName` gövdesinin ilk alt adını gösterir ve dizeleri eşleşen işlem adını gösterir, çiftleri ve dizeleri ile doldurulur bir sözlük bekliyor.</span><span class="sxs-lookup"><span data-stu-id="6f528-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="6f528-110">Bu `defaultOperationName` sözlükle eşleştirilemeyen tüm iletileri alan işlemin adı:</span><span class="sxs-lookup"><span data-stu-id="6f528-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="6f528-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>arabirimde tek bir yöntem olduğu için uygulamalar oluşturmak <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>çok kolaydır: .</span><span class="sxs-lookup"><span data-stu-id="6f528-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="6f528-112">Bu yöntemin işi, gelen bir iletiyi denetlemek ve geçerli bitiş noktası için hizmet sözleşmesinde bir yöntemin adı eşit bir dize döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="6f528-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="6f528-113">Bu örnekte, işlem seçici kullanarak <xref:System.Xml.XmlDictionaryReader> <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>gelen iletinin gövdesi için bir elde eder.</span><span class="sxs-lookup"><span data-stu-id="6f528-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="6f528-114">Bu yöntem zaten okuyucuyu iletinin gövdesinin ilk çocuğuna konumlandırır, böylece geçerli öğenin adını ve ad alanı `XmlQualifiedName` URI'yi almak ve bunları işlem seçicitarafından tutulan sözlükten karşılık gelen işlemi aramak için kullanılan bir şekilde birleştirmek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="6f528-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="6f528-115">İleti gövdesine <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> veya iletinin gövde içeriğine erişim sağlayan diğer yöntemlerden herhangi biriyle erişmek, iletinin "okundu" olarak işaretlenmesine neden olur, bu da iletinin başka bir işlem için geçersiz olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6f528-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="6f528-116">Bu nedenle, işlem seçici aşağıdaki kodda gösterilen yöntemle gelen iletinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f528-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="6f528-117">Denetim sırasında okuyucunun konumu değiştirilmedığından, ileti özelliklerinin ve ileti üstbilgilerinin de kopyalandığı yeni oluşturulan iletiyle başvurulabilir ve bu da özgün iletinin tam bir klonu ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="6f528-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="6f528-118">Hizmete İşlem Seçici Ekleme</span><span class="sxs-lookup"><span data-stu-id="6f528-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="6f528-119">Servis gönderme işlemi seçicileri, Windows Communication Foundation (WCF) göndericisinin uzantılarıdır.</span><span class="sxs-lookup"><span data-stu-id="6f528-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="6f528-120">Çift yönlü sözleşmelerin geri arama kanalında yöntemleri seçmek için, burada açıklanan gönderme işlemi seçicilerine çok benzeyen, ancak bu örnekte açıkça kapsanmayan istemci işlem seçicileri de vardır.</span><span class="sxs-lookup"><span data-stu-id="6f528-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="6f528-121">Çoğu hizmet modeli uzantıları gibi, sevkiyat işlemi seçicileri de davranışları kullanarak sevk irsaliyesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="6f528-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="6f528-122">*Davranış,* sevk çalışma süresine (veya istemci çalışma süresine) bir veya daha fazla uzantı ekleyen veya ayarlarını başka şekilde değiştiren bir yapılandırma nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="6f528-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="6f528-123">İşlem seçicileri sözleşme kapsamına sahip olduğundan, burada <xref:System.ServiceModel.Description.IContractBehavior>uygulanacak uygun davranış .</span><span class="sxs-lookup"><span data-stu-id="6f528-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="6f528-124">Arabirim, aşağıdaki kodda <xref:System.Attribute> gösterildiği gibi türetilmiş bir sınıfüzerinde uygulandığından, davranış bildirimolarak herhangi bir hizmet sözleşmesine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6f528-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="6f528-125">A <xref:System.ServiceModel.ServiceHost> açıldığında ve sevk çalışma zamanı oluşturulsa, sözleşmelerde, işlemlerde ve hizmet uygulamalarında öznitelikler olarak veya hizmet yapılandırmasındaki öğe olarak bulunan tüm davranışlar otomatik olarak eklenir ve daha sonra uzantılara katkıda bulunmaları veya varsayılan yapılandırmayı değiştirmeleri istenir.</span><span class="sxs-lookup"><span data-stu-id="6f528-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="6f528-126">Kısaltma için, aşağıdaki kod alıntısı yalnızca bu <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>örnekteki sevkiyatçının yapılandırma değişikliklerini etkileyen yöntemin uygulanmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f528-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="6f528-127">Diğer yöntemler gösterilmez, çünkü herhangi bir çalışma yapmadan arayanın geri dönmesine neden olurlar.</span><span class="sxs-lookup"><span data-stu-id="6f528-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="6f528-128">İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> uygulama, hizmet bitiş noktasının <xref:System.ServiceModel.Description.OperationDescription> öğeleri üzerinde yineleyerek işlem seçici için arama <xref:System.ServiceModel.Description.ContractDescription>sözlüğü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6f528-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="6f528-129">Daha sonra, her işlem açıklaması `DispatchBodyElementAttribute` davranışın varlığı için <xref:System.ServiceModel.Description.IOperationBehavior> denetlenir, bu örnekte de tanımlanan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="6f528-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="6f528-130">Bu sınıf aynı zamanda bir davranış olsa da, pasiftir ve sevkiyat çalışma süresine etkin olarak yapılandırma değişiklikleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6f528-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="6f528-131">Tüm yöntemleri herhangi bir işlem yapmadan arayanın geri döner.</span><span class="sxs-lookup"><span data-stu-id="6f528-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="6f528-132">İşlem davranışı yalnızca, yeni sevkiyat mekanizması için gerekli meta verilerin, yani bir işlemin oluşumunun seçildiği gövde öğesinin nitelikli adı, ilgili işlemlerle ilişkilendirilebilsin diye vardır.</span><span class="sxs-lookup"><span data-stu-id="6f528-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="6f528-133">Böyle bir davranış bulunursa, XML nitelikli adından`QName` (özellik) oluşturulan`Name` bir değer çifti ve işlem adı (özellik) sözlüğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="6f528-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="6f528-134">Sözlük dolduruldıktan sonra, bu `DispatchByBodyElementOperationSelector` bilgilerle yeni bir yapı oluşturulur ve sevk çalışma zamanının işlem seçicisi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="6f528-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="6f528-135">Hizmetin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="6f528-135">Implementing the Service</span></span>  
 <span data-ttu-id="6f528-136">Bu örnekte uygulanan davranış, doğrudan kablodan gelen iletilerin nasıl yorumlandığını ve gönderildiğini etkiler, bu da hizmet sözleşmesinin bir işlevidir.</span><span class="sxs-lookup"><span data-stu-id="6f528-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="6f528-137">Sonuç olarak, davranışı kullanmayı seçen herhangi bir hizmet uygulamasında hizmet sözleşmesi düzeyinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6f528-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="6f528-138">Örnek proje hizmeti, `DispatchByBodyElementBehaviorAttribute` sözleşme davranışını `IDispatchedByBody` hizmet sözleşmesine uygular ve `OperationForBodyA()` `OperationForBodyB()` her `DispatchBodyElementAttribute` iki işlemi ve bir işlem davranışını etiketler.</span><span class="sxs-lookup"><span data-stu-id="6f528-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="6f528-139">Bu sözleşmeyi uygulayan bir hizmetin hizmet ana bilgisayarı açıldığında, bu meta veriler daha önce açıklandığı gibi gönderen oluşturucu tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="6f528-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="6f528-140">İşlem seçici yalnızca ileti gövdesi öğesine göre gönderip "Eylem"i yok saydığından, döndürülen yanıtlardaki "Eylem" üstbilgisini özelliğine "\*" `ReplyAction` joker karakter atayarak denetlemememi için çalışma zamanı nın belirtilmesi <xref:System.ServiceModel.OperationContractAttribute>gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f528-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="6f528-141">Ayrıca, joker "\*"" olarak ayarlanmış "Eylem" özelliğine sahip varsayılan bir işlem olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f528-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="6f528-142">Varsayılan işlem, gönderilmeyen ve şu `DispatchBodyElementAttribute`gibi olmayan tüm iletileri alır:</span><span class="sxs-lookup"><span data-stu-id="6f528-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="6f528-143">Örnek hizmet uygulaması basittir.</span><span class="sxs-lookup"><span data-stu-id="6f528-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="6f528-144">Her yöntem alınan iletiyi bir yanıt iletisine sarar ve istemciye geri döndürer.</span><span class="sxs-lookup"><span data-stu-id="6f528-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="6f528-145">Numunenin Çalıştırılve Yapılmı</span><span class="sxs-lookup"><span data-stu-id="6f528-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="6f528-146">Örneği çalıştırdığınızda, işlem yanıtlarının gövde içeriği istemci konsol penceresinde aşağıdaki (biçimlendirilmiş) çıktıya benzer şekilde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6f528-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="6f528-147">İstemci, gövde içeriği öğesi adı `bodyA` `bodyB`,, ve `bodyX`, sırasıyla adlı hizmete üç ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="6f528-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="6f528-148">Önceki açıklama ve gösterilen hizmet sözleşmesinden ertelenebileceği gibi, `bodyA` öğeyle gelen ileti `OperationForBodyA()` yönteme gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6f528-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="6f528-149">`bodyX` Gövde öğesi ile ileti için açık bir gönderme hedefi olmadığından, ileti `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="6f528-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="6f528-150">Hizmet işlemlerinin her biri alınan ileti gövdesini yönteme özgü bir öğeye sarar ve bu örnek için giriş ve çıktı iletilerini açıkça ilişkilendirmek için yapılan iletileri döndürür:</span><span class="sxs-lookup"><span data-stu-id="6f528-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6f528-151">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6f528-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6f528-152">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="6f528-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6f528-153">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6f528-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6f528-154">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6f528-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f528-155">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f528-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6f528-156">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6f528-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6f528-157">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="6f528-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f528-158">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f528-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
