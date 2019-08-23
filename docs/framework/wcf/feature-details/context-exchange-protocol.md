---
title: Bağlam Değişimi Protokolü
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 19780cccc74f8c3615dc844e47be7613ca5f8bc1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911201"
---
# <a name="context-exchange-protocol"></a>Bağlam Değişimi Protokolü
Bu bölümde, sürüm 3,5 ' de Windows Communication Foundation (WCF) sürümü .NET Framework tanıtılan bağlam Değişim Protokolü açıklanmaktadır. Bu protokol, istemci kanalının bir hizmet tarafından sağlanan bağlamı kabul etmesine ve bu hizmetin aynı istemci kanalı örneği üzerinden gönderilen sonraki tüm isteklere uygulanmasına olanak tanır. Bağlam değişimi Protokolü uygulaması, sunucu ile istemci arasında bağlamı yaymak için aşağıdaki iki mekanizmadan birini kullanabilir: HTTP tanımlama bilgileri veya bir SOAP üst bilgisi.  
  
 Bağlam değişimi Protokolü özel bir kanal katmanında uygulanır. Kanal, <xref:System.ServiceModel.Channels.ContextMessageProperty> özelliği kullanarak uygulama katmanından ve öğesinden bağlamı iletişim kurar. Uç noktalar arasındaki iletim için bağlam değeri, kanal katmanında bir SOAP üst bilgisi olarak serileştirilir veya bir HTTP isteğini ve yanıtını temsil eden ileti özelliklerinden veya bu özelliklerden dönüştürülür. İkinci durumda, temel alınan kanal katmanlarından birinin HTTP istek ve yanıt iletisi özelliklerini sırasıyla HTTP tanımlama bilgilerine dönüştürdüğü beklenmektedir. Bağlamını değiştirmek için kullanılan mekanizmanın seçimi, <xref:System.ServiceModel.Channels.ContextExchangeMechanism> <xref:System.ServiceModel.Channels.ContextBindingElement>üzerindeki özelliği kullanılarak yapılır. Geçerli değerler veya `HttpCookie` `SoapHeader`' dir.  
  
 İstemcide, kanalın bir örneği, kanal özelliğindeki ayarlara bağlı olarak <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>iki modda çalışabilir.  
  
## <a name="mode-1-channel-context-management"></a>1\. mod: Kanal bağlam yönetimi  
 Bu, olarak `true`ayarlandığı varsayılan moddur <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> . Bu modda bağlam kanalı bağlamı yönetir ve ömrü boyunca bağlamı önbelleğe alır. Bağlam, `IContextManager` `GetContext` yöntemi çağırarak kanaldan Kanal özelliği aracılığıyla alınabilir. Kanal, `SetContext` yöntemi Kanal özelliği üzerinde çağırarak açılmadan önce belirli bağlamla önceden başlatılabilir. Kanal, bağlamı ile başlatıldıktan sonra sıfırlanamaz.  
  
 Aşağıda, bu moddaki ınvarıant 'ların bir listesi verilmiştir:  
  
- Kanal açıldıktan sonra kullanarak `SetContext` bağlamı sıfırlama girişimleri bir <xref:System.InvalidOperationException>oluşturur.  
  
- Giden bir iletide öğesini kullanarak <xref:System.ServiceModel.Channels.ContextMessageProperty> bağlamı gönderme girişimleri bir <xref:System.InvalidOperationException>oluşturur.  
  
- Belirli bir içeriğe sahip sunucudan bir ileti alındığında, Kanal belirli bir içerikle zaten başlatılmış olduğunda, bu bir <xref:System.ServiceModel.ProtocolException>ile sonuçlanır.  
  
    > [!NOTE]
    > Yalnızca Kanal açıkça herhangi bir bağlam kümesi olmadan açılırsa sunucudan ilk bağlam almak uygun olur.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty> Gelen ileti her zaman null olur.  
  
## <a name="mode-2-application-context-management"></a>Mod 2: Uygulama bağlamı yönetimi  
 Bu mod <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> olarak `false`ayarlanır. Bu modda bağlam kanalı bağlamı yönetmez. Kullanarak bağlamı alma, yönetme ve uygulama sorumluluğu uygulamanın sorumluluğundadır <xref:System.ServiceModel.Channels.ContextMessageProperty>. Herhangi bir çağrı `GetContext` yapmaya veya `SetContext` bir <xref:System.InvalidOperationException>ile sonuçlanır.  
  
 Hangi modun seçildiği, istemci kanalı fabrikası, ve <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ileti değişimi modellerini <xref:System.ServiceModel.Channels.IRequestSessionChannel>destekler.  
  
 Hizmette, gelen iletilerde istemci tarafından sağlanan bağlamın öğesine <xref:System.ServiceModel.Channels.ContextMessageProperty>dönüştürülmesi, kanalın bir örneği sorumludur. İleti özelliğine daha sonra uygulama katmanı veya diğer kanallar tarafından çağrı yığınında daha fazla erişilebilir. Hizmet kanalları aynı zamanda uygulama katmanının yanıt iletisine bir <xref:System.ServiceModel.Channels.ContextMessageProperty> ekleyerek istemciye geri yayılacağı yeni bir içerik değeri belirtmesini de sağlar. Bu özellik, bağlamanın yapılandırmasına bağlı olarak, bağlamını içeren SOAP üstbilgisine veya HTTP tanımlama bilgisine dönüştürülür. Hizmet kanalı dinleyicisi, <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>, ve <xref:System.ServiceModel.Channels.IReplySessionChannel> ileti değişimi düzenlerini destekler.  
  
 Bağlam değişimi Protokolü, http tanımlama bilgileri `wsc:Context` bağlamı yaymakta olmadığında bağlam bilgilerini temsil eden yeni bir SOAP üst bilgisi tanıtır. Bağlam üst bilgisi şeması, her biri dize anahtarı ve dize içeriği olan herhangi bir sayıda alt öğe sağlar. Aşağıda bir bağlam üst bilgisi örneği verilmiştir.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Modundayken, tanımlama bilgileri `SetCookie` üst bilgi kullanılarak ayarlanır. `HttpCookie` Tanımlama bilgisi adı `WscContext`. Tanımlama bilgisinin değeri, `wsc:Context` üst bilginin Base64 kodlamasıdır. Bu değer tırnak içine alınır.  
  
 Bağlam değeri, aktarım sırasında, WS-Addressing üst bilgilerinin korunduğu sırada değişiklik yapılmasının korunması gerekir – isteğin hizmette nereye dağıtılacağını belirlemekte kullanılacak üst bilgi kullanılır. Bu nedenle, bağlama ileti koruma özelliği sunduğunda, üstbilgininSOAPveyaAktarımdüzeyindedijitalolarakimzalanmasıyadaimzalanmasıveşifrelenmesigerekir.`wsc:Context` Bağlam yaymakta HTTP tanımlama bilgileri kullanıldığında, bunların aktarım güvenliği kullanılarak korunması gerekir.  
  
 Bağlam değişimi Protokolü için destek gerektiren hizmet uç noktaları, yayımlanan ilkede açık hale gelir. İstemcinin SOAP düzeyinde bağlam değişim protokolünü destekleme veya HTTP tanımlama bilgisi desteğini etkinleştirme gereksinimini temsil eden iki yeni ilke onayı eklenmiştir. Bu onayların hizmette ilke üzerinde oluşturulması, <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> özelliğin değeri tarafından aşağıdaki gibi denetlenir:  
  
- İçin <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>aşağıdaki onaylama oluşturulmuştur:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- İçin <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>aşağıdaki onaylama oluşturulmuştur:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
