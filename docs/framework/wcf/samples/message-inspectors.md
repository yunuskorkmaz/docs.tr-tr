---
title: "İleti Denetçileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ed4f31e004ddeb69a29568b3892ab7379715457
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="message-inspectors"></a><span data-ttu-id="c7492-102">İleti Denetçileri</span><span class="sxs-lookup"><span data-stu-id="c7492-102">Message Inspectors</span></span>
<span data-ttu-id="c7492-103">Bu örnek, uygulama ve hizmet ve istemci ileti denetçileri yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7492-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="c7492-104">Bir ileti denetçisi hizmet modelinin istemci çalışma zamanında kullanılan bir genişletilebilirlik nesne ve gönderme çalışma zamanı program aracılığıyla veya yapılandırma ve inceleyin ve iletileri alındıktan sonra veya gönderilmeden önce değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="c7492-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="c7492-105">Bu örnek, bir temel istemci ve gelen iletileri bir dizi yapılandırılabilir XML Şeması belgeler karşı doğrular hizmet ileti doğrulama mekanizması uygular.</span><span class="sxs-lookup"><span data-stu-id="c7492-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="c7492-106">Bu örnekte her bir işlemin iletileri doğrulamaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7492-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="c7492-107">Bu kasıtlı basitleştirme olur.</span><span class="sxs-lookup"><span data-stu-id="c7492-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="c7492-108">İleti denetçisi</span><span class="sxs-lookup"><span data-stu-id="c7492-108">Message Inspector</span></span>  
 <span data-ttu-id="c7492-109">İstemci ileti denetçiler uygulama <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimi ve hizmet ileti denetçiler uygulama <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c7492-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="c7492-110">Uygulamaları için iki tarafı da çalışır bir ileti denetçisi oluşturmak için tek bir sınıfta birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="c7492-111">Bu örnek, bu tür bir birleştirilmiş ileti denetçisi uygular.</span><span class="sxs-lookup"><span data-stu-id="c7492-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="c7492-112">Inspector göre gelen ve giden iletiler doğrulanma şemaları kümesinde geçirme oluşturulur ve gelen veya giden iletiler olup olmadığı doğrulanır ve Inspector gönderme veya istemci modunda olup olmadığını belirlemek Geliştirici sağlar; hata işleme, bu konunun ilerleyen bölümlerinde açıklandığı gibi etkiler.</span><span class="sxs-lookup"><span data-stu-id="c7492-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7492-113">Tüm hizmet (gönderen) iletiyi denetçisi iki uygulamalıdır <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> yöntemleri <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="c7492-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="c7492-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>seri durumdan ve işlem için gönderilen önce bir ileti alındı, kanal yığını tarafından işlenen ve bir hizmete atanan olduğunda, ancak gönderici tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7492-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="c7492-115">Gelen ileti şifrelenmişse, ileti denetçisi ulaştığında, ileti zaten şifresi çözülür.</span><span class="sxs-lookup"><span data-stu-id="c7492-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="c7492-116">Yöntemi alır `request` ileti geçirilen Denetlenmekte, yönetilebilir veya gerektiğinde yerini iletiye sağlayan bir başvuru parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="c7492-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="c7492-117">Dönüş değeri gibi herhangi bir nesne olabilir ve geçirilen bağıntı durumu nesnesi olarak kullanılan <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> hizmeti geçerli iletiye yanıt döndüğünde.</span><span class="sxs-lookup"><span data-stu-id="c7492-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="c7492-118">Bu örnekte <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> özel, yerel yöntemine iletisinin denetleme (doğrulama) Temsilciler `ValidateMessageBody` ve hiçbir bağıntı durum nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7492-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="c7492-119">Bu yöntem geçersiz ileti hizmete geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7492-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7492-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>bir yanıt gelen ileti işlendiğinde bir istemciye ya da tek yönlü iletileri, söz konusu olduğunda gönderilmek üzere hazır olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7492-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="c7492-121">Bu bağımsız olarak MEP simetrik, çağrılan saymak uzantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7492-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="c7492-122">İle <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, ileti başvuru parametre olarak geçirilir ve Denetlenmekte, değiştirilebilir veya değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c7492-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="c7492-123">Bu örnekte gerçekleştirilen ileti doğrulama yeniden için temsilci `ValidMessageBody` yöntemi, ancak doğrulama hatalarının işlenmesini biraz farklı bu durumda.</span><span class="sxs-lookup"><span data-stu-id="c7492-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="c7492-124">Hizmette bir doğrulama hatası oluşursa, `ValidateMessageBody` yöntemi atar <xref:System.ServiceModel.FaultException>-özel durumları türetilmiş.</span><span class="sxs-lookup"><span data-stu-id="c7492-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="c7492-125">İçinde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, bu özel durumlar burada bunlar otomatik olarak SOAP hataları dönüştürülen ve istemciye geçişli hizmet modeli altyapısı içine koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7492-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="c7492-126">İçinde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> özel durumlar gerekir değil put altyapısını, ileti denetçisi çağrılmadan önce hizmeti tarafından oluşturulan hataya özel durumları dönüştürme oluştuğundan.</span><span class="sxs-lookup"><span data-stu-id="c7492-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="c7492-127">Bu nedenle aşağıdaki uygulama bilinen yakalar `ReplyValidationFault` özel durumu ve yanıt iletisi bir açık hata iletisi ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c7492-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="c7492-128">Bu yöntem geçersiz ileti hizmeti uygulaması tarafından döndürülür sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7492-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7492-129">İstemci ileti denetçisi çok benzer.</span><span class="sxs-lookup"><span data-stu-id="c7492-129">The client message inspector is very similar.</span></span> <span data-ttu-id="c7492-130">Gelen uygulanmalı iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> olan <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> ve <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7492-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="c7492-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>ileti istemci uygulaması veya işlem biçimlendirici tarafından oluşan olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7492-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="c7492-132">İleti dağıtıcısı ileti denetçileri ile henüz olarak Denetlenmekte veya tamamen değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="c7492-133">Bu örnekte, denetçisi temsilciler aynı yerel `ValidateMessageBody` gönderme ileti denetçileri için de kullanılır yardımcı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7492-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="c7492-134">Davranış (oluşturucuda belirtildiği şekilde) istemci ve hizmet doğrulama arasında istemci doğrulama kullanıcı koda yerel olarak gerçekleştirildiği için ve bir hizmet hatası nedeniyle değil put yerel özel durumları oluşturur farktır.</span><span class="sxs-lookup"><span data-stu-id="c7492-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="c7492-135">Genellikle, hizmet dağıtıcısı denetçiler hataları throw ve istemci denetçiler özel durumlar oluşturma kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="c7492-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="c7492-136">Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulaması sağlar geçersiz ileti hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="c7492-137">`AfterReceiveReply` Uygulama hizmetinden alınan hiçbir geçersiz ileti için istemci kullanıcı koduna geçirilen sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7492-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="c7492-138">Bu belirli ileti denetçisinin Kalp olan `ValidateMessageBody` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7492-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="c7492-139">Kendi işlerini yapmak için bir doğrulama sarmaladığı <xref:System.Xml.XmlReader> gövde içerik alt ağaç geçirilen iletinin geçici.</span><span class="sxs-lookup"><span data-stu-id="c7492-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="c7492-140">Okuyucu ileti denetçisi tutan şemaları kümesi ile doldurulur ve doğrulama geri çağırma başvuran bir temsilci Ayarla `InspectionValidationHandler` yanı sıra bu yöntem tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c7492-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="c7492-141">Doğrulamayı gerçekleştirmek için ileti ardından okuma ve bir akış destekli belleğe Biriktiricideki <xref:System.Xml.XmlDictionaryWriter>.</span><span class="sxs-lookup"><span data-stu-id="c7492-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="c7492-142">Bir doğrulama hata veya uyarı işleminde ortaya çıkarsa, geri çağırma yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7492-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="c7492-143">Herhangi bir hata oluşursa, yeni bir ileti özellikleri ve üstbilgileri özgün iletiden kopyalar ve şimdi doğrulanmış bilgi tarafından Sarmalanan bellek akışında kullanan oluşturulan bir <xref:System.Xml.XmlDictionaryReader> ve değiştirme iletiye eklendi.</span><span class="sxs-lookup"><span data-stu-id="c7492-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7492-144">`InspectionValidationHandler` Doğrulayarak yöntemi çağrıldığında <xref:System.Xml.XmlReader> şema doğrulama hata veya uyarı olduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7492-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="c7492-145">Aşağıdaki uygulama yalnızca hatalarla çalışır ve tüm uyarıları yok sayar.</span><span class="sxs-lookup"><span data-stu-id="c7492-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="c7492-146">İlk konusuna göre bir doğrulama eklemesine olası görünebilir <xref:System.Xml.XmlReader> doğrulama ileti denetçisi ve let iletisine, ileti işleme ve ileti arabelleğe alma olmadan gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c7492-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="c7492-147">Geçersiz XML düğümlerini algılandığında, beklenmeyen bir davranışa kaynaklanan ancak, bu geri çağırma doğrulama istisnalarını hizmete yere atar anlamına gelir altyapı veya kullanıcı kodu model.</span><span class="sxs-lookup"><span data-stu-id="c7492-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="c7492-148">Arabelleğe alma yaklaşım geçersiz iletileri kullanıcı kodundan tamamen ayrıntılarından korur.</span><span class="sxs-lookup"><span data-stu-id="c7492-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="c7492-149">Daha önce ele alındığı gibi istemci ile hizmet arasında işleyici tarafından oluşturulan özel durumlar değişir.</span><span class="sxs-lookup"><span data-stu-id="c7492-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="c7492-150">Özel durumlar türetilir hizmette <xref:System.ServiceModel.FaultException>, istemcide normal özel durumları durumlardır.</span><span class="sxs-lookup"><span data-stu-id="c7492-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
```  
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
  
## <a name="behavior"></a><span data-ttu-id="c7492-151">Davranış</span><span class="sxs-lookup"><span data-stu-id="c7492-151">Behavior</span></span>  
 <span data-ttu-id="c7492-152">İleti denetçileri istemci çalışma zamanı veya gönderme çalışma zamanı uzantılarıdır.</span><span class="sxs-lookup"><span data-stu-id="c7492-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="c7492-153">Bu tür uzantılar kullanılarak yapılandırılmış olan *davranışları*.</span><span class="sxs-lookup"><span data-stu-id="c7492-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="c7492-154">Bir davranış için (örneğin, ileti denetçileri) uzantıları ekleme veya varsayılan yapılandırmayı değiştirme tarafından hizmet modeli çalışma zamanı davranışını değiştiren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="c7492-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="c7492-155">Aşağıdaki `SchemaValidationBehavior` için kullanılır. Bu örneği ait ileti denetçisi istemciye ekleyin veya çalışma zamanı gönderme davranışı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="c7492-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="c7492-156">Her iki durumda da yerine temel uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7492-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="c7492-157">İçinde <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> ve <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, ileti denetçisi oluşturulur ve eklenen <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> ilgili çalışma zamanı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c7492-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
```  
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
>  <span data-ttu-id="c7492-158">Bu belirli davranışı bir özniteliği olarak çift değil ve bu nedenle bildirimli olarak bir hizmet türünün anlaşma türünü eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c7492-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="c7492-159">Şema koleksiyonu bir öznitelik bildiriminde yüklenemiyor ve bu öznitelik (örneğin için uygulama ayarları) bir ek yapılandırma konuma başvuran yapılandırma öğesi oluşturma anlamına gelir çünkü yapılan tasarım kararı budur hizmet modeli yapılandırma geri kalanı ile tutarlı değil.</span><span class="sxs-lookup"><span data-stu-id="c7492-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="c7492-160">Bu nedenle, bu davranış yalnızca imperatively bir hizmet modeli yapılandırma uzantısı ve kod aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="c7492-161">Yapılandırma yoluyla ileti denetçisi ekleme</span><span class="sxs-lookup"><span data-stu-id="c7492-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="c7492-162">Uygulama yapılandırma dosyasında bir uç noktada özel davranışı yapılandırmak için hizmet modeli yapılandırma oluşturmak Implementers gerektirir *uzantı öğesi* türetilmiş bir sınıf tarafından temsil edilen <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span><span class="sxs-lookup"><span data-stu-id="c7492-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="c7492-163">Bu uzantı sonra uzantıları için hizmet modeli yapılandırma bölümü için bu bölümde ele alınan aşağıdaki uzantısı gösterildiği gibi eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7492-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
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
  
 <span data-ttu-id="c7492-164">Uzantılar uygulama ya da en yaygın seçimdir, ASP.NET yapılandırma dosyası veya makine yapılandırma dosyası eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="c7492-165">Uzantısı yapılandırma kapsamına eklendiğinde, aşağıdaki kodda gösterildiği gibi bir davranış yapılandırma davranışı eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="c7492-166">Davranış, gerektiği gibi birden çok uç nokta uygulanabilir yeniden kullanılabilir öğeleri bağlantılardır.</span><span class="sxs-lookup"><span data-stu-id="c7492-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="c7492-167">Olmasını belirli davranışı uygular burada yapılandırılan çünkü <xref:System.ServiceModel.Description.IEndpointBehavior>, yalnızca yapılandırma dosyasındaki ilgili yapılandırma bölümünde geçerli olduğundan.</span><span class="sxs-lookup"><span data-stu-id="c7492-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c7492-168">`<schemaValidator>` İleti denetçisi yapılandırır öğesi tarafından desteklenen `SchemaValidationBehaviorExtensionElement` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7492-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="c7492-169">Sınıf adlı iki Boole ortak özellikleri kullanıma sunan `ValidateRequest` ve `ValidateReply`.</span><span class="sxs-lookup"><span data-stu-id="c7492-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="c7492-170">Bunların her ikisi de ile işaretlenmiş bir <xref:System.Configuration.ConfigurationPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c7492-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="c7492-171">Bu öznitelik kod özellikleri ve önceki XML yapılandırma öğesinde görülebilir XML öznitelikleri arasındaki bağlantıyı meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="c7492-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="c7492-172">Sınıfı ayrıca bir özelliğe sahiptir `Schemas` ek olarak işaretlenen ile <xref:System.Configuration.ConfigurationCollectionAttribute> ve türü `SchemaCollection`, olduğu da kısaltma bu belgeden belirtilmemişse ancak bu örnek bir parçası.</span><span class="sxs-lookup"><span data-stu-id="c7492-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="c7492-173">Bu özellik koleksiyonu ve koleksiyon öğesi sınıfı ile birlikte `SchemaConfigElement` yedekler `<schemas>` önceki yapılandırma parçacığı öğesinde ve şemalar topluluğu doğrulama kümesine eklemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="c7492-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="c7492-174">Geçersiz kılınan `CreateBehavior` yöntemi bir istemci veya uç yapılar gibi çalışma zamanı yapılandırma verilerini değerlendirirken, bu yapılandırma verilerini bir davranış nesnesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c7492-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
```  
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
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="c7492-175">İleti denetçileri Imperatively ekleme</span><span class="sxs-lookup"><span data-stu-id="c7492-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="c7492-176">(Bu örnekte önceden bildirdi nedeni desteklenmez) öznitelikleri ve yapılandırma yoluyla, davranışları oldukça kolaylıkla kesinlik temelli kod kullanarak bir istemci ve hizmet çalışma zamanı için eklenebilir dışında.</span><span class="sxs-lookup"><span data-stu-id="c7492-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="c7492-177">Bu örnekte, bu istemci ileti denetçisi test etmek için istemci uygulamasında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="c7492-178">`GenericClient` Sınıfı türetilir <xref:System.ServiceModel.ClientBase%601>, kullanıcı kodu için uç nokta yapılandırması kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c7492-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="c7492-179">İstemci örtük olarak açılmadan önce uç nokta yapılandırması, örneğin aşağıdaki kodda gösterildiği gibi davranışları ekleyerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="c7492-180">Hizmette davranışı eklemek, burada gösterilen istemci teknik büyük ölçüde eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7492-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7492-181">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c7492-181">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c7492-182">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7492-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c7492-183">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7492-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c7492-184">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7492-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7492-185">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7492-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7492-186">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c7492-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7492-187">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c7492-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7492-188">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c7492-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
  
## <a name="see-also"></a><span data-ttu-id="c7492-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7492-189">See Also</span></span>
