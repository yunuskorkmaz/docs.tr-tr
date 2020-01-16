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
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964655"
---
# <a name="how-to-enable-message-replay-detection"></a>Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme
Bir saldırgan iki taraf arasında bir ileti akışını kopyaladığında veya bir veya daha fazla tarafın akışını yeniden oynadığında bir yeniden yürütme saldırısı meydana gelir. Hafiflemediği sürece, saldırıya tabi olan bilgisayarlar akışı meşru iletiler olarak işleyecek ve bu da bir öğenin gereksiz sıraları gibi hatalı sonuçlar oluşmasına neden olur.  
  
 İleti yeniden yürütme algılaması hakkında daha fazla bilgi için bkz. [ileti yeniden yürütme algılaması](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 Aşağıdaki yordamda Windows Communication Foundation (WCF) kullanarak yeniden yürütme algılamasını denetlemek için kullanabileceğiniz çeşitli özellikler gösterilmektedir.  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Kodu kullanarak istemcide yeniden yürütme algılamasını denetlemek için  
  
1. <xref:System.ServiceModel.Channels.CustomBinding>kullanmak için bir <xref:System.ServiceModel.Channels.SecurityBindingElement> oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Aşağıdaki örnek <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfının <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> oluşturulmuş bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> kullanır.  
  
2. <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> özelliğini kullanarak <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> sınıfına bir başvuru döndürün ve aşağıdaki özelliklerden herhangi birini uygun şekilde ayarlayın:  
  
    1. `DetectReplay`. Boole değeri. Bu, istemcinin sunucudan yeniden yürütme algılaması gerekip gerekmediğini yönetir. Varsayılan, `true` değeridir.  
  
    2. `MaxClockSkew`. Bir <xref:System.TimeSpan> değeri. Yeniden yürütme mekanizmasına ne kadar eğinin istemci ile sunucu arasında ne kadar zaman harcamaya harcanabileceği yönetir. Güvenlik mekanizması gönderilen zaman damgasını inceler ve geçmişte daha fazla geri gönderilip gönderilmediğini belirler. Varsayılan değer 5 dakikadır.  
  
    3. `ReplayWindow`. Bir `TimeSpan` değeri. Bu, istemciye ulaşmadan önce bir iletinin ağ üzerinde ne kadar süreyle (aracılar aracılığıyla) ne kadar sürdüğünü yönetir. İstemci, yeniden yürütme algılaması amacıyla en son `ReplayWindow` gönderilen iletilerin imzalarını izler.  
  
    4. `ReplayCacheSize`. Bir tamsayı değeri. İstemci, iletinin imzalarını bir önbellekte depolar. Bu ayar önbelleğin kaç tane imza depolayabileceği belirtir. Son yeniden yürütme penceresi içinde gönderilen ileti sayısı önbellek sınırına ulaşırsa, en eski önbelleğe alınan imzaların zaman sınırına ulaşması için yeni iletiler reddedilir. Varsayılan değer 500000 ' dir.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Kodu kullanarak hizmette yeniden yürütme algılamasını denetlemek için  
  
1. <xref:System.ServiceModel.Channels.CustomBinding>kullanmak için bir <xref:System.ServiceModel.Channels.SecurityBindingElement> oluşturun.  
  
2. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfına bir başvuru döndürmek ve daha önce açıklandığı gibi özellikleri ayarlamak için <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> özelliğini kullanın.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>İstemci veya hizmet yapılandırmasında yeniden yürütme algılamayı denetlemek için  
  
1. [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)oluşturun.  
  
2. `<security>` öğesi oluşturun.  
  
3. [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) veya [\<localservicesettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)oluşturun.  
  
4. Aşağıdaki öznitelik değerlerini uygun şekilde ayarlayın: `detectReplays`, `maxClockSkew`, `replayWindow`ve `replayCacheSize`. Aşağıdaki örnek, hem `<localServiceSettings>` hem de bir `<localClientSettings>` öğesinin özniteliklerini ayarlar:  
  
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
 Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemini kullanarak bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> oluşturur ve bağlamanın yeniden yürütme özelliklerini ayarlar.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Yeniden yürütme kapsamı: yalnızca Ileti güvenliği  
 Aşağıdaki yordamların yalnızca Ileti güvenliği modu için uygulanacağını unutmayın. Ileti kimlik bilgileri modlarıyla taşıma ve taşıma için, aktarım mekanizmaları yeniden oynatılır.  
  
## <a name="secure-conversation-notes"></a>Güvenli konuşma notları  
 Güvenli konuşmaları etkinleştiren bağlamalar için, bu ayarları hem uygulama kanalında hem de güvenli konuşma önyükleme bağlaması için ayarlayabilirsiniz. Örneğin, uygulama kanalı için yeniden oynatılamayı kapatabilir, ancak bunları güvenli konuşmayı kuran önyükleme kanalı için etkinleştirebilirsiniz.  
  
 Güvenli konuşma oturumlarını kullanmıyorsanız, yeniden yürütme algılaması, sunucu grubu senaryolarında ve işlem geri dönüştürüldüğünde yeniden yürütmenin saptanmasını garantilemez. Bu, sistem tarafından belirtilen aşağıdaki bağlamalar için geçerlidir:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği `false`olarak ayarlanmış <xref:System.ServiceModel.WSHttpBinding>.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Kodu derlemek için aşağıdaki ad alanları gereklidir:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Güvenli İletişimler ve Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
