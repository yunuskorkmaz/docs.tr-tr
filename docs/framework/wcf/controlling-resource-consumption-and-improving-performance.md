---
title: Kaynak Tüketimini Denetleme ve Performansı Geliştirme
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 976eb1e4a507d3c09bbc6e030985cbc3143b5946
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320612"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Kaynak Tüketimini Denetleme ve Performansı Geliştirme
Bu konuda, kaynak tüketimini denetlemek ve performans ölçümlerini etkilemek için çalışan Windows Communication Foundation (WCF) mimarisinin farklı alanlarındaki çeşitli özellikler açıklanmaktadır.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>WCF 'de kaynak tüketimini kısıtlayan Özellikler
 Windows Communication Foundation (WCF), güvenlik veya performans amaçları için belirli işlem türlerinde kısıtlamalar uygular. Bu kısıtlamalar iki ana formda gelir, Kotalar ve kısıtlar. *Kotalar* , sistem içindeki bir noktada anlık özel durum tetiklemeye ulaşıldığında veya aşılmışsa kısıtlar. *Kısıtlar* , bir özel durumun oluşturulmasına hemen neden olmayan sınırlardır. Bunun yerine, bir kısıtlama sınırına ulaşıldığında işleme devam eder, ancak bu kısıtlama değeri tarafından ayarlanan limitlerin içinde olur. Bu sınırlı işlem bir özel durumu başka bir yerde tetikleyebilir, ancak bu uygulamaya bağımlıdır.

 Kotalar ve kısıtlar arasındaki ayrım konusunda ek olarak, bazı kısıtlama özellikleri serileştirme düzeyinde, bazıları Aktarım düzeyinde ve bazı uygulama düzeyinde bulunur. Örneğin, sistem tarafından sağlanan tüm aktarım bağlama öğeleri tarafından uygulanan <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> kotası, kötü amaçlı istemcilerin, çok fazla bellek oluşmasına neden olan hizmet reddi saldırılarına karşı, varsayılan olarak 65.536 bayta ayarlanır Mine. (Genellikle, bu değeri azaltarak performansı artırabilirsiniz.)

 Serileştirme kotasına örnek olarak, seri hale getirici seri hale getirilen veya tek bir <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> Yöntem çağrısında seri hale getirilen en fazla nesne sayısını belirten <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> özelliğidir. Uygulama düzeyinde bir kısıtlama örneği, varsayılan olarak, eş zamanlı oturumsuz bağlantı sayısını 10 ' a kısıtlayan <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> özelliğidir. (Kotaların aksine, bu azaltma değerine ulaşıldığında uygulama işleme devam eder ancak yeni oturumsuz kanallar kabul etmez, bu da yeni istemcilerin diğer oturumlardan biri sonlandırana kadar bağlanamaması anlamına gelir.)

 Bu denetimler, belirli saldırı türlerine karşı bir kullanıma hazır risk azaltma veya bellek kaplama, başlangıç saati vb. gibi performans ölçümlerini geliştirmeye yönelik olarak tasarlanmıştır. Ancak, uygulamaya bağlı olarak, bu denetimler hizmet uygulaması performansını engelleyebilir veya uygulamanın hiç çalışmasını engelleyebilir. Örneğin, video akışı için tasarlanan bir uygulama, varsayılan <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> özelliğini kolayca aşabilirler. Bu konu, tüm WCF düzeylerinde uygulamalara uygulanan çeşitli denetimlere genel bakış sağlar, bir ayarın uygulamanız hindering olup olmadığı hakkında daha fazla bilgi edinmek için çeşitli yollar ve çeşitli sorunları düzeltme yollarını açıklar. En kısıtları ve bazı kotalar, temel özellik bir serileştirme veya aktarım kısıtlaması olduğunda bile uygulama düzeyinde kullanılabilir. Örneğin, hizmet sınıfındaki <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> özelliğini kullanarak <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> özelliğini ayarlayabilirsiniz.

> [!NOTE]
> Belirli bir sorununuz varsa, önce sorunun (ve bir çözümün) orada listelenip listelenmediğini öğrenmek için önce [WCF sorun giderme hızlı](wcf-troubleshooting-quickstart.md) başlangıcı ' nı okumalısınız.

 Serileştirme süreçlerini kısıtlayan özellikler, [veriler Için güvenlik konuları](./feature-details/security-considerations-for-data.md)' nda listelenmiştir. Aktarımlarla ilgili kaynakların tüketimini kısıtlayan Özellikler [Aktarım kotalarında](./feature-details/transport-quotas.md)listelenmiştir. Uygulama katmanındaki kaynakların tüketimini kısıtlayan Özellikler <xref:System.ServiceModel.Dispatcher.ServiceThrottle> sınıfının üyeleridir.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Kota ayarlarıyla Ilgili uygulama ve performans sorunları algılanıyor
 Yaygın güvenlik sorunlarına karşı temel koruma sağlarken, yukarıdaki değerlerin Varsayılanları çok çeşitli uygulama türleri genelinde temel uygulama işlevselliğini etkinleştirmek için seçilmiştir. Bununla birlikte, farklı uygulama tasarımları bir veya daha fazla azaltma ayarını aşabileceğinden, aksi halde uygulama güvenli hale gelse ve tasarlandıkları gibi çalışır. Bu durumlarda, hangi kısıtlama değerlerinin aşıldığını ve hangi düzeyde olduğunu tanımlamalısınız ve uygulama aktarım hızını artırmak için uygun eylem konusuna karar vermelisiniz.

 Genellikle, uygulamayı yazarken ve hata ayıklarken, <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini yapılandırma dosyasında veya program aracılığıyla `true` olarak ayarlarsınız. Bu, WCF 'yi, görüntüleme için hizmet özel durum yığını izlemelerini istemci uygulamasına döndürecek şekilde yönlendirir. Bu özellik, uygulama düzeyindeki özel durumların çoğunu, bu sorun varsa hangi kota ayarlarının dahil olabileceğini göstermek için bir şekilde bildirir.

 Bazı özel durumlar, uygulama katmanının görünürlüğü altında çalışma zamanında gerçekleşir ve bu mekanizma kullanılarak döndürülmez ve özel bir @no__t 0 uygulaması tarafından işlenmeyebilir. Microsoft Visual Studio gibi bir geliştirme ortamındaysanız, bu özel durumların çoğu otomatik olarak görüntülenir. Ancak bazı özel durumlar, [yalnızca kendi kodum](/visualstudio/debugger/just-my-code) Visual Studio gibi geliştirme ortamı ayarları tarafından maskelenebilir.

 Geliştirme ortamınızın özelliklerine bakılmaksızın, tüm özel durumların hatalarını ayıklamak ve uygulamalarınızın performansını ayarlamak için WCF izleme ve ileti günlüğe kaydetme yeteneklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [uygulamanızın sorunlarını gidermek Için Izlemeyi kullanma](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Performans sorunları ve XmlSerializer
 @No__t-0 kullanılarak seri hale getirilebilir veri türlerini kullanan hizmetler ve istemci uygulamaları, çalışma zamanında bu veri türleri için serileştirme kodu oluşturur ve derler ve bu da yavaş başlangıç performansına yol açabilir.

> [!NOTE]
> Önceden oluşturulmuş serileştirme kodu, hizmetlerde değil yalnızca istemci uygulamalarında kullanılabilir.

 [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , uygulama için derlenmiş derlemelerden gerekli serileştirme kodunu oluşturarak bu uygulamalar için başlangıç performansını iyileştirebilir. Daha fazla bilgi için bkz. [nasıl yapılır: XmlSerializer kullanarak WCF Istemci uygulamalarının başlangıç zamanını geliştirme](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>WCF hizmetlerini ASP.NET altında barındırırken performans sorunları
 Bir WCF hizmeti IIS ve ASP.NET altında barındırıldığı zaman IIS ve ASP.NET yapılandırma ayarları, WCF hizmetinin aktarım hızını ve bellek parmak izini etkileyebilir.  ASP.NET performansı hakkında daha fazla bilgi için bkz. [ASP.net performansını geliştirme](https://go.microsoft.com/fwlink/?LinkId=186462).  İstem dışı sonuçlara sahip olabilecek bir ayar, <xref:System.Web.Configuration.ProcessModelSection> ' in bir özelliği olan <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> ' dır. Uygulamanızda sabit veya az sayıda istemci varsa, <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> ' ı 2 olarak ayarlamak, CPU kullanımı %100 ' a yakın olan çok işlemcili bir makineye bir verimlilik artışı sağlayabilir. Bu performans artışı bir maliyetle birlikte gelir: Ayrıca, bellek kullanımında artışa neden olur ve bu da ölçeklenebilirliği azaltabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve Tanılama](./diagnostics/index.md)
- [Büyük Veriler ve Akış Yapma](./feature-details/large-data-and-streaming.md)
