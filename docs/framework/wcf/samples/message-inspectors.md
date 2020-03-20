---
title: İleti Denetçileri
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 705401a182d5d816bc2682f5f21ff09ca95f21c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144454"
---
# <a name="message-inspectors"></a><span data-ttu-id="fe6d2-102">İleti Denetçileri</span><span class="sxs-lookup"><span data-stu-id="fe6d2-102">Message Inspectors</span></span>
<span data-ttu-id="fe6d2-103">Bu örnek, istemci ve hizmet iletisi denetçilerinin nasıl uygulanacağını ve yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="fe6d2-104">İleti denetçisi, hizmet modelinin istemci çalışma zamanında ve gönderme çalışma saatinde veya yapılandırma yoluyla kullanılabilecek ve iletileri alındıktan sonra veya gönderilmeden önce inceleyip değiştirebilen bir genişletilebilirlik nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="fe6d2-105">Bu örnek, gelen iletileri yapılandırılabilir XML Şema belgelerine karşı doğrulayan temel bir istemci ve hizmet iletisi doğrulama mekanizması uygular.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="fe6d2-106">Bu örnek her işlem için iletileri doğrulamaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="fe6d2-107">Bu kasıtlı bir basitleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="fe6d2-108">İleti Denetçisi</span><span class="sxs-lookup"><span data-stu-id="fe6d2-108">Message Inspector</span></span>  
 <span data-ttu-id="fe6d2-109">İstemci ileti <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> denetçileri arabirimi uygular <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> ve hizmet iletisi denetmenleri arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="fe6d2-110">Uygulamalar, her iki taraf için de çalışan bir ileti denetçisi oluşturmak için tek bir sınıfa birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="fe6d2-111">Bu örnek böyle bir leştirilmiş ileti denetçisi uygular.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="fe6d2-112">Denetçi, gelen ve giden iletilerin doğrulandığı bir dizi şema da oluşturulur ve geliştiricinin gelen veya giden iletilerin doğrulanıp doğrulanmadığını ve denetçinin sevk veya istemci modunda olup olmadığını belirlemesine olanak tanır, bu konunun daha sonra tartışılan hata işleme etkiler.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
```csharp
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 <span data-ttu-id="fe6d2-113">Herhangi bir hizmet (sevk irsaliyesi) ileti denetçisi iki <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> yöntem <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="fe6d2-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>bir ileti alındığı, kanal yığını tarafından işlendiği ve bir hizmete atandığı, ancak seri çözülmeden ve bir işleme gönderilmeden önce sevk eden tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="fe6d2-115">Gelen ileti şifrelenmişse, ileti denetçisi ne zaman ulaşırsa iletinin şifresi zaten çözülür.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="fe6d2-116">Yöntem, iletinin `request` denetlenmesini, işlenmesini veya gerektiği gibi değiştirilmesine olanak tanıyan bir başvuru parametresi olarak iletinin geçirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="fe6d2-117">İade değeri herhangi bir nesne olabilir ve hizmet geçerli iletiye <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> bir yanıt verdiğinde geçirilen bir korelasyon durumu nesnesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="fe6d2-118">Bu örnekte, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> iletinin denetimini (doğrulanmasını) özel, `ValidateMessageBody` yerel yönteme devreder ve hiçbir korelasyon durumu nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="fe6d2-119">Bu yöntem, hizmete geçersiz iletilerin geçmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
```csharp  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="fe6d2-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>bir yanıt istemciye geri gönderilmeye hazır olduğunda veya gelen ileti işlendiğinde tek yönlü iletiler söz konusu olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="fe6d2-121">Bu uzantıları ne olursa olsun MEP, simetrik olarak adlandırılan saymak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="fe6d2-122">Olduğu <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>gibi, ileti bir başvuru parametresi olarak geçirilir ve denetlenebilir, değiştirilebilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="fe6d2-123">Bu örnekte gerçekleştirilen iletinin doğrulaması yine `ValidMessageBody` yönteme devredilir, ancak doğrulama hatalarının işlenmesi bu durumda biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="fe6d2-124">Hizmette bir doğrulama hatası oluşursa, `ValidateMessageBody` <xref:System.ServiceModel.FaultException>yöntem türetilmiş özel durumlar atar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="fe6d2-125">Bu <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>istisnalar, otomatik olarak SOAP hatalarına dönüştürülüp istemciye aktarılan servis modeli altyapısına konulabilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="fe6d2-126">Hizmet <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> <xref:System.ServiceModel.FaultException> tarafından atılan hata özel durumlarının dönüşümü ileti denetçisi çağrılmadan önce oluştuğundan, özel durumlar altyapıya konulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="fe6d2-127">Bu nedenle, aşağıdaki `ReplyValidationFault` uygulama bilinen özel durumu yakalar ve yanıt iletisi açık bir hata iletisi ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="fe6d2-128">Bu yöntem, hizmet uygulaması tarafından geçersiz iletilerin döndürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
```csharp  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 <span data-ttu-id="fe6d2-129">İstemci ileti denetçisi çok benzer.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-129">The client message inspector is very similar.</span></span> <span data-ttu-id="fe6d2-130">Uygulanması gereken iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> ve <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> . <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A></span><span class="sxs-lookup"><span data-stu-id="fe6d2-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="fe6d2-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>ileti istemci uygulaması veya işlem formatter tarafından oluşturulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="fe6d2-132">Sevk irsaliyesi ileti denetçilerinde olduğu gibi, ileti sadece denetlenebilir veya tamamen değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="fe6d2-133">Bu örnekte, denetçi, gönderme iletisi denetçileri için de kullanılan aynı yerel `ValidateMessageBody` yardımcı yöntemini devreder.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="fe6d2-134">İstemci ve hizmet doğrulaması arasındaki davranış farkı (oluşturucuda belirtildiği gibi), istemci doğrulamasının bir hizmet hatası nedeniyle değil, yerel olarak oluştukları için kullanıcı koduna konulan yerel özel durumlar atmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="fe6d2-135">Genel olarak, kural, servis sevk irsaliyesi müfettişleri hataları atmak ve istemci müfettişleri özel durumlar atmak olduğunu.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="fe6d2-136">Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulama, hizmete geçersiz ileti gönderilmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="fe6d2-137">Uygulama, `AfterReceiveReply` hizmetten alınan geçersiz iletilerin istemci kullanıcı koduna iletilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="fe6d2-138">Bu özel mesaj denetçisinin `ValidateMessageBody` kalbi yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="fe6d2-139">Çalışmasını gerçekleştirmek için, geçirilen iletinin <xref:System.Xml.XmlReader> gövde içeriği alt ağacının etrafına doğrulayan bir sarar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="fe6d2-140">Okuyucu, ileti denetçisinin tuttuğu şema kümesiyle doldurulur ve doğrulama geri araması, bu yöntemin yanında tanımlanana atıfta bulunan `InspectionValidationHandler` bir temsilciye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="fe6d2-141">Doğrulamayı gerçekleştirmek için ileti okunur ve bellek akışı destekli bir alana <xref:System.Xml.XmlDictionaryWriter>biriktirilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="fe6d2-142">İşlemde bir doğrulama hatası veya uyarı oluşursa, geri arama yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="fe6d2-143">Hata oluşmaz, özellikleri ve üstbilgileri özgün iletiden kopyalayan ve bellek akışında şimdi doğrulanmış bilgi kümesini kullanan ve bir <xref:System.Xml.XmlDictionaryReader> iletiyi sarıp değiştirilen iletiye eklenen yeni bir ileti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
```csharp  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 <span data-ttu-id="fe6d2-144">Yöntem, `InspectionValidationHandler` şema doğrulama <xref:System.Xml.XmlReader> hatası veya uyarısı oluştuğunda doğrulama tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="fe6d2-145">Aşağıdaki uygulama yalnızca hatalarla çalışır ve tüm uyarıları yok sayar.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="fe6d2-146">İlk olarak, ileti denetçisi ile <xref:System.Xml.XmlReader> iletiye doğrulama enjekte etmek ve ileti işlenirken ve iletiyi arabelleğe almadan doğrulamanın gerçekleşmesine izin vermek mümkün görünebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="fe6d2-147">Ancak bu, bu geri aramanın doğrulama özel durumlarını hizmet modeli altyapısına veya geçersiz XML düğümleri algılanırken kullanıcı koduna bir yere attığı ve öngörülemeyen davranışlara yol açacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="fe6d2-148">Arabelleğe alma yaklaşımı, kullanıcı kodunu geçersiz iletilerden tamamen korur.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="fe6d2-149">Daha önce de ele alındığı gibi, işleyici tarafından atılan özel durumlar istemci ve hizmet arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="fe6d2-150">Hizmette, özel <xref:System.ServiceModel.FaultException>durumlar, istemcide istisnalar düzenli özel özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
```csharp  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a><span data-ttu-id="fe6d2-151">Davranış</span><span class="sxs-lookup"><span data-stu-id="fe6d2-151">Behavior</span></span>  
 <span data-ttu-id="fe6d2-152">İleti denetçileri istemci çalışma zamanı veya sevk çalışma zamanı uzantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="fe6d2-153">Bu tür uzantılar *davranışlar*kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="fe6d2-154">Davranış, varsayılan yapılandırmayı değiştirerek veya uzantılar (ileti baslayışları gibi) ekleyerek hizmet modelinin çalışma zamanı davranışını değiştiren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="fe6d2-155">Aşağıdaki `SchemaValidationBehavior` sınıf, bu örneğin ileti denetçisini istemciye veya sevk çalışma süresine eklemek için kullanılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="fe6d2-156">Uygulama her iki durumda da oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="fe6d2-157">Içinde <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>ve , ileti denetçisi <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> oluşturulur ve ilgili çalışma zamanı nın koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
```csharp
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;
    bool validateRequest;
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,
       System.ServiceModel.Channels.BindingParameterCollection
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,
         System.ServiceModel.Dispatcher.EndpointDispatcher
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="fe6d2-158">Bu özel davranış bir öznitelik olarak iki katına çıkmaz ve bu nedenle bir hizmet türünün sözleşme türüne bildirimsel olarak eklenemez.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="fe6d2-159">Şema koleksiyonu bir öznitelik bildirimine yüklenemediği ve bu öznitelikte fazladan bir yapılandırma konumuna (örneğin uygulama ayarlarına) atıfta bulunulduğu için bu, bir yapılandırma öğesi oluşturma anlamına geldiği için alınan bir yan tasarım kararıdır. hizmet modeli yapılandırmasının geri kalanıyla tutarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="fe6d2-160">Bu nedenle, bu davranış yalnızca zorunlu olarak kod ve hizmet modeli yapılandırma uzantısı yoluyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="fe6d2-161">Yapılandırma yoluyla İleti Denetçisi ekleme</span><span class="sxs-lookup"><span data-stu-id="fe6d2-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="fe6d2-162">Uygulama yapılandırma dosyasındaki bir bitiş noktasında özel bir davranışı yapılandırmak için, hizmet modeli uygulayıcıların türetilen <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>bir sınıf tarafından temsil edilen bir yapılandırma uzantısı *öğesi* oluşturmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="fe6d2-163">Bu uzantı, bu bölümde açıklanan aşağıdaki uzantıda gösterildiği gibi uzantılar için hizmet modelinin yapılandırma bölümüne eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 <span data-ttu-id="fe6d2-164">Uzantılar, en yaygın seçenek olan uygulama veya ASP.NET yapılandırma dosyasına veya makine yapılandırma dosyasına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="fe6d2-165">Uzantı yapılandırma kapsamına eklendiğinde, davranış aşağıdaki kodda gösterildiği gibi davranış yapılandırmasına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="fe6d2-166">Davranış yapılandırmaları, gerektiğinde birden çok uç noktaya uygulanabilen yeniden kullanılabilir öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="fe6d2-167">Burada yapılandırılacak belirli bir davranış <xref:System.ServiceModel.Description.IEndpointBehavior>uygulandığından, yalnızca yapılandırma dosyasındaki ilgili yapılandırma bölümünde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="fe6d2-168">İleti `<schemaValidator>` denetçisini yapılandıran öğe `SchemaValidationBehaviorExtensionElement` sınıf tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="fe6d2-169">Sınıf adlı `ValidateRequest` iki Boolean ortak `ValidateReply`özellikleri ortaya çıkarır ve .</span><span class="sxs-lookup"><span data-stu-id="fe6d2-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="fe6d2-170">Bunların her ikisi de <xref:System.Configuration.ConfigurationPropertyAttribute>bir .</span><span class="sxs-lookup"><span data-stu-id="fe6d2-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="fe6d2-171">Bu öznitelik, önceki XML yapılandırma öğesinde görülebilen kod özellikleri ile XML öznitelikleri arasındaki bağlantıyı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="fe6d2-172">Sınıf ayrıca ek `Schemas` olarak işaretlenmiş <xref:System.Configuration.ConfigurationCollectionAttribute> bir özelliği vardır ve `SchemaCollection`türü , aynı zamanda bu örneğin bir parçası olan ancak kısalık için bu belgeden atlanan.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="fe6d2-173">Bu özellik, koleksiyon ve koleksiyon `SchemaConfigElement` öğesi sınıfıyla birlikte önceki yapılandırma snippet'indeki öğeyi `<schemas>` geri verir ve doğrulama kümesine şema koleksiyonu eklemeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="fe6d2-174">Geçersiz kılınan `CreateBehavior` yöntem, çalışma zamanı bir istemci veya bitiş noktası oluştururken yapılandırma verilerini değerlendirirken yapılandırma verilerini davranış nesnesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
```csharp
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType
    {
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs
     //.NET Framework to build a nested section of
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="fe6d2-175">Zorunlu Olarak İleti Denetçisi Ekleme</span><span class="sxs-lookup"><span data-stu-id="fe6d2-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="fe6d2-176">Öznitelikler (daha önce atıfta bulunulan nedenlerle bu örnekte desteklenmeyen) ve yapılandırma dışında, davranışlar zorunlu kod kullanılarak istemci ve hizmet çalışma süresine kolayca eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="fe6d2-177">Bu örnekte, bu istemci ileti denetçisi sınamak için istemci uygulamasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="fe6d2-178"><xref:System.ServiceModel.ClientBase%601>Sınıf, `GenericClient` uç nokta yapılandırmasını kullanıcı koduna gösteren türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="fe6d2-179">İstemci örtülü olarak açılmadan önce, örneğin aşağıdaki kodda gösterildiği gibi davranışlar eklenerek uç nokta yapılandırması değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="fe6d2-180">Hizmetteki davranışın eklenmesi büyük ölçüde burada gösterilen istemci tekniğine eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
```csharp  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fe6d2-181">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fe6d2-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fe6d2-182">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fe6d2-183">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fe6d2-184">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fe6d2-185">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fe6d2-186">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fe6d2-187">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fe6d2-188">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe6d2-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
