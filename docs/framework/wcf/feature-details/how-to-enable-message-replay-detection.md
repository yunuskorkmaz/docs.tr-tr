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
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184947"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="80ab6-102">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="80ab6-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="80ab6-103">Bir yeniden oynatma saldırısı, bir saldırgan iki taraf arasındaki ileti akışını kopyaladığında ve akışı taraflardan birine veya daha fazlasına yeniden oynattığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="80ab6-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="80ab6-104">Azaltılmadığı sürece, saldırıya maruz kalan bilgisayarlar akışı meşru iletiler olarak işleyerek bir öğenin gereksiz siparişleri gibi bir dizi kötü sonuca yol açacaktır.</span><span class="sxs-lookup"><span data-stu-id="80ab6-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="80ab6-105">İleti yeniden oynatma algılama hakkında daha fazla bilgi için ileti [yeniden oynatma algılama](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10))konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="80ab6-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="80ab6-106">Aşağıdaki yordam, Windows Communication Foundation (WCF) kullanarak yeniden oynatma algılamasını denetlemek için kullanabileceğiniz çeşitli özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="80ab6-107">Kodu kullanarak istemcide yeniden oynatma algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="80ab6-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="80ab6-108">Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> 'de kullanılacak <xref:System.ServiceModel.Channels.CustomBinding>bir şey oluşturun</span><span class="sxs-lookup"><span data-stu-id="80ab6-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="80ab6-109">Daha fazla bilgi için [bkz: SecurityBindingElement kullanarak Özel Bağlama oluşturun.](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)</span><span class="sxs-lookup"><span data-stu-id="80ab6-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="80ab6-110">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfın bir ile oluşturulan kullanır.</span><span class="sxs-lookup"><span data-stu-id="80ab6-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="80ab6-111">Sınıfa <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> bir başvuru döndürmek ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlamak için özelliği kullanın: <xref:System.ServiceModel.Channels.LocalClientSecuritySettings></span><span class="sxs-lookup"><span data-stu-id="80ab6-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="80ab6-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="80ab6-112">`DetectReplay`.</span></span> <span data-ttu-id="80ab6-113">Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="80ab6-113">A Boolean value.</span></span> <span data-ttu-id="80ab6-114">Bu, istemcinin sunucudan yeniden oynatma algılayıp algılamaması gerektiğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="80ab6-115">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="80ab6-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="80ab6-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="80ab6-116">`MaxClockSkew`.</span></span> <span data-ttu-id="80ab6-117">Bir <xref:System.TimeSpan> değer.</span><span class="sxs-lookup"><span data-stu-id="80ab6-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="80ab6-118">Yeniden oynatma mekanizmasının istemci ve sunucu arasında ne kadar zaman çarpıtabileceğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="80ab6-119">Güvenlik mekanizması, gönderilen zaman damgasını inceler ve geçmişte çok uzağa gönderilip gönderilmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="80ab6-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="80ab6-120">Varsayılan değer 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="80ab6-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="80ab6-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="80ab6-121">`ReplayWindow`.</span></span> <span data-ttu-id="80ab6-122">Bir `TimeSpan` değer.</span><span class="sxs-lookup"><span data-stu-id="80ab6-122">A `TimeSpan` value.</span></span> <span data-ttu-id="80ab6-123">Bu, sunucu istemciye ulaşmadan önce iletinin (aracılar aracılığıyla) gönderdikten sonra ağda ne kadar süre yle yaşayabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="80ab6-124">İstemci, yeniden oynatma algılama amacıyla en `ReplayWindow` son gönderilen iletilerin imzalarını izler.</span><span class="sxs-lookup"><span data-stu-id="80ab6-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="80ab6-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="80ab6-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="80ab6-126">Bir sayı değeri.</span><span class="sxs-lookup"><span data-stu-id="80ab6-126">An integer value.</span></span> <span data-ttu-id="80ab6-127">İstemci iletinin imzalarını bir önbellekte depolar.</span><span class="sxs-lookup"><span data-stu-id="80ab6-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="80ab6-128">Bu ayar, önbelleğin depolayabileceği kaç imza olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="80ab6-129">Son yeniden oynatma penceresinde gönderilen ileti sayısı önbellek sınırına ulaşırsa, önbelleğe alınan en eski imzalar zaman sınırına ulaşana kadar yeni iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="80ab6-130">Varsayılan değer 500000'dir.</span><span class="sxs-lookup"><span data-stu-id="80ab6-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="80ab6-131">Kodu kullanarak hizmette yeniden oynatma algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="80ab6-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="80ab6-132">Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> 'de kullanılacak <xref:System.ServiceModel.Channels.CustomBinding>bir şey oluşturun</span><span class="sxs-lookup"><span data-stu-id="80ab6-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="80ab6-133">Sınıfa <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> bir başvuru döndürmek için özelliği kullanın ve özellikleri daha önce açıklandığı gibi ayarlayın. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings></span><span class="sxs-lookup"><span data-stu-id="80ab6-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="80ab6-134">İstemci veya hizmet için yapılandırmada yeniden oynatma algılamasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="80ab6-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="80ab6-135">[ \<Özelbağlayıcı>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80ab6-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="80ab6-136">Bir `<security>` öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80ab6-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="80ab6-137">[ \<Yerel](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) bir Müşteri Ayarları>veya [ \<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80ab6-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="80ab6-138">Aşağıdaki öznitelik değerlerini uygun şekilde `detectReplays` `maxClockSkew`ayarlayın: , , `replayWindow`ve `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="80ab6-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="80ab6-139">Aşağıdaki örnek, hem a `<localServiceSettings>` hem `<localClientSettings>` de bir öğenin özniteliklerini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="80ab6-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="80ab6-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ab6-140">Example</span></span>  
 <span data-ttu-id="80ab6-141">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi kullanarak oluşturur ve bağlamanın yeniden oynatma özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="80ab6-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="80ab6-142">Yeniden Oynatmanın Kapsamı: Yalnızca İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="80ab6-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="80ab6-143">Aşağıdaki yordamların yalnızca İleti güvenlik moduna uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="80ab6-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="80ab6-144">İleti Kimlik Bilgisi modları ile Aktarım ve Aktarım için, aktarım mekanizmaları tekrarları algılar.</span><span class="sxs-lookup"><span data-stu-id="80ab6-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="80ab6-145">Güvenli Konuşma Notları</span><span class="sxs-lookup"><span data-stu-id="80ab6-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="80ab6-146">Güvenli konuşmaları etkinleştiren bağlamalar için, bu ayarları hem uygulama kanalı hem de güvenli konuşma bootstrap bağlama için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80ab6-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="80ab6-147">Örneğin, uygulama kanalının tekrarlarını kapatabilir, ancak güvenli konuşmayı oluşturan bootstrap kanalı için bunları etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80ab6-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="80ab6-148">Güvenli konuşma oturumları kullanmıyorsanız, yeniden oynatma algılama, sunucu eksede senaryolarında ve işlem geri dönüştürüldüğünde yeniden oynatmaalgılanmasını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="80ab6-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="80ab6-149">Bu, sistem tarafından sağlanan aşağıdaki bağlamalar için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="80ab6-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="80ab6-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="80ab6-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="80ab6-151"><xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> olarak ayarlanmış olan `false`özellik ile.</span><span class="sxs-lookup"><span data-stu-id="80ab6-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80ab6-152">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="80ab6-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="80ab6-153">Kodu derlemek için aşağıdaki ad alanları gereklidir:</span><span class="sxs-lookup"><span data-stu-id="80ab6-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="80ab6-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80ab6-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="80ab6-155">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="80ab6-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="80ab6-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="80ab6-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="80ab6-157">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="80ab6-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
