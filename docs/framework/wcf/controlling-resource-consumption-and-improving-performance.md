---
title: Kaynak Tüketimini Denetleme ve Performansı Geliştirme
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 11d1333ed0ae8b46f8f87fa6f4643d4b31fac3ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664167"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Kaynak Tüketimini Denetleme ve Performansı Geliştirme
Bu konuda çeşitli özelliklerini denetimi kaynak tüketimi için çalışma ve performans ölçümlerini etkileyen farklı alanlarda Windows Communication Foundation (WCF) mimarisi açıklanmaktadır.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Wcf'de kaynak tüketimini sınırlamak özellikleri
 Windows Communication Foundation (WCF), güvenlik veya performans amaçlı işlemler belirli türlerdeki kısıtlamalar geçerlidir. Bu kısıtlamalar, iki ana biçimde, kotalar ve kısıtlamalar da gelir. *Kotalar* ulaşıldığında veya aşıldı sistemde belirli bir noktada hemen bir özel durum tetikleyeceğinizi limitlerdir. *Kısıtlar* hemen bir özel durum oluşturulmasına neden olmaz limitlerdir. Bunun yerine, bir azaltma sınırına ulaşıldığında, işleme devam eder ancak sınırları içinde bu kısıtlama değere göre ayarlayın. Bu sınırlı işlem başka bir yerde bir özel durum tetikleyebilir, ancak bu uygulama gereksinimlerinize bağlıdır.

 Kotalar ve kısıtlamalar arasındaki ayrımı ek olarak, bazı kısıtlayan özellikleri serileştirme düzeyinde, aktarım düzeyinde bazı ve bazı uygulama düzeyinde yer alır. Örneğin, kota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, tüm sistem tarafından sağlanan aktarım bağlama öğeleri tarafından uygulanan 65.536 bayt için varsayılan olarak ayarlandığı kötü amaçlı istemcileri, hizmet reddi saldırılarına karşı bir hizmet aşırı şekilde bellek neden olarak yapmasının engellemesini Tüketim. (Genellikle, performans bu değer indirerek artırabilirsiniz.)

 Bir seri hale getirme kota örneğidir <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> tek bir seri hale getirici serileştiren veya seri durumdan çıkarır nesneleri sayısı belirten özellik <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> yöntem çağrısı. Uygulama düzeyi kısıtlama örneğidir <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> özelliği, varsayılan olarak 10 eşzamanlı oturum kanalı bağlantı sayısını kısıtlar. (Kotalar aksine bu kısıtlama değeri ulaşılırsa uygulama işleme devam eder ancak hiçbir yeni oturumdaki kanallar kabul eden bir oturumdaki kanallar birine tamamlanıncaya kadar yeni istemciler bağlanamıyor anlamına gelir.)

 Bu denetimler belirli saldırı türlerine karşı karşı bir kullanıma hazır azaltma sağlamak veya bellek Ayak izi, başlangıç saati ve benzeri gibi performans ölçümlerini iyileştirmek için tasarlanmıştır. Ancak, uygulamaya bağlı olarak, bu denetimleri hizmet uygulama performansını engelleyebildiğinden veya hiç çalışmasını engellemek. Örneğin, stream video için tasarlanmış bir uygulama varsayılan kolayca aşabilir <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> özelliği. Bu konu, çeşitli denetimleri genel bir bakış uygulamalarına tüm WCF düzeylerinde uygulanan bir ayar, uygulamanızın olup hindering hakkında daha fazla bilgi edinmek için çeşitli yolları açıklar ve çeşitli sorunları düzeltmek için yollar açıklar sağlar. Çoğu kısıtlamalar ve bazı kotalar temel özellik serileştirme veya aktarım kısıtlaması olsa bile uygulama düzeyinde kullanılabilir. Örneğin, ayarlayabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> özelliğini kullanarak <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> hizmet sınıfı özelliği.

> [!NOTE]
> Önce okumanız gereken belirli bir sorun varsa, [WCF sorun giderme hızlı başlangıcı](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) sorununuzu (ve bir çözüm) vardır listelenmiş olup olmadığını görmek için.

 Seri hale getirme işlemleri kısıtlayan özellikleri listelenmiştir [veriler için güvenlik konuları](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Taşımasıyla ilgili kaynakların tüketimini kısıtlamak özellikler listelenir [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md). Uygulama katmanındaki kaynaklarının kullanımını kısıtlayan özellikleri olan üyeleri <xref:System.ServiceModel.Dispatcher.ServiceThrottle> sınıfı.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Uygulama ve kota ayarları ile ilgili performans sorunlarını algılama
 Ortak güvenlik sorunlarına karşı temel koruma sağlarken, çok çeşitli uygulama türleri arasında temel uygulama işlevselliğini etkinleştirmek için yukarıdaki değerleri varsayılan seçildi. Ancak, aksi takdirde uygulama güvenlidir ve tasarlandığı gibi çalışır ancak farklı uygulama tasarımları bir veya daha fazla kısıtlama ayarlarını aşabilir. Bu durumlarda, hangi Kısıtlama değerlerinin aşılsa belirlemeniz gerekir ve ne düzeyi ve uygulama performansını artırmak için eylem uygun kursu karar verin.

 Genellikle, uygulama yazma ve hata ayıklama, ayarladığınızda <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini `true` yapılandırma dosyası veya programlama yoluyla. Bu, istemci uygulaması izleme için hizmet özel durum yığın izlemelerini dönmek için WCF bildirir. Bu özellik, sorun ise hangi kota ayarları dahil edilmelidir, görüntüleme biçimini çoğu uygulama düzeyi özel durumları bildirir.

 Bazı özel durumlar çalışma zamanında uygulama katmanına görünürlüğünü aşağıda gerçekleşir ve bu mekanizma kullanılarak döndürülmez ve bunlar tarafından özel işlenebilmesini değil <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> uygulaması. Microsoft Visual Studio gibi geliştirme ortamlarında varsa, bu özel durumların çoğu otomatik olarak görüntülenir. Ancak, bazı özel durumlar gibi geliştirme ortamı ayarları tarafından maskelenmiş olamaz [yalnızca kendi kodum](/visualstudio/debugger/just-my-code) Visual Studio.

 Geliştirme ortamınızı yeteneklerini bağımsız olarak, tüm özel durumların hatalarını ayıklayabilir ve uygulamalarınızın performansını ayarlamak için WCF izleme ve iletileri günlüğe kaydetme özelliklerini kullanabilirsiniz. Daha fazla bilgi için [kullanarak uygulamanızı sorun giderme için izleme](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Performans sorunlarını ve XmlSerializer
 Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamalar <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve yavaş başlatma performansı düşürebilir çalışma zamanında bu veri türleri için serileştirme kodu derleyin.

> [!NOTE]
> Önceden oluşturulan serileştirme kod, yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.

 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) derlenmiş bütünleştirilmiş uygulama için gerekli serileştirme kod oluşturarak bu uygulamaları için başlatma performansını geliştirebilir. Daha fazla bilgi için [nasıl yapılır: Başlangıç zamanı, istemci XmlSerializer kullanarak WCF uygulamalarının geliştirilmesine](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>WCF hizmetleri altında ASP.NET barındırırken performans sorunları
 Bir WCF Hizmeti IIS ve ASP.NET altında barındırıldığında, aktarım hızı ve bellek Ayak izi WCF Hizmeti IIS ve ASP.NET yapılandırma ayarlarının etkileyebilir.  ASP.NET performansıyla ilgili daha fazla bilgi için bkz. [ASP.NET performans geliştirme](https://go.microsoft.com/fwlink/?LinkId=186462).  Bir ayar olabilir istenmeyen sonuçları olan <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, bir özelliği olan <xref:System.Web.Configuration.ProcessModelSection>. Uygulamanızın istemciler sabit ya da küçük bir dizi varsa, ayarı <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2'ye bir CPU kullanımı % 100 olan bir çok işlemcili bir makine üzerinde bir aktarım hızı boost sağlayabilir. Bu performans artışı bir maliyetle birlikte gelir: Ayrıca ölçeklenebilirliği de azaltabilir bellek kullanımında artışa neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve Tanılama](../../../docs/framework/wcf/diagnostics/index.md)
- [Büyük Veriler ve Akış Yapma](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
