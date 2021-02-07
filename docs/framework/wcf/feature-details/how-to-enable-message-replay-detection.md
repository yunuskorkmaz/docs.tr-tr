---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Ileti yeniden yürütme algılamayı etkinleştirme'
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
ms.openlocfilehash: 743452195d5bf78360909a22ea81997c2712dd06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704673"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="3d39a-103">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3d39a-103">How to: Enable Message Replay Detection</span></span>

<span data-ttu-id="3d39a-104">Bir saldırgan iki taraf arasında bir ileti akışını kopyaladığında veya bir veya daha fazla tarafın akışını yeniden oynadığında bir yeniden yürütme saldırısı meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-104">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="3d39a-105">Hafiflemediği sürece, saldırıya tabi olan bilgisayarlar akışı meşru iletiler olarak işleyecek ve bu da bir öğenin gereksiz sıraları gibi hatalı sonuçlar oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3d39a-105">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="3d39a-106">İleti yeniden yürütme algılaması hakkında daha fazla bilgi için bkz. [ileti yeniden yürütme algılaması](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="3d39a-106">For more information about message replay detection, see [Message Replay Detection](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="3d39a-107">Aşağıdaki yordamda Windows Communication Foundation (WCF) kullanarak yeniden yürütme algılamasını denetlemek için kullanabileceğiniz çeşitli özellikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-107">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="3d39a-108">Kodu kullanarak istemcide yeniden yürütme algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="3d39a-108">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="3d39a-109"><xref:System.ServiceModel.Channels.SecurityBindingElement>Bir içinde kullanmak için oluşturun <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="3d39a-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="3d39a-110">Daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="3d39a-110">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="3d39a-111">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> sınıfının ile oluşturulmuş bir öğesini kullanır <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="3d39a-111">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="3d39a-112"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>Sınıfına bir başvuru döndürmek <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlamak için özelliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="3d39a-112">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="3d39a-113">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="3d39a-113">`DetectReplay`.</span></span> <span data-ttu-id="3d39a-114">Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="3d39a-114">A Boolean value.</span></span> <span data-ttu-id="3d39a-115">Bu, istemcinin sunucudan yeniden yürütme algılaması gerekip gerekmediğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-115">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="3d39a-116">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="3d39a-116">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="3d39a-117">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="3d39a-117">`MaxClockSkew`.</span></span> <span data-ttu-id="3d39a-118">Bir <xref:System.TimeSpan> değer.</span><span class="sxs-lookup"><span data-stu-id="3d39a-118">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="3d39a-119">Yeniden yürütme mekanizmasına ne kadar eğinin istemci ile sunucu arasında ne kadar zaman harcamaya harcanabileceği yönetir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-119">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="3d39a-120">Güvenlik mekanizması gönderilen zaman damgasını inceler ve geçmişte daha fazla geri gönderilip gönderilmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="3d39a-120">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="3d39a-121">Varsayılan değer 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="3d39a-121">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="3d39a-122">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="3d39a-122">`ReplayWindow`.</span></span> <span data-ttu-id="3d39a-123">Bir `TimeSpan` değer.</span><span class="sxs-lookup"><span data-stu-id="3d39a-123">A `TimeSpan` value.</span></span> <span data-ttu-id="3d39a-124">Bu, istemciye ulaşmadan önce bir iletinin ağ üzerinde ne kadar süreyle (aracılar aracılığıyla) ne kadar sürdüğünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-124">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="3d39a-125">İstemci, yeniden yürütme algılaması amacıyla en son içinde gönderilen iletilerin imzalarını izler `ReplayWindow` .</span><span class="sxs-lookup"><span data-stu-id="3d39a-125">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="3d39a-126">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="3d39a-126">`ReplayCacheSize`.</span></span> <span data-ttu-id="3d39a-127">Bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="3d39a-127">An integer value.</span></span> <span data-ttu-id="3d39a-128">İstemci, iletinin imzalarını bir önbellekte depolar.</span><span class="sxs-lookup"><span data-stu-id="3d39a-128">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="3d39a-129">Bu ayar önbelleğin kaç tane imza depolayabileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-129">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="3d39a-130">Son yeniden yürütme penceresi içinde gönderilen ileti sayısı önbellek sınırına ulaşırsa, en eski önbelleğe alınan imzaların zaman sınırına ulaşması için yeni iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-130">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="3d39a-131">Varsayılan değer 500000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3d39a-131">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="3d39a-132">Kodu kullanarak hizmette yeniden yürütme algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="3d39a-132">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="3d39a-133"><xref:System.ServiceModel.Channels.SecurityBindingElement>Bir içinde kullanmak için oluşturun <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="3d39a-133">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="3d39a-134"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>Sınıfına bir başvuru döndürmek <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> ve daha önce açıklandığı gibi özellikleri ayarlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d39a-134">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="3d39a-135">İstemci veya hizmet yapılandırmasında yeniden yürütme algılamayı denetlemek için</span><span class="sxs-lookup"><span data-stu-id="3d39a-135">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="3d39a-136">Oluşturun [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3d39a-136">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="3d39a-137">Bir `<security>` öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3d39a-137">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="3d39a-138">Veya oluşturun [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="3d39a-138">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="3d39a-139">Aşağıdaki öznitelik değerlerini uygun şekilde ayarlayın: `detectReplays` , `maxClockSkew` , `replayWindow` ve `replayCacheSize` .</span><span class="sxs-lookup"><span data-stu-id="3d39a-139">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="3d39a-140">Aşağıdaki örnek, ve öğelerinin özniteliklerini ayarlar `<localServiceSettings>` `<localClientSettings>` :</span><span class="sxs-lookup"><span data-stu-id="3d39a-140">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3d39a-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d39a-141">Example</span></span>  

 <span data-ttu-id="3d39a-142">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> yöntemini kullanarak bir oluşturur <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> ve bağlamanın yeniden yürütme özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3d39a-142">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="3d39a-143">Yeniden yürütme kapsamı: yalnızca Ileti güvenliği</span><span class="sxs-lookup"><span data-stu-id="3d39a-143">Scope of Replay: Message Security Only</span></span>  

 <span data-ttu-id="3d39a-144">Aşağıdaki yordamların yalnızca Ileti güvenliği modu için uygulanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3d39a-144">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="3d39a-145">Ileti kimlik bilgileri modlarıyla taşıma ve taşıma için, aktarım mekanizmaları yeniden oynatılır.</span><span class="sxs-lookup"><span data-stu-id="3d39a-145">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="3d39a-146">Güvenli konuşma notları</span><span class="sxs-lookup"><span data-stu-id="3d39a-146">Secure Conversation Notes</span></span>  

 <span data-ttu-id="3d39a-147">Güvenli konuşmaları etkinleştiren bağlamalar için, bu ayarları hem uygulama kanalında hem de güvenli konuşma önyükleme bağlaması için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d39a-147">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="3d39a-148">Örneğin, uygulama kanalı için yeniden oynatılamayı kapatabilir, ancak bunları güvenli konuşmayı kuran önyükleme kanalı için etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d39a-148">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="3d39a-149">Güvenli konuşma oturumlarını kullanmıyorsanız, yeniden yürütme algılaması, sunucu grubu senaryolarında ve işlem geri dönüştürüldüğünde yeniden yürütmenin saptanmasını garantilemez.</span><span class="sxs-lookup"><span data-stu-id="3d39a-149">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="3d39a-150">Bu, sistem tarafından belirtilen aşağıdaki bağlamalar için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="3d39a-150">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="3d39a-151"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3d39a-151"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="3d39a-152"><xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A>özelliği olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="3d39a-152"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d39a-153">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3d39a-153">Compiling the Code</span></span>  
  
- <span data-ttu-id="3d39a-154">Kodu derlemek için aşağıdaki ad alanları gereklidir:</span><span class="sxs-lookup"><span data-stu-id="3d39a-154">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="3d39a-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d39a-155">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="3d39a-156">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="3d39a-156">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="3d39a-157">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d39a-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
