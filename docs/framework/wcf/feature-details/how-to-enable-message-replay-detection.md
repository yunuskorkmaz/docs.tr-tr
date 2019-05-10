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
ms.openlocfilehash: a41c53e87d82452eac8d7535a422b7aa4bd4e270
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626885"
---
# <a name="how-to-enable-message-replay-detection"></a>Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme
Yeniden yürütme saldırı bir saldırganın iki taraflar arasında iletileri akışını kopyalar ve bir veya daha fazla taraflar akışa başlayarak yeniden oynatılır oluşur. Azaltılabilir sürece, saldırı bilgisayarların stream yasal iletileri, sonuçta hatalı sonuçları, bir öğenin yedekli siparişler gibi bir dizi olarak işler.  
  
 İleti yeniden yürütme algılamayı hakkında daha fazla bilgi için bkz: [ileti yeniden yürütme algılamayı](https://go.microsoft.com/fwlink/?LinkId=88536).  
  
 Aşağıdaki yordam Windows Communication Foundation (WCF) kullanarak yeniden yürütme algılaması denetlemek için kullanabileceğiniz çeşitli özelliklerini gösterir.  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Kod kullanılarak istemcide yeniden yürütme algılaması denetlemek için  
  
1. Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> kullanmak için bir <xref:System.ServiceModel.Channels.CustomBinding>. Daha fazla bilgi için [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Aşağıdaki örnekte bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ile oluşturulan <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> , <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.  
  
2. Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> bir başvuru döndürmek için özellik <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> sınıfı ve aşağıdaki özellikleri uygun şekilde ayarlayın:  
  
    1. `DetectReplay`. Bir Boole değeri. Bu, istemcinin sunucudan olumsuzlukları algılanmalıdır olmadığını yönetir. Varsayılan, `true` değeridir.  
  
    2. `MaxClockSkew`. A <xref:System.TimeSpan> değeri. Yeniden yürütme mekanizması istemci ve sunucu arasında tolere edebilen ne kadar zaman eğimi yönetir. Güvenlik mekanizması, zaman damgası gönderilen ve bu çok kadar geri geçmişte gönderilip gönderilmediğini belirler inceler. Varsayılan değer 5 dakikadır.  
  
    3. `ReplayWindow`. A `TimeSpan` değeri. Bu ne kadar iletiye yöneten sunucu (aracılar) üzerinden istemci ulaşmadan önce gönderdikten sonra ağdaki Canlı çalıştırabilirsiniz. En son gönderilen iletilerin imzalarını istemci izler `ReplayWindow` yeniden yürütme algılaması amaçları için.  
  
    4. `ReplayCacheSize`. Bir tamsayı değeri. İstemci, iletinin imzalarını bir önbellekte depolar. Bu ayar önbellekte saklayabilirsiniz kaç imzaları belirtir. Son yeniden yürütme penceresine gönderilen ileti sayısını önbellek sınırı ulaşırsa, en eski önbelleğe alınmış imzaları süre ulaşana kadar yeni iletileri reddedilir. 500000 varsayılandır.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Kod kullanarak hizmet yeniden yürütme algılamayı denetlemek için  
  
1. Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> kullanmak için bir <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2. Kullanım <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> bir başvuru döndürmek için özellik <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı ve daha önce açıklandığı gibi özellikleri ayarlayın.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Yeniden yürütme algılaması istemci veya hizmet yapılandırmasında denetlemek için  
  
1. Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Oluşturma bir `<security>` öğesi.  
  
3. Oluşturma bir [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) veya [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Aşağıdaki öznitelik değerlerini uygun şekilde ayarlayın: `detectReplays`, `maxClockSkew`, `replayWindow`, ve `replayCacheSize`. Aşağıdaki örnek, her iki öznitelikleri ayarlar bir `<localServiceSettings>` ve `<localClientSettings>` öğesi:  
  
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
 Aşağıdaki örnek, oluşturur bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> kullanarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi ve bağlama yeniden yürütme özelliklerini ayarlar.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Yeniden yürütme kapsamı: İleti güvenliği  
 Aşağıdaki yordamlar, yalnızca ileti güvenlik modu için geçerli olduğunu unutmayın. Taşıma ve ileti kimlik bilgileri modları ile aktarma için taşıma mekanizmaları olumsuzlukları algılayın.  
  
## <a name="secure-conversation-notes"></a>Güvenli konuşma notları  
 Güvenli konuşma etkinleştirmek için bağlamaları, hem uygulama kanalı yanı sıra güvenli konuşma başlatma bağlaması için bu ayarları ayarlayabilirsiniz. Örneğin, uygulama kanalı olumsuzlukları kapatma ancak kuran güvenli konuşma önyükleme kanalı odaklanmalarını.  
  
 Güvenli konuşma oturumları kullanıyorsanız değil, yeniden yürütme algılaması olumsuzlukları sunucu grubu senaryolarını ve ne zaman işlem geri dönüştürülmeden algılama garanti etmez. Bu, aşağıdaki sistem tarafından sağlanan bağlamalar için geçerlidir:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding> ile <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini `false`.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Aşağıdaki ad alanlarını, kodu derlemek için gereklidir:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Güvenli İletişimler ve Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
