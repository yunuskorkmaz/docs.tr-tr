---
title: İleti Denetçileri
description: Bir ileti doğrulama mekanizması sağlayan WCF istemcisi ve hizmet ileti denetçilerini uygulamayı ve yapılandırmayı öğrenin.
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 20abb655a58f9dce4a967ade9b51db90eed2375b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246217"
---
# <a name="message-inspectors"></a><span data-ttu-id="1a01b-103">İleti Denetçileri</span><span class="sxs-lookup"><span data-stu-id="1a01b-103">Message Inspectors</span></span>
<span data-ttu-id="1a01b-104">Bu örnek, istemci ve hizmet ileti denetçilerini nasıl uygulanacağını ve yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-104">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="1a01b-105">İleti denetçisi, hizmet modelinin istemci çalışma zamanı ve dağıtım çalışma zamanında programlama yoluyla veya yapılandırma aracılığıyla kullanılabilen ve iletileri alındıktan sonra veya gönderilmeden önce incelemenize ve değiştirebilecek bir genişletilebilirlik nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-105">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="1a01b-106">Bu örnek, bir dizi yapılandırılabilir XML şema belgelerine karşı gelen iletileri doğrulayan temel bir istemci ve hizmet iletisi doğrulama mekanizmasını uygular.</span><span class="sxs-lookup"><span data-stu-id="1a01b-106">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="1a01b-107">Bu örnekte her işlem için iletileri doğrulamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1a01b-107">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="1a01b-108">Bu, bilerek basitleştirmesi.</span><span class="sxs-lookup"><span data-stu-id="1a01b-108">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="1a01b-109">İleti denetçisi</span><span class="sxs-lookup"><span data-stu-id="1a01b-109">Message Inspector</span></span>  
 <span data-ttu-id="1a01b-110">İstemci ileti Inspectors <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimini ve hizmet iletisi denetçilerini uygulayan <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="1a01b-110">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="1a01b-111">Uygulamalar, her iki taraf için de çalışacak bir ileti denetçisi oluşturmak için tek bir sınıfta birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-111">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="1a01b-112">Bu örnek, bu tür bir Birleşik ileti denetçisi uygular.</span><span class="sxs-lookup"><span data-stu-id="1a01b-112">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="1a01b-113">Inspector, gelen ve giden iletilerin doğrulandığı bir şema kümesi ile oluşturulur ve geliştiricinin gelen veya giden mesajların doğrulanıp onaylanmadığını ve Inspector 'ın gönderim veya istemci modunda olup olmadığını belirtmesini sağlar ve bu konunun ilerleyen kısımlarında açıklanan hata işlemeyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="1a01b-113">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-114">Herhangi bir hizmet (dağıtıcı) ileti denetçisi iki <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> yöntemi ve uygulamalıdır <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> .</span><span class="sxs-lookup"><span data-stu-id="1a01b-114">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="1a01b-115"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, bir ileti alındığında, kanal yığını tarafından işlendiğinde ve bir hizmete atandığında,, seri durumdan çıkarılmadan ve bir işleme dağıtılmadan önce dağıtıcı tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-115"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="1a01b-116">Gelen ileti şifrelendiyse, ileti denetçisine ulaştığında iletinin şifresi zaten çözülür.</span><span class="sxs-lookup"><span data-stu-id="1a01b-116">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="1a01b-117">Yöntemi, `request` bir başvuru parametresi olarak geçirilen iletiyi alır, bu da iletinin gerekli olduğu şekilde incelen, değiştirilmesine veya değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-117">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="1a01b-118">Dönüş değeri herhangi bir nesne olabilir ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> hizmet geçerli iletiye bir yanıt döndürdüğünde geçirilen bir bağıntı durumu nesnesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-118">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="1a01b-119">Bu örnekte, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> iletinin denetlemesini (doğrulaması) Private, yerel yöntemine devreder `ValidateMessageBody` ve bağıntı durumu nesnesi döndürmez.</span><span class="sxs-lookup"><span data-stu-id="1a01b-119">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="1a01b-120">Bu yöntem, hizmete hiçbir geçersiz ileti geçmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-120">This method ensures that no invalid messages pass into the service.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-121"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>bir yanıt istemciye geri gönderilmek üzere olduğunda veya tek yönlü iletiler söz konusu olduğunda gelen ileti işlendiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-121"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="1a01b-122">Bu, uzantılarından bağımsız olarak, uzantıların simetrik olarak çağrıldığından sayımına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-122">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="1a01b-123">İle olduğu gibi <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> , ileti başvuru parametresi olarak geçirilir ve incelenebilir, değiştirilebilir veya değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-123">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="1a01b-124">Bu örnekte gerçekleştirilen iletinin doğrulanması, yöntemi için yeniden temsilci olarak oluşturulur `ValidMessageBody` , ancak doğrulama hatalarının işlenmesi bu durumda biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-124">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="1a01b-125">Hizmette bir doğrulama hatası oluşursa, `ValidateMessageBody` yöntemi <xref:System.ServiceModel.FaultException> -türetilmiş özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-125">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="1a01b-126"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>' De, bu özel durumlar, otomatik olarak SOAP hatalarına dönüştürülebileceği ve istemciye geçirildikleri hizmet modeli altyapısına yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="1a01b-127">' De <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> , <xref:System.ServiceModel.FaultException> hizmet tarafından oluşturulan hata özel durumlarının dönüşümü ileti denetçisi çağrılmadan önce gerçekleştiği için özel durumlar altyapıya yerleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-127">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="1a01b-128">Bu nedenle, aşağıdaki uygulama bilinen `ReplyValidationFault` özel durumu yakalar ve yanıt iletisini açık bir hata iletisiyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-128">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="1a01b-129">Bu yöntem, hizmet uygulamasının hiçbir geçersiz ileti döndürülmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-129">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-130">İstemci ileti denetçisi çok benzerdir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-130">The client message inspector is very similar.</span></span> <span data-ttu-id="1a01b-131">' Den uygulanması gereken iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> ve ' dir <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> .</span><span class="sxs-lookup"><span data-stu-id="1a01b-131">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="1a01b-132"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>ileti, istemci uygulaması ya da işlem biçimlendirici tarafından oluşturulduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-132"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="1a01b-133">Dağıtıcı ileti denetçiler itibariyle, ileti yalnızca incelenebilir veya tamamen değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-133">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="1a01b-134">Bu örnekte, Inspector `ValidateMessageBody` dağıtım iletisi denetçisi için de kullanılan aynı yerel yardımcı yöntemine temsilci atar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-134">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="1a01b-135">İstemci ve hizmet doğrulaması arasındaki davranış farkı (oluşturucuda belirtildiği gibi), istemci doğrulamasının bir hizmet hatası nedeniyle yerel olarak gerçekleştiğinden, Kullanıcı koduna yerleştirilen yerel özel durumları yaratmaktır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-135">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="1a01b-136">Genellikle kural, hizmet dağıtıcılarının hata oluşturması ve istemci denetçlarının özel durumlar oluşturması şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-136">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="1a01b-137">Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulama, hizmete geçersiz ileti gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-137">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-138">`AfterReceiveReply`Uygulama, hizmetten alınan geçersiz iletilerin istemci kullanıcı koduna geçirilmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-138">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="1a01b-139">Bu özel ileti denetçisinin kalp `ValidateMessageBody` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-139">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="1a01b-140">Çalışmasını gerçekleştirmek için, <xref:System.Xml.XmlReader> geçirilen iletinin gövde içeriği alt ağacı etrafında bir doğrulama sarmalar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-140">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="1a01b-141">Okuyucu, ileti denetçisinin tuttuğu şemalar kümesi ile doldurulur ve doğrulama geri çağırması, `InspectionValidationHandler` Bu yöntemin yanı sıra tanımlanan öğesine başvuran bir temsilciye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-141">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="1a01b-142">Doğrulama işlemini gerçekleştirmek için ileti daha sonra okuyup bir bellek akışı ile desteklenir <xref:System.Xml.XmlDictionaryWriter> .</span><span class="sxs-lookup"><span data-stu-id="1a01b-142">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="1a01b-143">İşlemde bir doğrulama hatası veya uyarı oluşursa, geri çağırma yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-143">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="1a01b-144">Herhangi bir hata oluşursa, özgün iletiden özellikleri ve başlıkları kopyalayan ve bir ile kaydırılan <xref:System.Xml.XmlDictionaryReader> ve değiştirme iletisine eklenen bir bellek akışında şimdi doğrulanan bilgi kümesini kullanan yeni bir ileti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-144">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-145">`InspectionValidationHandler`Yöntemi, <xref:System.Xml.XmlReader> bir şema doğrulama hatası veya uyarı oluştuğunda doğrulama tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-145">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="1a01b-146">Aşağıdaki uygulama yalnızca hatalarla birlikte çalışarak tüm uyarıları yoksayar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-146">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="1a01b-147">İlk bakışta ileti <xref:System.Xml.XmlReader> denetçisi ile iletiye bir doğrulama eklemek ve ileti işlendiğinde ve iletiyi arabelleğe almadan doğrulamanın gerçekleşmesini sağlamak mümkün görünebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-147">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="1a01b-148">Bununla birlikte, bu geri aramanın, doğrulama özel durumlarını hizmet modeli altyapısında veya geçersiz XML düğümleri algılandığı için Kullanıcı kodu olduğu anlamına gelir, ancak öngörülemeyen davranışlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-148">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="1a01b-149">Arabelleğe alma yaklaşımı, Kullanıcı kodunu geçersiz iletilerden tamamen kalkan.</span><span class="sxs-lookup"><span data-stu-id="1a01b-149">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="1a01b-150">Daha önce anlatıldığı gibi işleyici tarafından oluşturulan özel durumlar, istemci ve hizmet arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-150">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="1a01b-151">Hizmette, özel durumlar ' dan türetilir <xref:System.ServiceModel.FaultException> , istemci üzerindeki özel durumlar normal özel istisnalardır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-151">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
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
  
## <a name="behavior"></a><span data-ttu-id="1a01b-152">Davranış</span><span class="sxs-lookup"><span data-stu-id="1a01b-152">Behavior</span></span>  
 <span data-ttu-id="1a01b-153">İleti denetçiler, istemci çalışma zamanına veya dağıtım çalışma zamanına yönelik uzantılardır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-153">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="1a01b-154">Bu tür uzantılar *davranışlar*kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-154">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="1a01b-155">Davranış, varsayılan yapılandırmayı değiştirerek veya uzantıları (ileti denetçiler gibi) ekleyerek hizmet modeli çalışma zamanının davranışını değiştiren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-155">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="1a01b-156">Aşağıdaki `SchemaValidationBehavior` sınıf, bu örneğin ileti denetçisini istemciye veya dağıtım çalışma zamanına eklemek için kullanılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-156">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="1a01b-157">Uygulama, her iki durumda da temel değildir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-157">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="1a01b-158"><xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A>Ve <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> ' de, ileti denetçisi oluşturulur ve <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> ilgili çalışma zamanının koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-158">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
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
> <span data-ttu-id="1a01b-159">Bu belirli davranış bir öznitelik olarak Double değildir ve bu nedenle bir hizmet türünün anlaşma türüne bildirimli olarak eklenemez.</span><span class="sxs-lookup"><span data-stu-id="1a01b-159">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="1a01b-160">Şema koleksiyonu bir öznitelik bildiriminde yüklenemeyeceği ve bu öznitelikteki ek bir yapılandırma konumuna (örneğin uygulama ayarlarına) başvuru yapıldığından, hizmet modeli yapılandırmasının geri kalanı ile tutarlı olmayan bir yapılandırma öğesi oluşturulması gerektiği için, bu bir tasarım tarafından yapılan bir karardır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-160">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="1a01b-161">Bu nedenle, bu davranış yalnızca kod üzerinden ve bir hizmet modeli yapılandırma uzantısı aracılığıyla imperatively eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-161">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="1a01b-162">Yapılandırma yoluyla Ileti denetçisi ekleme</span><span class="sxs-lookup"><span data-stu-id="1a01b-162">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="1a01b-163">Uygulama yapılandırma dosyasındaki bir uç noktada özel bir davranışı yapılandırmak için, hizmet modeli, ımplemenondan türetilmiş bir sınıf tarafından temsil edilen bir yapılandırma *uzantısı öğesi* oluşturmasını gerektirir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="1a01b-163">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="1a01b-164">Bu uzantı, bu bölümde açıklanan aşağıdaki uzantı için gösterildiği gibi, uzantılar için hizmet modelinin yapılandırma bölümüne eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-164">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-165">Uzantılar, en yaygın seçim olan veya makine yapılandırma dosyasında bulunan uygulama veya ASP.NET yapılandırma dosyasına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-165">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="1a01b-166">Uzantı bir yapılandırma kapsamına eklendiğinde, davranış aşağıdaki kodda gösterildiği gibi bir davranış yapılandırmasına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-166">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="1a01b-167">Davranış yapılandırması, gerektiğinde birden çok uç noktaya uygulanabilen yeniden kullanılabilir öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-167">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="1a01b-168">Burada yapılandırılacak belirli davranış uyguladığı için <xref:System.ServiceModel.Description.IEndpointBehavior> , yapılandırma dosyasındaki ilgili yapılandırma bölümünde yalnızca geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-168">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="1a01b-169">`<schemaValidator>`İleti denetçisini yapılandıran öğe, sınıfı tarafından desteklenir `SchemaValidationBehaviorExtensionElement` .</span><span class="sxs-lookup"><span data-stu-id="1a01b-169">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="1a01b-170">Sınıfı, ve adlı iki Boole ortak özelliği kullanıma sunar `ValidateRequest` `ValidateReply` .</span><span class="sxs-lookup"><span data-stu-id="1a01b-170">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="1a01b-171">Bunların her ikisi de ile işaretlenir <xref:System.Configuration.ConfigurationPropertyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1a01b-171">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="1a01b-172">Bu öznitelik, önceki XML yapılandırma öğesinde görünebileceğiniz kod özellikleri ve XML öznitelikleri arasındaki bağlantıyı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-172">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="1a01b-173">Sınıfı ayrıca `Schemas` , ile birlikte işaretlenmiş ve bu örneğin bir parçası olan <xref:System.Configuration.ConfigurationCollectionAttribute> `SchemaCollection` ancak bu örnek, kısaltma için bu belgeden atlanan bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-173">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="1a01b-174">Koleksiyon ve koleksiyon öğesi sınıfıyla birlikte bu özellik, `SchemaConfigElement` `<schemas>` önceki yapılandırma parçacığındaki öğesini yedekler ve doğrulama kümesine bir şema koleksiyonu eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-174">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="1a01b-175">Geçersiz kılınan `CreateBehavior` Yöntem, bir istemci veya uç nokta oluştururken, çalışma zamanı yapılandırma verilerini değerlendirirken, yapılandırma verilerini bir davranış nesnesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1a01b-175">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="1a01b-176">Ileti Inspectors Imperatively ekleme</span><span class="sxs-lookup"><span data-stu-id="1a01b-176">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="1a01b-177">Öznitelikleri (daha önce, bu örnekte, daha önce alıntı yapılan nedenler için desteklenmez) ve yapılandırma dışında, davranışları, zorunlu kod kullanarak istemci ve hizmet çalışma zamanına oldukça kolay bir şekilde eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-177">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="1a01b-178">Bu örnekte, istemci uygulamasında istemci ileti denetçisini test etmek için bu yapılır.</span><span class="sxs-lookup"><span data-stu-id="1a01b-178">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="1a01b-179">`GenericClient`Sınıfı öğesinden türetilir <xref:System.ServiceModel.ClientBase%601> ve bu, uç nokta yapılandırmasını Kullanıcı koduna sunar.</span><span class="sxs-lookup"><span data-stu-id="1a01b-179">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="1a01b-180">İstemci örtük olarak açılmadan önce, aşağıdaki kodda gösterildiği gibi davranışları ekleyerek uç nokta yapılandırması değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-180">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="1a01b-181">Hizmetin davranışını eklemek burada gösterilen istemci tekniğinden büyük ölçüde eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-181">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a01b-182">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1a01b-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1a01b-183">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1a01b-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1a01b-184">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1a01b-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1a01b-185">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1a01b-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a01b-186">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a01b-186">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1a01b-187">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1a01b-187">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1a01b-188">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1a01b-188">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a01b-189">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1a01b-189">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
