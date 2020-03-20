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
# <a name="how-to-enable-message-replay-detection"></a>Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme
Bir yeniden oynatma saldırısı, bir saldırgan iki taraf arasındaki ileti akışını kopyaladığında ve akışı taraflardan birine veya daha fazlasına yeniden oynattığında oluşur. Azaltılmadığı sürece, saldırıya maruz kalan bilgisayarlar akışı meşru iletiler olarak işleyerek bir öğenin gereksiz siparişleri gibi bir dizi kötü sonuca yol açacaktır.  
  
 İleti yeniden oynatma algılama hakkında daha fazla bilgi için ileti [yeniden oynatma algılama](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10))konusuna bakın.  
  
 Aşağıdaki yordam, Windows Communication Foundation (WCF) kullanarak yeniden oynatma algılamasını denetlemek için kullanabileceğiniz çeşitli özellikleri gösterir.  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Kodu kullanarak istemcide yeniden oynatma algılamasını denetlemek için  
  
1. Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> 'de kullanılacak <xref:System.ServiceModel.Channels.CustomBinding>bir şey oluşturun Daha fazla bilgi için [bkz: SecurityBindingElement kullanarak Özel Bağlama oluşturun.](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfın bir ile oluşturulan kullanır.  
  
2. Sınıfa <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> bir başvuru döndürmek ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlamak için özelliği kullanın: <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
    1. `DetectReplay`. Boole değeri. Bu, istemcinin sunucudan yeniden oynatma algılayıp algılamaması gerektiğini yönetir. Varsayılan değer: `true`.  
  
    2. `MaxClockSkew`. Bir <xref:System.TimeSpan> değer. Yeniden oynatma mekanizmasının istemci ve sunucu arasında ne kadar zaman çarpıtabileceğini yönetir. Güvenlik mekanizması, gönderilen zaman damgasını inceler ve geçmişte çok uzağa gönderilip gönderilmediğini belirler. Varsayılan değer 5 dakikadır.  
  
    3. `ReplayWindow`. Bir `TimeSpan` değer. Bu, sunucu istemciye ulaşmadan önce iletinin (aracılar aracılığıyla) gönderdikten sonra ağda ne kadar süre yle yaşayabileceğini belirtir. İstemci, yeniden oynatma algılama amacıyla en `ReplayWindow` son gönderilen iletilerin imzalarını izler.  
  
    4. `ReplayCacheSize`. Bir sayı değeri. İstemci iletinin imzalarını bir önbellekte depolar. Bu ayar, önbelleğin depolayabileceği kaç imza olduğunu belirtir. Son yeniden oynatma penceresinde gönderilen ileti sayısı önbellek sınırına ulaşırsa, önbelleğe alınan en eski imzalar zaman sınırına ulaşana kadar yeni iletiler reddedilir. Varsayılan değer 500000'dir.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Kodu kullanarak hizmette yeniden oynatma algılamasını denetlemek için  
  
1. Bir <xref:System.ServiceModel.Channels.SecurityBindingElement> 'de kullanılacak <xref:System.ServiceModel.Channels.CustomBinding>bir şey oluşturun  
  
2. Sınıfa <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> bir başvuru döndürmek için özelliği kullanın ve özellikleri daha önce açıklandığı gibi ayarlayın. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>İstemci veya hizmet için yapılandırmada yeniden oynatma algılamasını denetlemek için  
  
1. [ \<Özelbağlayıcı>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)oluşturun.  
  
2. Bir `<security>` öğe oluşturun.  
  
3. [ \<Yerel](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) bir Müşteri Ayarları>veya [ \<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)oluşturun.  
  
4. Aşağıdaki öznitelik değerlerini uygun şekilde `detectReplays` `maxClockSkew`ayarlayın: , , `replayWindow`ve `replayCacheSize`. Aşağıdaki örnek, hem a `<localServiceSettings>` hem `<localClientSettings>` de bir öğenin özniteliklerini ayarlar:  
  
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
 Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi kullanarak oluşturur ve bağlamanın yeniden oynatma özelliklerini ayarlar.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Yeniden Oynatmanın Kapsamı: Yalnızca İleti Güvenliği  
 Aşağıdaki yordamların yalnızca İleti güvenlik moduna uygulandığını unutmayın. İleti Kimlik Bilgisi modları ile Aktarım ve Aktarım için, aktarım mekanizmaları tekrarları algılar.  
  
## <a name="secure-conversation-notes"></a>Güvenli Konuşma Notları  
 Güvenli konuşmaları etkinleştiren bağlamalar için, bu ayarları hem uygulama kanalı hem de güvenli konuşma bootstrap bağlama için ayarlayabilirsiniz. Örneğin, uygulama kanalının tekrarlarını kapatabilir, ancak güvenli konuşmayı oluşturan bootstrap kanalı için bunları etkinleştirebilirsiniz.  
  
 Güvenli konuşma oturumları kullanmıyorsanız, yeniden oynatma algılama, sunucu eksede senaryolarında ve işlem geri dönüştürüldüğünde yeniden oynatmaalgılanmasını garanti etmez. Bu, sistem tarafından sağlanan aşağıdaki bağlamalar için geçerlidir:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> olarak ayarlanmış olan `false`özellik ile.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Kodu derlemek için aşağıdaki ad alanları gereklidir:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Güvenli İletişimler ve Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
