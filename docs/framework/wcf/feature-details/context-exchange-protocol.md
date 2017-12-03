---
title: "Bağlam Değişimi Protokolü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ef5406831e1bfaa9c1c4f959363bc8b26cd3820
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="context-exchange-protocol"></a>Bağlam Değişimi Protokolü
Bu bölümde sunulan bağlam değişimi protokolü açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] serbest bırakın. Bu protokol hizmeti tarafından sağlanan bir bağlam kabul etmek ve tüm istekler aynı istemci kanal örneği gönderilen bu hizmete uygulamak istemci kanal sağlar. Bağlam değişimi Protokolü aşağıdaki iki mekanizmalardan biri sunucu ve istemci arasındaki bağlam yaymak için kullanabilirsiniz: HTTP tanımlama bilgilerini veya SOAP üstbilgisi.  
  
 Bağlam değişimi protokolü özel kanal katmanında uygulanır. Kanal bağlamı uygulama katmanı kullanarak gelen ve giden iletişim kuran bir <xref:System.ServiceModel.Channels.ContextMessageProperty> özelliği. Uç noktalar arasında aktarım için context değeri SOAP üstbilgi kanal katmanında olarak serileştirilmiş, veya için veya bir HTTP istek ve yanıt temsil eden ileti özelliklerinin dönüştürülür. İkinci durumda, kanal katmanlarda birini HTTP istek ve yanıt ileti özelliklerini HTTP tanımlama bilgileri, gelen ve giden sırasıyla dönüştürdüğü beklenir. Bağlam değişimi için kullanılan mekanizma seçimi yapılır kullanarak <xref:System.ServiceModel.Channels.ContextExchangeMechanism> özelliği <xref:System.ServiceModel.Channels.ContextBindingElement>. Geçerli değerler `HttpCookie` veya `SoapHeader`.  
  
 İstemci üzerinde bir kanal örneği kanal özellikte ayarlara göre iki modda çalışabilir <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Mod 1: Kanal içerik yönetimi  
 Bu varsayılan moddur nerede <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ayarlanır `true`. Bu modda içerik kanalı bağlam yönetir ve bağlam yaşam süresi boyunca önbelleğe alır. İçerik kanalı özelliği aracılığıyla kanaldan alınabilir `IContextManager` çağırarak `GetContext` yöntemi. Kanal ayrıca çağırarak açılmasını önce belirli bağlamla önceden başlatılmış olabilir `SetContext` kanal özellikte yöntemi. Kanal bağlamla başlatıldıktan sonra sıfırlanamaz.  
  
 Bu modda invariants listesi aşağıdadır:  
  
-   Yapmaya bağlamını kullanarak sıfırlamak `SetContext` kanal açılan atar sağlandıktan sonra bir <xref:System.InvalidOperationException>.  
  
-   Yapmaya bağlamı kullanarak göndermek <xref:System.ServiceModel.Channels.ContextMessageProperty> giden iletisinde oluşturur bir <xref:System.InvalidOperationException>.  
  
-   Kanalı ile belirli bir bağlam zaten başlatılmış olan bir ileti ile belirli bir bağlam sunucusundan alınırsa, bu sonuçlanan bir <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  Yalnızca açık olarak ayarlanıp herhangi bir bağlam olmadan kanal açtıysanız ilk içerik sunucusundan almak uygundur.  
  
-   <xref:System.ServiceModel.Channels.ContextMessageProperty> Gelen ileti üzerinde her zaman boştur.  
  
## <a name="mode-2-application-context-management"></a>Mod 2: Uygulama içerik yönetimi  
 Bu mod olduğu zaman <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ayarlanır `false`. Bu modda, bağlam içerik kanalı yönetmez. Bu almak, yönetmek ve bağlamı kullanarak uygulamak için uygulamanın sorumluluğundadır <xref:System.ServiceModel.Channels.ContextMessageProperty>. Herhangi bir çağrı dener `GetContext` veya `SetContext` sonuçlanan bir <xref:System.InvalidOperationException>.  
  
 Hangi modun olsun istemci kanal fabrikası destekleyen seçilir <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel> exchange desenleri iletisi.  
  
 Hizmette kanal örneği gelen iletiler için istemci tarafından sağlanan içerik dönüştürme için sorumlu olan <xref:System.ServiceModel.Channels.ContextMessageProperty>. İleti özelliği sonra uygulama katmanı tarafından erişilebilir veya diğer kanallar çağrı yığınında daha. Hizmet kanal ekleyerek istemciye yayılması için yeni bir bağlam değeri belirtmek uygulama katmanı da izin bir <xref:System.ServiceModel.Channels.ContextMessageProperty> yanıt iletisi. Bu özellik, SOAP üstbilgi veya bağlama yapılandırmasına bağlıdır bağlamını içeren HTTP tanımlama bilgisi dönüştürülür. Hizmet kanal dinleyicisi destekler <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, ve <xref:System.ServiceModel.Channels.IReplySessionChannel> exchange desenleri iletisi.  
  
 Bağlam değişimi Protokolü yeni tanıtır `wsc:Context` SOAP üstbilgi HTTP bağlamı yaymak için kullanılmaz, bağlam bilgilerini temsil eder. İçerik Üstbilgisi şemasının herhangi bir sayıda alt öğeleri, her bir dize anahtar ve dize içeriği sağlar. İçerik üstbilgisinin bir örnek verilmiştir.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Zaman içinde `HttpCookie` modu, tanımlama bilgileri kullanılarak ayarlanır `SetCookie` üstbilgi. Tanımlama bilgisi adıdır `WscContext`. Base64 tanımlama bilgisinin değeri kodlamasını `wsc:Context` üstbilgi. Bu değer tırnak işaretleri içine alınır.  
  
 Aynı nedenden dolayı aktarımda WS adresleme üstbilgileri korunan sırada context değeri değiştirilmeye karşı korumalı olması gereken – üstbilgi hizmette isteğin gönderileceği yeri belirlemek için kullanılır. `wsc:Context` Üstbilgisi bu nedenle dijital olarak imzalanmış veya imzalanmasını ve bağlama ileti koruma özelliği önerdiğinde SOAP veya aktarım düzeyinde şifrelenmiş için gereklidir. HTTP tanımlama bilgilerini bağlam yaymak için kullanıldığında, taşıma güveliği kullanarak korunmalıdır.  
  
 Bağlam değişimi protokolü için desteği gerektiren hizmet uç noktaları yayımlanan ilkesinde açık yapabilirsiniz. Bağlam değişimi Protokolü SOAP düzeyinde desteklemek veya HTTP tanımlama bilgisi desteğini etkinleştirmek için istemci gereksinimini göstermek için iki yeni ilke onaylamalarını tanıtılmıştır. Bu onaylar hizmet ilkesindeki içine nesil değeri tarafından denetlenen <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> özelliğini aşağıdaki gibi:  
  
-   İçin <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, aşağıdaki onay oluşturulur:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
-   İçin <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, aşağıdaki onay oluşturulur:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Hizmetleri protokolleri birlikte çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
