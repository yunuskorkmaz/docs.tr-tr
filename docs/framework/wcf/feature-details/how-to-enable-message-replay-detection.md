---
title: "Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12b0317503a907700099b1594b8b33799938f752
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-message-replay-detection"></a>Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme
Yeniden yürütme saldırı bir saldırganın iki taraflar arasında iletileri akışı kopyalar ve bir veya daha fazla tarafların akışa başlayarak yeniden oynatılır oluşur. Azaltıldığından sürece, bilgisayarlar saldırı tabi akış yasal iletileri, bir öğenin yedekli siparişleri gibi hatalı sonuçları aralığında kaynaklanan olarak işler.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ileti yeniden yürütme algılaması için bkz: [ileti yeniden yürütme algılaması](http://go.microsoft.com/fwlink/?LinkId=88536).  
  
 Aşağıdaki yordamda denetlemek için kullanabileceğiniz çeşitli özellikler yeniden yürütme algılaması kullanarak gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Kod kullanılarak istemcide yeniden yürütme algılaması denetlemek için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> kullanmak için bir <xref:System.ServiceModel.Channels.CustomBinding>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Aşağıdaki örnek kullanan bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ile oluşturulan <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> , <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.  
  
2.  Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> bir başvuru döndürmek için özellik <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> sınıfı ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlayın:  
  
    1.  `DetectReplay`. Bir Boole değeri. Bu istemci sunucudan yürütmelerini algılamak gerekmediğini belirler. Varsayılan, `true` değeridir.  
  
    2.  `MaxClockSkew`. A <xref:System.TimeSpan> değeri. Yeniden yürütme mekanizması istemci ve sunucu arasında dayanabileceği ne kadar süre eğme yönetir. Güvenlik mekanizması zaman damgası gönderilen ve bu geri çok kadar geçmişte gönderilip gönderilmediğini belirler inceler. Varsayılan değer 5 dakikadır.  
  
    3.  `ReplayWindow`. A `TimeSpan` değeri. Bu ne kadar ileti yöneten sunucu (üzerinden aracılar) istemci ulaşmadan önce gönderdikten sonra ağda dinamik. İstemci en son içinde gönderilen iletileri imzalarını izler `ReplayWindow` yeniden yürütme algılaması amacı.  
  
    4.  `ReplayCacheSize`. Bir tamsayı değeri. İstemci ileti imzalarını bir önbellekte depolar. Bu ayar, önbellekte saklayabilirsiniz kaç imzaları belirtir. Son yeniden yürütme pencereye gönderilen ileti sayısını önbellek sınırı ulaşırsa, en eski önbelleğe alınmış imzaları süre gelene kadar yeni iletiler reddedilir. 500000 varsayılandır.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Kod kullanarak hizmet yeniden yürütme algılamayı denetlemek için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> kullanmak için bir <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> bir başvuru döndürmek için özellik <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı ve daha önce açıklandığı gibi özellikleri ayarlayın.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Yeniden yürütme algılaması istemci veya hizmet yapılandırmasında denetlemek için  
  
1.  Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Oluşturma bir `<security>` öğesi.  
  
3.  Oluşturma bir [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) veya [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4.  Aşağıdaki öznitelik değerlerini uygun şekilde ayarlayın: `detectReplays`, `maxClockSkew`, `replayWindow`, ve `replayCacheSize`. Aşağıdaki örnek, her ikisi de özniteliklerini ayarlar bir `<localServiceSettings>` ve `<localClientSettings>` öğe:  
  
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
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> kullanarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi ve bağlama yeniden yürütme özelliklerini ayarlar.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Yeniden yürütme kapsamını: yalnızca ileti güvenliği  
 Aşağıdaki yordamlar yalnızca ileti güvenlik modu için geçerli olduğunu unutmayın. Taşıma ve ileti kimlik bilgileri modlarıyla aktarımı için aktarım düzeneklerini yürütmelerini algılamak.  
  
## <a name="secure-conversation-notes"></a>Konuşma Notları güvenli  
 Güvenli konuşmaları etkinleştirmek için bağlamaları, hem uygulama kanalı yanı sıra güvenli konuşma başlatma bağlaması için bu ayarları ayarlayabilirsiniz. Örneğin, uygulama kanalı yürütmelerini kapatmak ancak güvenli Konuşmayla kuran önyükleme kanalı etkinleştirin.  
  
 Güvenli Konuşmayla oturumları kullanıyorsanız değil, yeniden yürütme algılaması sunucu grubu senaryolarını ve ne zaman işlem geri dönüştürülmeden yürütmelerini algılamak garanti etmez. Bu, aşağıdaki sistem tarafından sağlanan bağlamaları için geçerlidir:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding>ile <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini `false`.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Şu ad alanlarından Kodu derlemek için gereklidir:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Güvenli iletişimler ve güvenli oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
