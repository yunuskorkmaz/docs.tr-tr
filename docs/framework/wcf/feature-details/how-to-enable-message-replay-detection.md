---
title: 'Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: c99500a3d4dc0bd8abe7062f23e064d395cadf36
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557885"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="e0c60-102">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e0c60-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="e0c60-103">Bir saldırgan iki taraf arasında bir ileti akışını kopyaladığında veya bir veya daha fazla tarafın akışını yeniden oynadığında bir yeniden yürütme saldırısı meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="e0c60-104">Hafiflemediği sürece, saldırıya tabi olan bilgisayarlar akışı meşru iletiler olarak işleyecek ve bu da bir öğenin gereksiz sıraları gibi hatalı sonuçlar oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e0c60-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="e0c60-105">İleti yeniden yürütme algılaması hakkında daha fazla bilgi için bkz. [ileti yeniden yürütme algılaması](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e0c60-105">For more information about message replay detection, see [Message Replay Detection](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="e0c60-106">Aşağıdaki yordamda Windows Communication Foundation (WCF) kullanarak yeniden yürütme algılamasını denetlemek için kullanabileceğiniz çeşitli özellikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="e0c60-107">Kodu kullanarak istemcide yeniden yürütme algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="e0c60-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="e0c60-108"><xref:System.ServiceModel.Channels.SecurityBindingElement>Bir içinde kullanmak için oluşturun <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="e0c60-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="e0c60-109">Daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="e0c60-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="e0c60-110">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfının ile oluşturulmuş bir öğesini kullanır <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="e0c60-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="e0c60-111"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>Sınıfına bir başvuru döndürmek <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlamak için özelliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="e0c60-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="e0c60-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="e0c60-112">`DetectReplay`.</span></span> <span data-ttu-id="e0c60-113">Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e0c60-113">A Boolean value.</span></span> <span data-ttu-id="e0c60-114">Bu, istemcinin sunucudan yeniden yürütme algılaması gerekip gerekmediğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="e0c60-115">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="e0c60-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="e0c60-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="e0c60-116">`MaxClockSkew`.</span></span> <span data-ttu-id="e0c60-117">Bir <xref:System.TimeSpan> değer.</span><span class="sxs-lookup"><span data-stu-id="e0c60-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="e0c60-118">Yeniden yürütme mekanizmasına ne kadar eğinin istemci ile sunucu arasında ne kadar zaman harcamaya harcanabileceği yönetir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="e0c60-119">Güvenlik mekanizması gönderilen zaman damgasını inceler ve geçmişte daha fazla geri gönderilip gönderilmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e0c60-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="e0c60-120">Varsayılan değer 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="e0c60-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="e0c60-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="e0c60-121">`ReplayWindow`.</span></span> <span data-ttu-id="e0c60-122">Bir `TimeSpan` değer.</span><span class="sxs-lookup"><span data-stu-id="e0c60-122">A `TimeSpan` value.</span></span> <span data-ttu-id="e0c60-123">Bu, istemciye ulaşmadan önce bir iletinin ağ üzerinde ne kadar süreyle (aracılar aracılığıyla) ne kadar sürdüğünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="e0c60-124">İstemci, yeniden yürütme algılaması amacıyla en son içinde gönderilen iletilerin imzalarını izler `ReplayWindow` .</span><span class="sxs-lookup"><span data-stu-id="e0c60-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="e0c60-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="e0c60-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="e0c60-126">Bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="e0c60-126">An integer value.</span></span> <span data-ttu-id="e0c60-127">İstemci, iletinin imzalarını bir önbellekte depolar.</span><span class="sxs-lookup"><span data-stu-id="e0c60-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="e0c60-128">Bu ayar önbelleğin kaç tane imza depolayabileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="e0c60-129">Son yeniden yürütme penceresi içinde gönderilen ileti sayısı önbellek sınırına ulaşırsa, en eski önbelleğe alınan imzaların zaman sınırına ulaşması için yeni iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="e0c60-130">Varsayılan değer 500000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e0c60-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="e0c60-131">Kodu kullanarak hizmette yeniden yürütme algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="e0c60-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="e0c60-132"><xref:System.ServiceModel.Channels.SecurityBindingElement>Bir içinde kullanmak için oluşturun <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="e0c60-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="e0c60-133"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>Sınıfına bir başvuru döndürmek <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> ve daha önce açıklandığı gibi özellikleri ayarlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0c60-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="e0c60-134">İstemci veya hizmet yapılandırmasında yeniden yürütme algılamayı denetlemek için</span><span class="sxs-lookup"><span data-stu-id="e0c60-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="e0c60-135">Oluşturun [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e0c60-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="e0c60-136">Bir `<security>` öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0c60-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="e0c60-137">Veya oluşturun [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e0c60-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="e0c60-138">Aşağıdaki öznitelik değerlerini uygun şekilde ayarlayın: `detectReplays` , `maxClockSkew` , `replayWindow` ve `replayCacheSize` .</span><span class="sxs-lookup"><span data-stu-id="e0c60-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="e0c60-139">Aşağıdaki örnek, ve öğelerinin özniteliklerini ayarlar `<localServiceSettings>` `<localClientSettings>` :</span><span class="sxs-lookup"><span data-stu-id="e0c60-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e0c60-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0c60-140">Example</span></span>  
 <span data-ttu-id="e0c60-141">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> yöntemini kullanarak bir oluşturur <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> ve bağlamanın yeniden yürütme özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0c60-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="e0c60-142">Yeniden yürütme kapsamı: yalnızca Ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="e0c60-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="e0c60-143">Aşağıdaki yordamların yalnızca Ileti güvenliği modu için uygulanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0c60-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="e0c60-144">Ileti kimlik bilgileri modlarıyla taşıma ve taşıma için, aktarım mekanizmaları yeniden oynatılır.</span><span class="sxs-lookup"><span data-stu-id="e0c60-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="e0c60-145">Güvenli konuşma notları</span><span class="sxs-lookup"><span data-stu-id="e0c60-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="e0c60-146">Güvenli konuşmaları etkinleştiren bağlamalar için, bu ayarları hem uygulama kanalında hem de güvenli konuşma önyükleme bağlaması için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0c60-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="e0c60-147">Örneğin, uygulama kanalı için yeniden oynatılamayı kapatabilir, ancak bunları güvenli konuşmayı kuran önyükleme kanalı için etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0c60-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="e0c60-148">Güvenli konuşma oturumlarını kullanmıyorsanız, yeniden yürütme algılaması, sunucu grubu senaryolarında ve işlem geri dönüştürüldüğünde yeniden yürütmenin saptanmasını garantilemez.</span><span class="sxs-lookup"><span data-stu-id="e0c60-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="e0c60-149">Bu, sistem tarafından belirtilen aşağıdaki bağlamalar için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="e0c60-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="e0c60-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e0c60-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="e0c60-151"><xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A>özelliği olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="e0c60-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0c60-152">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e0c60-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="e0c60-153">Kodu derlemek için aşağıdaki ad alanları gereklidir:</span><span class="sxs-lookup"><span data-stu-id="e0c60-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="e0c60-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c60-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="e0c60-155">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="e0c60-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="e0c60-156">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0c60-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
