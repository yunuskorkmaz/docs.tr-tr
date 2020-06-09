---
title: Bağlam Değişimi Protokolü
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 86d2a19b086fbd5d6be6f1a084bfd7aaace0e250
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597442"
---
# <a name="context-exchange-protocol"></a>Bağlam Değişimi Protokolü
Bu bölümde, sürüm 3,5 ' de Windows Communication Foundation (WCF) sürümü .NET Framework tanıtılan bağlam Değişim Protokolü açıklanmaktadır. Bu protokol, istemci kanalının bir hizmet tarafından sağlanan bağlamı kabul etmesine ve bu hizmetin aynı istemci kanalı örneği üzerinden gönderilen sonraki tüm isteklere uygulanmasına olanak tanır. Bağlam değişimi Protokolü uygulaması, bağlamı sunucu ile istemci arasında yaymak için aşağıdaki iki mekanizmadan birini kullanabilir: HTTP tanımlama bilgileri veya bir SOAP üstbilgisi.  
  
 Bağlam değişimi Protokolü özel bir kanal katmanında uygulanır. Kanal, özelliği kullanarak uygulama katmanından ve öğesinden bağlamı iletişim kurar <xref:System.ServiceModel.Channels.ContextMessageProperty> . Uç noktalar arasındaki iletim için bağlam değeri, kanal katmanında bir SOAP üst bilgisi olarak serileştirilir veya bir HTTP isteğini ve yanıtını temsil eden ileti özelliklerinden veya bu özelliklerden dönüştürülür. İkinci durumda, temel alınan kanal katmanlarından birinin HTTP istek ve yanıt iletisi özelliklerini sırasıyla HTTP tanımlama bilgilerine dönüştürdüğü beklenmektedir. Bağlamını değiştirmek için kullanılan mekanizmanın seçimi <xref:System.ServiceModel.Channels.ContextExchangeMechanism> , üzerindeki özelliği kullanılarak yapılır <xref:System.ServiceModel.Channels.ContextBindingElement> . Geçerli değerler veya ' dir `HttpCookie` `SoapHeader` .  
  
 İstemcide, kanalın bir örneği, kanal özelliğindeki ayarlara bağlı olarak iki modda çalışabilir <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> .  
  
## <a name="mode-1-channel-context-management"></a>Mod 1: Kanal bağlam yönetimi  
 Bu, olarak ayarlandığı varsayılan moddur <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> `true` . Bu modda bağlam kanalı bağlamı yönetir ve ömrü boyunca bağlamı önbelleğe alır. Bağlam, yöntemi çağırarak kanaldan Kanal özelliği aracılığıyla alınabilir `IContextManager` `GetContext` . Kanal, `SetContext` yöntemi Kanal özelliği üzerinde çağırarak açılmadan önce belirli bağlamla önceden başlatılabilir. Kanal, bağlamı ile başlatıldıktan sonra sıfırlanamaz.  
  
 Aşağıda, bu moddaki ınvarıant 'ların bir listesi verilmiştir:  
  
- Kanal açıldıktan sonra kullanarak bağlamı sıfırlama girişimleri `SetContext` bir oluşturur <xref:System.InvalidOperationException> .  
  
- Giden bir iletide öğesini kullanarak bağlamı gönderme girişimleri <xref:System.ServiceModel.Channels.ContextMessageProperty> bir oluşturur <xref:System.InvalidOperationException> .  
  
- Belirli bir içeriğe sahip sunucudan bir ileti alındığında, Kanal belirli bir içerikle zaten başlatılmış olduğunda, bu bir ile sonuçlanır <xref:System.ServiceModel.ProtocolException> .  
  
    > [!NOTE]
    > Yalnızca Kanal açıkça herhangi bir bağlam kümesi olmadan açılırsa sunucudan ilk bağlam almak uygun olur.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty>Gelen ileti her zaman null olur.  
  
## <a name="mode-2-application-context-management"></a>Mod 2: uygulama bağlamı yönetimi  
 Bu mod <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> olarak ayarlanır `false` . Bu modda bağlam kanalı bağlamı yönetmez. Kullanarak bağlamı alma, yönetme ve uygulama sorumluluğu uygulamanın sorumluluğundadır <xref:System.ServiceModel.Channels.ContextMessageProperty> . Herhangi bir çağrı yapmaya `GetContext` veya `SetContext` bir ile sonuçlanır <xref:System.InvalidOperationException> .  
  
 Hangi modun seçildiği, istemci kanalı fabrikası, <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ileti değişimi modellerini destekler.  
  
 Hizmette, gelen iletilerde istemci tarafından sağlanan bağlamın öğesine dönüştürülmesi, kanalın bir örneği sorumludur <xref:System.ServiceModel.Channels.ContextMessageProperty> . İleti özelliğine daha sonra uygulama katmanı veya diğer kanallar tarafından çağrı yığınında daha fazla erişilebilir. Hizmet kanalları aynı zamanda uygulama katmanının yanıt iletisine bir ekleyerek istemciye geri yayılacağı yeni bir içerik değeri belirtmesini de sağlar <xref:System.ServiceModel.Channels.ContextMessageProperty> . Bu özellik, bağlamanın yapılandırmasına bağlı olarak, bağlamını içeren SOAP üstbilgisine veya HTTP tanımlama bilgisine dönüştürülür. Hizmet kanalı dinleyicisi,, <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel> ve <xref:System.ServiceModel.Channels.IReplySessionChannel> ileti değişimi düzenlerini destekler.  
  
 Bağlam değişimi Protokolü, `wsc:Context` http tanımlama bilgileri bağlamı yaymakta olmadığında bağlam bilgilerini temsil eden yeni bir SOAP üst bilgisi tanıtır. Bağlam üst bilgisi şeması, her biri dize anahtarı ve dize içeriği olan herhangi bir sayıda alt öğe sağlar. Aşağıda bir bağlam üst bilgisi örneği verilmiştir.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 `HttpCookie`Modundayken, tanımlama bilgileri `SetCookie` üst bilgi kullanılarak ayarlanır. Tanımlama bilgisi adı `WscContext` . Tanımlama bilgisinin değeri, üst bilginin Base64 kodlamasıdır `wsc:Context` . Bu değer tırnak içine alınır.  
  
 Bağlam değeri, aktarım sırasında, WS-Addressing üst bilgilerinin korunduğu sırada değişiklik yapılmasının korunması gerekir – isteğin hizmette nereye dağıtılacağını belirlemekte kullanılacak üst bilgi kullanılır. `wsc:Context`Bu nedenle, bağlama ileti koruma özelliği sunduğunda, üst BILGININ SOAP veya Aktarım düzeyinde dijital olarak imzalanması ya da imzalanması ve şifrelenmesi gerekir. Bağlam yaymakta HTTP tanımlama bilgileri kullanıldığında, bunların aktarım güvenliği kullanılarak korunması gerekir.  
  
 Bağlam değişimi Protokolü için destek gerektiren hizmet uç noktaları, yayımlanan ilkede açık hale gelir. İstemcinin SOAP düzeyinde bağlam değişim protokolünü destekleme veya HTTP tanımlama bilgisi desteğini etkinleştirme gereksinimini temsil eden iki yeni ilke onayı eklenmiştir. Bu onayların hizmette ilke üzerinde oluşturulması, özelliğin değeri tarafından <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> aşağıdaki gibi denetlenir:  
  
- İçin <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader> aşağıdaki onaylama oluşturulmuştur:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- İçin <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie> aşağıdaki onaylama oluşturulmuştur:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Web Hizmetleri Protokolleri Birlikte Çalışabilirlik Kılavuzu](web-services-protocols-interoperability-guide.md)
