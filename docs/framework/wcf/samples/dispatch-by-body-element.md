---
title: Gövde Öğesine göre Dağıt
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ab8ddccafa8dbf1ecde8afbb07f0a61faa62be5
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="d2c1b-102">Gövde Öğesine göre Dağıt</span><span class="sxs-lookup"><span data-stu-id="d2c1b-102">Dispatch by Body Element</span></span>
<span data-ttu-id="d2c1b-103">Bu örnek, gelen iletileri işlemlerine izin atamak için alternatif bir algoritma uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="d2c1b-104">Varsayılan olarak, hizmet modeli dağıtıcısı ileti WS-üzerinde tabanlı adresleme gelen ileti için uygun işleme yöntemi seçer "Eylem" üstbilgi veya HTTP SOAP isteğinin eşdeğer bilgileri.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="d2c1b-105">WS izlemeyin yığınları bazı SOAP 1.1 Web Hizmetleri-ı temel Profil 1.1 yönergeleri eylem URI üzerinde temel, ancak bunun yerine ilk öğe SOAP gövdesi içinde XML tam adını temel iletileri gönderme değil.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="d2c1b-106">Benzer şekilde, bu yığınları istemci tarafı SOAP 1.1 belirtimine göre verilmişti bir boş veya rasgele HTTP SoapAction başlık iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="d2c1b-107">Yöntemlere iletileri gönderilen şeklini değiştirmek için örnek uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> genişletilebilirlik arabirimde `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="d2c1b-108">Bu sınıf, ileti gövdesinin ilk öğe üzerinde temel işlemleri seçer.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="d2c1b-109">Sınıf oluşturucu çiftleri ile doldurulan bir sözlük bekliyor `XmlQualifiedName` ve alınabildiği nitelenmiş adlar SOAP gövdesi ilk alt adını belirtmek ve işlem adıyla eşleşen dizeleri belirtmek dizeleri.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="d2c1b-110">`defaultOperationName` Bu sözlük karşı eşleşen tüm iletileri alan işlemi adıdır:</span><span class="sxs-lookup"><span data-stu-id="d2c1b-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <span data-ttu-id="d2c1b-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> uygulamaları arabirimde tek bir yöntem olarak oluşturmak çok basit: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="d2c1b-112">Bu yöntemin iş gelen iletiyi incelemek için bir hizmet sözleşmesi yöntemi geçerli uç nokta adına eşit bir dize döndürecek şekilde ise.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="d2c1b-113">Bu örnekte, işlem Seçici edinir bir <xref:System.Xml.XmlDictionaryReader> gelen ileti gövdesi kullanarak kullanıcının <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="d2c1b-114">Bu yöntem okuyucu böylece geçerli öğenin adını ve ad alanı URI'si almak ve bunları birleştirmek yeterli iletinin gövdesi ilk alt zaten yerleştirir. bir `XmlQualifiedName` sonra kullanılan karşılık gelen işlemi bakmak işlem Seçici tarafından tutulan sözlük.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```  
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
  
 <span data-ttu-id="d2c1b-115">İleti gövdesi erişme <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ya da ileti gövdesi içeriğe erişmeye neden iletinin ileti herhangi başka bir işleme için geçersiz olduğu anlamına gelir "Okuma" olarak işaretlenmiş sağlayan diğer yöntemlerden herhangi birini.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="d2c1b-116">Bu nedenle, işlem Seçici aşağıdaki kodda gösterildiği yöntemiyle gelen iletinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="d2c1b-117">Okuyucunun konumu İnceleme sırasında değiştirilmedi çünkü orijinal iletinin tam bir kopyasını sonuçları yeni oluşturulan ileti için ileti özellikleri ve ileti üstbilgilerini de kopyalanır, tarafından başvurulabilir:</span><span class="sxs-lookup"><span data-stu-id="d2c1b-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="d2c1b-118">Bir hizmet için bir işlem seçici ekleme</span><span class="sxs-lookup"><span data-stu-id="d2c1b-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="d2c1b-119">Hizmeti dağıtma işlemi seçiciler uzantıları olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dağıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-119">Service dispatch operation selectors are extensions to the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher.</span></span> <span data-ttu-id="d2c1b-120">Çift yönlü sözleşmeler geri çağırma kanalda yöntemlerini seçmek için de vardır çok gönderme işlemi seçiciler burada açıklanan ancak, bu örnekte açıkça kapsanmayan gibi iş istemci işlemi seçicileri.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="d2c1b-121">Çoğu hizmet modeli uzantıları gibi gönderme işlemi seçiciler davranışları kullanarak dağıtıcısı eklenir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="d2c1b-122">A *davranışı* gönderme çalışma zamanı (veya istemci çalışma zamanı) bir veya daha fazla uzantıları ekler veya aksi halde ayarlarını değiştirir yapılandırma nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="d2c1b-123">İşlem Seçici sözleşmesi kapsamına sahip olduğundan, burada uygulamak için uygun davranıştır <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="d2c1b-124">Arabirim üzerinde uygulanır çünkü bir <xref:System.Attribute> türetilmiş sınıf aşağıdaki kodda gösterildiği gibi davranışı bildirimli olarak hiçbir hizmet sözleşmesine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="d2c1b-125">Her bir <xref:System.ServiceModel.ServiceHost> açılır ve gönderme çalışma zamanı oluşturulmuştur, tüm davranışları sözleşmeler, işlemleri ve hizmet uygulamaları özniteliklerinde veya hizmet yapılandırma öğesi olarak otomatik olarak eklenir ve daha sonra istenir bulundu Uzantıları katkıda veya varsayılan yapılandırmayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="d2c1b-126">Konuyu uzatmamak amacıyla, aşağıdaki kod Alıntısı yöntemin kullanımı yalnızca gösterir <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, hangi etkiler yapılandırma değişikliklerinin bu örnekteki dağıtıcı için.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="d2c1b-127">Herhangi bir iş yapmadan çağırana döndürmeleri çünkü diğer yöntemleri gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="d2c1b-128">İlk olarak, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> uygulama ayarlayan işlem Seçici arama sözlük üzerinden yineleme tarafından <xref:System.ServiceModel.Description.OperationDescription> hizmet uç noktanın öğelerinde <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="d2c1b-129">Her işlem açıklaması varlığını ardından Denetlenmekte `DispatchBodyElementAttribute` davranışı, uygulaması <xref:System.ServiceModel.Description.IOperationBehavior> Bu örnek ayrıca tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="d2c1b-130">Bu sınıf bir davranış da olsa da, pasif ve etkin olarak gönderme çalışma zamanı için herhangi bir yapılandırma değişikliği katkıda değil.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="d2c1b-131">Tüm yöntemlerinden herhangi bir eylem bırakmadan çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="d2c1b-132">Böylece bir işlem seçildiğinde, geçişi ile ilgili işlemleri ilişkilendirilebilir yeni gönderme mekanizması için yani body öğesinde tam adını meta verileri gerekli işlemi davranışı yalnızca bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="d2c1b-133">Bu tür bir davranış bulunursa, değer çifti oluşturulan XML tam adı (`QName` özelliği) ve işlem adı (`Name` özelliği) sözlüğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="d2c1b-134">Sözlük, yeni bir doldurulduktan sonra `DispatchByBodyElementOperationSelector` bu bilgilerle oluşturulur ve gönderme çalışma zamanı işlem Seçici ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="d2c1b-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="d2c1b-135">Uygulama hizmeti</span><span class="sxs-lookup"><span data-stu-id="d2c1b-135">Implementing the Service</span></span>  
 <span data-ttu-id="d2c1b-136">Bu örnekte doğrudan uygulanan davranışını nasıl kablo iletilerden yorumlanır ve dağıtılan, hizmet sözleşmesi işlevinin olduğu etkiler.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="d2c1b-137">Sonuç olarak, davranışı kullanmak için seçtiği herhangi bir hizmet uygulaması hizmet sözleşmesi düzeyinde üzerindeki bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="d2c1b-138">Örnek Proje hizmeti geçerlidir `DispatchByBodyElementBehaviorAttribute` sözleşme davranışına `IDispatchedByBody` hizmet sözleşmesi ve etiketlerinin her iki işlem `OperationForBodyA()` ve `OperationForBodyB()` ile bir `DispatchBodyElementAttribute` işlemi davranışı.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="d2c1b-139">Bu sözleşme uygulayan bir hizmet için bir hizmet konak açıldığında, bu meta veriler daha önce anlatıldığı dağıtıcısı Oluşturucu tarafından kayıt.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="d2c1b-140">İşlem Seçici ileti gövdesi öğesinde yalnızca tabanlı gönderir ve "Eylem" yoksayar olduğundan, döndürülen yanıt "Eylem" başlığında joker atayarak denetlemek için çalışma zamanı bildirmek için gereklidir "\*" için `ReplyAction` özelliği <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="d2c1b-141">Ayrıca, "Eylem" özelliği için joker karakter olarak ayarlanmış bir varsayılan işlemi sahip olması gereken "\*".</span><span class="sxs-lookup"><span data-stu-id="d2c1b-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="d2c1b-142">Varsayılan işlemi gönderilen olamaz ve sahip olmayan tüm iletileri alan bir `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="d2c1b-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```  
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
  
 <span data-ttu-id="d2c1b-143">Örnek hizmet uygulaması basittir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="d2c1b-144">Her yöntem alınan ileti yanıt iletisine sarmalar ve istemciye görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="d2c1b-145">Çalıştıran ve örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2c1b-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="d2c1b-146">Örneği çalıştırdığınızda, işlem yanıt gövdesi içeriğini aşağıdaki (biçimlendirilmiş) çıktıyı benzer istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="d2c1b-147">İstemci üç iletileri hizmetine, gövde öğesi adlandırılan içerik gönderir `bodyA`, `bodyB`, ve `bodyX`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="d2c1b-148">Önceki Açıklama ve gösterilen hizmet sözleşmesini ertelenmiş olarak gelen ileti ile `bodyA` öğesi gönderilen için `OperationForBodyA()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="d2c1b-149">İleti için hiçbir açık gönderme hedef olduğundan `bodyX` ileti body öğesi gönderilen için `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="d2c1b-150">Her hizmet işlemlerinin yönteme belirli bir öğenin içine alınan ileti gövdesi sarmalar ve, giriş ilişkilendirmek ve bu örnek için açıkça iletileri çıkış yapılır döndürür:</span><span class="sxs-lookup"><span data-stu-id="d2c1b-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d2c1b-151">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d2c1b-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d2c1b-152">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2c1b-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d2c1b-153">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2c1b-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d2c1b-154">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2c1b-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2c1b-155">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d2c1b-156">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d2c1b-157">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d2c1b-158">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="d2c1b-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c1b-159">See Also</span></span>
