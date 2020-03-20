---
title: Bağlam Değişimi Protokolü
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 00adb68d96f77ce0953811d13b5377ec4ed1e0ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185260"
---
# <a name="context-exchange-protocol"></a>Bağlam Değişimi Protokolü
Bu bölümde, Windows Communication Foundation (WCF) sürümü .NET Framework sürüm 3.5'te tanıtılan bağlam değişimi protokolü açıklanmaktadır. Bu iletişim kuralı, istemci kanalının bir hizmet tarafından sağlanan bir bağlamı kabul etmesine ve aynı istemci kanalı örneği üzerinden gönderilen bu hizmete sonraki tüm isteklere uygulamasına olanak tanır. Bağlam değişimi protokolünün uygulanması, sunucu ve istemci arasındaki bağlamı yaymak için aşağıdaki iki mekanizmadan birini kullanabilir: HTTP çerezleri veya soap üstbilgisi.  
  
 Bağlam değiştirme protokolü özel bir kanal katmanında uygulanır. Kanal, bir <xref:System.ServiceModel.Channels.ContextMessageProperty> özelliği kullanarak bağlamı uygulama katmanına ve uygulama katmanından ileter. Uç noktalar arasındaki iletim için bağlamın değeri kanal katmanında SOAP üstbilgisi olarak serihale edilir veya http isteği ve yanıtını temsil eden ileti özelliklerine dönüştürülür. İkinci durumda, temel kanal katmanlarından birinin, http isteği ve yanıt iletisi özelliklerini sırasıyla HTTP tanımlama bilgilerine ve bu tanımlama bilgilerine dönüştürmesi beklenmektedir. Bağlam değişimi için kullanılan mekanizmanın seçimi üzerinde <xref:System.ServiceModel.Channels.ContextExchangeMechanism> özellik <xref:System.ServiceModel.Channels.ContextBindingElement>kullanılarak yapılır. Geçerli değerler `HttpCookie` `SoapHeader`veya .  
  
 İstemcide, bir kanal örneği, kanal özelliğindeki ayarlara göre iki <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>modda çalışabilir.  
  
## <a name="mode-1-channel-context-management"></a>Mod 1: Kanal Bağlam Yönetimi  
 Bu varsayılan mod <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> olarak `true`ayarlanır. Bu modda bağlam kanalı bağlamı yönetir ve kullanım ömrü boyunca bağlamı önbelleğe getirir. `GetContext` Bağlam, yöntem `IContextManager` çağırılarak kanal özelliği üzerinden kanaldan alınabilir. Kanal özelliği üzerinde `SetContext` yöntem çağırarak açılmadan önce belirli bir bağlam ile ön önolarak önolarak açılabilir. Kanal bağlamla başharfe basıldıktan sonra sıfırlanamaz.  
  
 Bu modda değişmezlerin listesi aşağıda veda edinilir:  
  
- Kanal açıldıktan sonra bağlamı sıfırlamaya `SetContext` yönelik herhangi <xref:System.InvalidOperationException>bir girişim bir .  
  
- Giden bir <xref:System.ServiceModel.Channels.ContextMessageProperty> iletide kullanarak bağlam gönderme girişimi bir <xref:System.InvalidOperationException>.  
  
- Bir ileti sunucudan belirli bir bağlamla alınırsa, kanal zaten belirli bir bağlamla baş <xref:System.ServiceModel.ProtocolException>harfe batmışsa, bu bir .  
  
    > [!NOTE]
    > Yalnızca kanal açık olarak ayarlanan herhangi bir bağlam olmadan açıldığında sunucudan bir başlangıç bağlamı almak uygundur.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty> Gelen ileti her zaman geçersizdir.  
  
## <a name="mode-2-application-context-management"></a>Mod 2: Uygulama Bağlam Yönetimi  
 Bu mod da <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> `false`ayarlanır. Bu modda bağlam kanalı bağlamı yönetmez. Bağlamı kullanarak bağlamı almak, yönetmek ve uygulamak <xref:System.ServiceModel.Channels.ContextMessageProperty>uygulamanın sorumluluğudur. Herhangi `GetContext` bir arama `SetContext` girişimi <xref:System.InvalidOperationException>veya sonuç bir .  
  
 Hangi mod seçilirse seçilsin, istemci kanal fabrikası destekler <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ileti alışverişi desenleri.  
  
 Hizmette, kanalın bir örneği, istemci tarafından gelen iletilerde sağlanan bağlamı <xref:System.ServiceModel.Channels.ContextMessageProperty>. İleti özelliğine daha sonra uygulama katmanı veya arama yığınının diğer kanalları tarafından erişilebilir. Hizmet kanalları ayrıca, yanıt iletisine bir ileti <xref:System.ServiceModel.Channels.ContextMessageProperty> ekleyerek istemciye yeniden yayılacak yeni bir bağlam değeri belirtmek için uygulama katmanına da izin verir. Bu özellik, bağlama yapılandırmasına bağlı bağlamı içeren SOAP üstbilgisine veya HTTP çerezine dönüştürülür. Servis kanalı dinleyicisi, <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel> ve ileti alışverişi desenlerini destekler.  
  
 Bağlam değiştirme protokolü, http `wsc:Context` tanımlama bilgileri bağlamı yaymak için kullanılmadığında bağlam bilgilerini temsil edecek yeni bir SOAP üstbilgisi sunar. Bağlam üstbilgi şeması, her biri dize tuşu ve dize içeriğine sahip her biri olan herhangi bir sayıda alt öğeye izin verir. Aşağıda bir bağlam üstbilgi örneği verilmiştir.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Moddayken, `HttpCookie` çerezler `SetCookie` üstbilgi kullanılarak ayarlanır. Çerez `WscContext`adı. Çerezin değeri üstbilginin Base64 kodlamasidır. `wsc:Context` Bu değer tırnak içinde eklenir.  
  
 Bağlamın değeri, WS Adresleme üstbilgileriyle aynı nedenle geçiş sırasında değişiklikten korunmalıdır – üstbilgi, isteğin hizmete nereye gönderilen yeri belirlemek için kullanılır. Bu `wsc:Context` nedenle üstbilginin, bağlama ileti koruma özelliği sunduğunda, sabun veya aktarım düzeyinde dijital olarak imzalanması veya imzalanması ve şifrelemesi gerekir. BAĞLAMi yaymak için HTTP tanımlama bilgileri kullanıldığında, aktarım güvenliği kullanılarak korunmalıdır.  
  
 Bağlam değişimi protokolü için destek gerektiren hizmet uç noktaları, yayımlanmış ilkede bunu açıkça belirtebilir. İstemcinin bağlam değişim protokolünü SOAP düzeyinde desteklemesi veya HTTP çerez desteğini etkinleştirme gereksinimini temsil etmek için iki yeni ilke iddiası sunulmuştur. Hizmet ilkesine bu iddiaların nesil aşağıdaki gibi <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> özelliğin değeri tarafından denetlenir:  
  
- Bunun <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>için, aşağıdaki iddia oluşturulur:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Bunun <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>için, aşağıdaki iddia oluşturulur:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
