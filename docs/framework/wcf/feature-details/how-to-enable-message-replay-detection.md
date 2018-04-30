---
title: 'Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cada24098f5800f56d7dd50119c3fe3394ba14cd
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="0e89f-102">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0e89f-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="0e89f-103">Yeniden yürütme saldırı bir saldırganın iki taraflar arasında iletileri akışı kopyalar ve bir veya daha fazla tarafların akışa başlayarak yeniden oynatılır oluşur.</span><span class="sxs-lookup"><span data-stu-id="0e89f-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="0e89f-104">Azaltıldığından sürece, bilgisayarlar saldırı tabi akış yasal iletileri, bir öğenin yedekli siparişleri gibi hatalı sonuçları aralığında kaynaklanan olarak işler.</span><span class="sxs-lookup"><span data-stu-id="0e89f-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="0e89f-105">İleti yeniden yürütme algılaması hakkında daha fazla bilgi için bkz: [ileti yeniden yürütme algılaması](http://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="0e89f-105">For more information about message replay detection, see [Message Replay Detection](http://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="0e89f-106">Aşağıdaki yordamda denetlemek için kullanabileceğiniz çeşitli özellikler yeniden yürütme algılaması kullanarak gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e89f-106">The following procedure demonstrates various properties that you can use to control replay detection using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="0e89f-107">Kod kullanılarak istemcide yeniden yürütme algılaması denetlemek için</span><span class="sxs-lookup"><span data-stu-id="0e89f-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="0e89f-108">Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> kullanmak için bir <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="0e89f-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="0e89f-109">Daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="0e89f-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="0e89f-110">Aşağıdaki örnek kullanan bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ile oluşturulan <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> , <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e89f-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="0e89f-111">Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> bir başvuru döndürmek için özellik <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> sınıfı ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0e89f-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  <span data-ttu-id="0e89f-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="0e89f-112">`DetectReplay`.</span></span> <span data-ttu-id="0e89f-113">Bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0e89f-113">A Boolean value.</span></span> <span data-ttu-id="0e89f-114">Bu istemci sunucudan yürütmelerini algılamak gerekmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="0e89f-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="0e89f-115">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0e89f-115">The default is `true`.</span></span>  
  
    2.  <span data-ttu-id="0e89f-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="0e89f-116">`MaxClockSkew`.</span></span> <span data-ttu-id="0e89f-117">A <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="0e89f-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="0e89f-118">Yeniden yürütme mekanizması istemci ve sunucu arasında dayanabileceği ne kadar süre eğme yönetir.</span><span class="sxs-lookup"><span data-stu-id="0e89f-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="0e89f-119">Güvenlik mekanizması zaman damgası gönderilen ve bu geri çok kadar geçmişte gönderilip gönderilmediğini belirler inceler.</span><span class="sxs-lookup"><span data-stu-id="0e89f-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="0e89f-120">Varsayılan değer 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="0e89f-120">The default is 5 minutes.</span></span>  
  
    3.  <span data-ttu-id="0e89f-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="0e89f-121">`ReplayWindow`.</span></span> <span data-ttu-id="0e89f-122">A `TimeSpan` değeri.</span><span class="sxs-lookup"><span data-stu-id="0e89f-122">A `TimeSpan` value.</span></span> <span data-ttu-id="0e89f-123">Bu ne kadar ileti yöneten sunucu (üzerinden aracılar) istemci ulaşmadan önce gönderdikten sonra ağda dinamik.</span><span class="sxs-lookup"><span data-stu-id="0e89f-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="0e89f-124">İstemci en son içinde gönderilen iletileri imzalarını izler `ReplayWindow` yeniden yürütme algılaması amacı.</span><span class="sxs-lookup"><span data-stu-id="0e89f-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  <span data-ttu-id="0e89f-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="0e89f-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="0e89f-126">Bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="0e89f-126">An integer value.</span></span> <span data-ttu-id="0e89f-127">İstemci ileti imzalarını bir önbellekte depolar.</span><span class="sxs-lookup"><span data-stu-id="0e89f-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="0e89f-128">Bu ayar, önbellekte saklayabilirsiniz kaç imzaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e89f-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="0e89f-129">Son yeniden yürütme pencereye gönderilen ileti sayısını önbellek sınırı ulaşırsa, en eski önbelleğe alınmış imzaları süre gelene kadar yeni iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="0e89f-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="0e89f-130">500000 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0e89f-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="0e89f-131">Kod kullanarak hizmet yeniden yürütme algılamayı denetlemek için</span><span class="sxs-lookup"><span data-stu-id="0e89f-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="0e89f-132">Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> kullanmak için bir <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="0e89f-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="0e89f-133">Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> bir başvuru döndürmek için özellik <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı ve daha önce açıklandığı gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e89f-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="0e89f-134">Yeniden yürütme algılaması istemci veya hizmet yapılandırmasında denetlemek için</span><span class="sxs-lookup"><span data-stu-id="0e89f-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="0e89f-135">Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0e89f-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="0e89f-136">Oluşturma bir `<security>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0e89f-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="0e89f-137">Oluşturma bir [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) veya [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="0e89f-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="0e89f-138">Aşağıdaki öznitelik değerlerini uygun şekilde ayarlayın: `detectReplays`, `maxClockSkew`, `replayWindow`, ve `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="0e89f-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="0e89f-139">Aşağıdaki örnek, her ikisi de özniteliklerini ayarlar bir `<localServiceSettings>` ve `<localClientSettings>` öğe:</span><span class="sxs-lookup"><span data-stu-id="0e89f-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="0e89f-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e89f-140">Example</span></span>  
 <span data-ttu-id="0e89f-141">Aşağıdaki örnekte bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> kullanarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi ve bağlama yeniden yürütme özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e89f-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="0e89f-142">Yeniden yürütme kapsamını: yalnızca ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="0e89f-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="0e89f-143">Aşağıdaki yordamlar yalnızca ileti güvenlik modu için geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e89f-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="0e89f-144">Taşıma ve ileti kimlik bilgileri modlarıyla aktarımı için aktarım düzeneklerini yürütmelerini algılamak.</span><span class="sxs-lookup"><span data-stu-id="0e89f-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="0e89f-145">Konuşma Notları güvenli</span><span class="sxs-lookup"><span data-stu-id="0e89f-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="0e89f-146">Güvenli konuşmaları etkinleştirmek için bağlamaları, hem uygulama kanalı yanı sıra güvenli konuşma başlatma bağlaması için bu ayarları ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e89f-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="0e89f-147">Örneğin, uygulama kanalı yürütmelerini kapatmak ancak güvenli Konuşmayla kuran önyükleme kanalı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0e89f-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="0e89f-148">Güvenli Konuşmayla oturumları kullanıyorsanız değil, yeniden yürütme algılaması sunucu grubu senaryolarını ve ne zaman işlem geri dönüştürülmeden yürütmelerini algılamak garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="0e89f-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="0e89f-149">Bu, aşağıdaki sistem tarafından sağlanan bağlamaları için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0e89f-149">This applies to the following system-provided bindings:</span></span>  
  
-   <span data-ttu-id="0e89f-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0e89f-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
-   <span data-ttu-id="0e89f-151"><xref:System.ServiceModel.WSHttpBinding> ile <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="0e89f-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e89f-152">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e89f-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0e89f-153">Şu ad alanlarından Kodu derlemek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0e89f-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="0e89f-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e89f-154">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="0e89f-155">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="0e89f-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [<span data-ttu-id="0e89f-156">\<localClientSettings ></span><span class="sxs-lookup"><span data-stu-id="0e89f-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [<span data-ttu-id="0e89f-157">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e89f-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
