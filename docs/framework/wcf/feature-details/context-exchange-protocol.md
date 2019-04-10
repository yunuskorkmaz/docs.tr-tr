---
title: Bağlam Değişimi Protokolü
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: a6bc0ac45282d94a6aea8dbbdb5a7d34163c692e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217009"
---
# <a name="context-exchange-protocol"></a>Bağlam Değişimi Protokolü
Bu bölümde, Windows Communication Foundation (WCF) .NET Framework sürüm 3.5 sürümünde tanıtılan bağlam değişimi Protokolü açıklanmaktadır. Bu protokol, istemci bir hizmeti tarafından sağlanan bir bağlam kabul edin ve bu hizmet aynı istemci kanal örneği gönderilen tüm istekler geçerli kanala sağlar. Bağlam değişimi Protokolü uygulanmasının sunucu ve istemci arasında bağlamı yaymak için aşağıdaki iki mekanizma birini kullanabilirsiniz: HTTP tanımlama bilgileri veya bir SOAP üst bilgisi.  
  
 Bağlam değişimi protokolü, bir özel kanal katmana uygulanır. Kanal bağlamı uygulama katmanını kullanarak gelen ve giden iletişim kuran bir <xref:System.ServiceModel.Channels.ContextMessageProperty> özelliği. Uç noktalar arasında iletim için bağlam değerini kanal katmanında SOAP üst bilgi olarak seri hale getirilmiş, veya ya da bir HTTP isteği ve yanıtı temsil eden ileti özelliklerinden dönüştürülür. İkinci durumda, kanal katmanlarda birini HTTP istek ve yanıt iletisi özellikleri HTTP tanımlama bilgileri, gelen ve giden sırasıyla dönüştürdüğü beklenmektedir. Bağlam değişimi için kullanılan mekanizma seçimi yapılır kullanarak <xref:System.ServiceModel.Channels.ContextExchangeMechanism> özellikte <xref:System.ServiceModel.Channels.ContextBindingElement>. Geçerli değerler `HttpCookie` veya `SoapHeader`.  
  
 İstemcide, bir kanal örneği ayarlara göre kanal özelliği iki modda çalışabilir <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Modu 1'de: Kanal içerik yönetimi  
 Bu varsayılan moddur burada <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ayarlanır `true`. Bu modda içerik kanalı bağlamı yönetir ve yaşam süresi boyunca içeriği önbelleğe alır. Bağlam, kanal özelliği aracılığıyla bir kanaldan alınabilir `IContextManager` çağırarak `GetContext` yöntemi. Kanal ayrıca çağırarak açılmasını önce belirli bağlamı ile önceden başlatılmış olabilir `SetContext` kanal özellik yöntemi. Kanal bağlamıyla başlatıldıktan sonra sıfırlanamaz.  
  
 Bu modda okuduğunuzda listesi verilmiştir:  
  
-   Yapmaya bağlamını kullanarak sıfırlamak `SetContext` kanal açılan oluşturur sonra bir <xref:System.InvalidOperationException>.  
  
-   Yapmaya kullanarak içerik göndermeye <xref:System.ServiceModel.Channels.ContextMessageProperty> giden iletisinde oluşturur bir <xref:System.InvalidOperationException>.  
  
-   Kanalı ile belirli bir bağlam zaten başlatılmış, belirli bir içerik sunucusundan bir ileti alındığında, sonuçlanır bir <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  Yalnızca açık olarak herhangi bir bağlam olmadan kanal açıldığında bir başlangıç bağlamı sunucudan almak uygundur.  
  
-   <xref:System.ServiceModel.Channels.ContextMessageProperty> Üzerinde gelen iletilerin her zaman null şeklindedir.  
  
## <a name="mode-2-application-context-management"></a>2. modu: Uygulama içerik yönetimi  
 Bu modu etkin olduğunda <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ayarlanır `false`. Bu modda, bağlam içerik kanalı yönetmez. Bunu almak, yönetmek ve bağlamı kullanarak uygulamak için uygulamanın sorumluluğundadır <xref:System.ServiceModel.Channels.ContextMessageProperty>. Çağrılacak yapmaya `GetContext` veya `SetContext` sonuçlanır bir <xref:System.InvalidOperationException>.  
  
 İstemci kanal fabrikası destekler ne olursa olsun, hangi modu seçilen <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel> exchange desenleri iletisi.  
  
 Hizmette örneğini kanal, gelen iletiler için istemci tarafından sağlanan bağlam oluşturmaktan sorumludur <xref:System.ServiceModel.Channels.ContextMessageProperty>. İleti özelliği daha sonra uygulama katmanı tarafından erişilebilir veya diğer kanallar daha fazla çağrı yığınında yukarı. Hizmet kanalları da ekleyerek istemciye dağıtılmasını yeni bir bağlam değeri belirtmek uygulama katmanı izin bir <xref:System.ServiceModel.Channels.ContextMessageProperty> yanıt iletisi. Bu özellik SOAP üst bilgi veya bağlamı, bağlama yapılandırmasına bağlıdır içeren HTTP tanımlama bilgisi dönüştürülür. Hizmet kanal dinleyicisi destekler <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, ve <xref:System.ServiceModel.Channels.IReplySessionChannel> exchange desenleri iletisi.  
  
 Bağlam değişimi Protokolü yeni kullanıma sunuyor `wsc:Context` bağlam yaymak için HTTP tanımlama bilgileri kullanılmaz, bağlam bilgilerini temsil etmek için SOAP üstbilgisi. Herhangi bir sayıda alt öğeleri, her bir dize anahtarı ve dize içerik için içerik üstbilgisi şemasının sağlar. Bağlam üst bilgisi bir örnek verilmiştir.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Zaman içinde `HttpCookie` modu, tanımlama bilgisi kullanılarak ayarlanır `SetCookie` başlığı. Tanımlama bilgisi adı `WscContext`. Tanımlama bilgisinin değeri bir Base64 değeri kodlamasını `wsc:Context` başlığı. Bu değer tırnak işaretleri içine alınır.  
  
 WS-Addressing üst bilgileri aynı nedenle aktarım sırasında korunur context değeri değişikliklere karşı korunması gerekir: Başlık hizmetine isteğin gönderileceği yerini belirlemek için kullanılır. `wsc:Context` Üst bilgisi, bu nedenle dijital olarak imzalı veya imzalı ve bağlama iletisi koruma özelliği sunar SOAP veya aktarım düzeyinde şifreli gereklidir. HTTP tanımlama bilgileri, bağlam yaymak için kullanıldığında, aktarım güvenliği kullanarak korunmalıdır.  
  
 Bağlam değişimi protokolü için destek gerektiren bir hizmet uç noktaları, yayımlanmış bir ilke içinde açık zorlaştırabilir. Bağlam değişimi Protokolü SOAP düzeyinde desteklemek veya HTTP tanımlama bilgisi desteğini etkinleştirmek için istemci gereksinimi temsil etmek için iki yeni ilke onaylamalarını tanıtılmıştır. Deyimlerinize hizmetine ilke oluşturulmasını değeri tarafından denetlenen <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> özelliğini aşağıdaki gibi:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
