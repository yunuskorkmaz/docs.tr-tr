---
title: "Kaynak Tüketimini Denetleme ve Performansı Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8cd80805eee58db16f5865683cbd322a49c554a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Kaynak Tüketimini Denetleme ve Performansı Geliştirme
Bu konu, farklı bölgelerdeki çeşitli özellikleri açıklar [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] kaynak tüketimini denetleme ve performans ölçümleri etkileyen iş mimarisi.  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>WCF kaynak tüketimini sınırlamak özellikleri  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]belirli türde bir işlemler güvenlik veya performans amacıyla kısıtlamalar geçerlidir. Bu kısıtlamaların iki ana biçimde, kotaları ve kısıtlamaları gelir. *Kotalar* ulaştı veya aşıldı sistemde belirli bir noktada hemen bir özel durum harekete kısıtlamalardır. *Kısıtlar* hemen bir özel durum oluşturulmasına neden olmaz kısıtlamalardır. Bunun yerine, bir kısıtlama sınırına ulaşıldığında, işleme devam eder ancak sınırlarda tarafından kısıtlama değeri ayarlayın. Sınırlı bu işlem başka bir yerde bir özel durum harekete, ancak bu uygulamanın bağlıdır.  
  
 Kotaları ve kısıtlamaları arasında ayrım yanı sıra kısıtlayan bazı özellikleri seri hale getirme düzeyinde, bazı aktarım düzeyinde ve bazı uygulama düzeyinde bulunur. Örneğin, kota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, tüm sistem tarafından sağlanan aktarım bağlama öğeleri tarafından uygulanan ayarlanmış 65,536 bayt varsayılan olarak hizmet reddi saldırılarına karşı bir hizmet olarak aşırı bellek neden olarak yapmasının kötü amaçlı istemcileri azaltabilir Tüketim. (Tipik olarak, performans bu değeri azaltarak artırabilirsiniz.)  
  
 Bir seri hale getirme kota örneğidir <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> tek bir seri hale getirici serileştiren veya seri durumdan çıkarır nesneler en fazla sayısını belirtir özelliği <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> yöntem çağrısı. Uygulama düzeyi kısıtlama örneğidir <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> varsayılan olarak 10 eşzamanlı süre sonuyla kanalı bağlantıları sayısını kısıtlar özelliği. (Kotaları aksine bu kısıtlama değeri ulaştıysanız, uygulamanın devam ettirir, ancak yeni hiçbir süre sonuyla kanalı diğer süre sonuyla kanallarını sonlanana yeni istemciler bağlanamıyor anlamı kabul eder.)  
  
 Bu denetimler, belirli türde bir saldırılarına karşı Giden kutusu azaltma sağlamak ya da performans ölçümleri bellek alanını, başlangıç saati vb. gibi artırmak için tasarlanmıştır. Ancak, uygulamaya bağlı olarak, bu denetimleri hizmet uygulama performansını olumsuz yönde hiç çalışma uygulamanın veya engeller. Örneğin, akış video için tasarlanmış bir uygulama varsayılan kolayca aşabilir <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> özelliği. Bu konu tüm düzeylerdeki uygulamalara uygulanan çeşitli denetimlerin genel bir bakış sağlar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bir ayar, uygulamanızın olup hindering hakkında daha fazla bilgi edinmek için çeşitli yollarını açıklar ve çeşitli düzeltmek için yolları açıklanmaktadır sorunları. Çoğu kısıtlamaları ve bazı kotalar temel özelliği seri hale getirme veya taşıma kısıtlaması olsa bile uygulama düzeyinde kullanılabilir. Örneğin, ayarlayabileceğiniz <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> özelliğini kullanarak <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> hizmet sınıfı özelliği.  
  
> [!NOTE]
>  Belirli bir sorun varsa, ilk okumalısınız [WCF sorun giderme Hızlı Başlangıç](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) sorununuzu (ve bir çözüm) var. listelenmiş olup olmadığını görmek için.  
  
 Seri hale getirme işlemlerini kısıtlamak özellikler listelenmiştir [veriler için güvenlik konuları](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Taşımasıyla ilgili kaynaklarının kullanımını kısıtlamak özellikler listelenmiştir [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md). Uygulama katmanı kaynaklarının kullanımını kısıtlamak özellikleri üyeleri olan <xref:System.ServiceModel.Dispatcher.ServiceThrottle> sınıfı.  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Uygulama ve kota ayarlarıyla ilgili performans sorunlarını algılama  
 Yukarıdaki değerleri Varsayılanları, genel güvenlik sorunları karşı temel koruma sağlarken çok çeşitli uygulama türleri arasında temel uygulama işlevselliğini etkinleştirmek için seçildi. Ancak, aksi takdirde uygulamanın güvenli ve tasarlandığı gibi çalışır ancak farklı bir uygulama tasarımları bir veya daha fazla kısıtlama ayarlarını aşabilir. Bu durumlarda, hangi Kısıtlama değerlerinin aşıldı tanımlamanız gerekir ve ne düzey ve uygulama verimliliğini artırmak için eylem uygun seyri üzerinde karar verin.  
  
 Genellikle, uygulama yazmak ve bu hata ayıklama, ayarladığınızda <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğine `true` yapılandırma dosyası veya program aracılığıyla. Bu bildirir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] görüntülemek için istemci uygulaması hizmeti özel durum Yığın izlemeleri dönün. Bu özellik, çoğu uygulama düzeyinde istisnalar hangi kota ayarları söz konusu, bu sorun olursa görüntülemek şekilde bildirir.  
  
 Bazı özel durumlar uygulama katmanın görünürlüğünü aşağıda çalışma zamanında gerçekleşir ve bu mekanizmayı kullanarak döndürülmez ve bunlar özel tarafından ele alınması değil <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> uygulaması. Microsoft Visual Studio gibi geliştirme ortamında varsa, bu özel durumlar çoğunu otomatik olarak görüntülenir. Ancak, bazı özel durumlar gibi geliştirme ortamı ayarları tarafından maskelenecek [sadece kendi kodumu](http://go.microsoft.com/fwlink/?LinkId=82174) Visual Studio 2005'te ayarlar.  
  
 Geliştirme ortamınızı yeteneklerini bağımsız olarak yeteneklerini kullanabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ileti izleme ve tüm özel durumları hata ayıklama ve uygulamalarınızın performansını ayarlamak için kaydetme. Daha fazla bilgi için bkz: [kullanarak izleme uygulamanız sorun giderme için](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="performance-issues-and-xmlserializer"></a>Performans sorunlarını ve XmlSerializer  
 Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamaları <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu veri türleri için seri hale getirme kodu, yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında derleyin.  
  
> [!NOTE]
>  Önceden oluşturulmuş serileştirme kod, yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.  
  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) başlangıcından bu uygulamalar için uygulama için derlenmiş derlemelerden gerekli serileştirme kod oluşturarak performansı artırabilir. Daha fazla bilgi için bkz: [nasıl yapılır: Başlangıç saati, WCF istemci XmlSerializer kullanarak uygulamaları geliştirmek](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>WCF hizmetleri ASP.NET altında barındırdığında performans sorunları  
 Bir WCF Hizmeti IIS ve ASP.NET altında barındırıldığında, IIS ve ASP.NET yapılandırma ayarlarını WCF hizmetini işleme ve bellek ayak etkileyebilir.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]ASP.NET performansı bkz [ASP.NET performans geliştirme](http://go.microsoft.com/fwlink/?LinkId=186462).  Bir ayar olabilir istenmeyen sonuçlara olan <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, bir özelliği olan <xref:System.Web.Configuration.ProcessModelSection>. Uygulamanızın istemci sabit veya küçük bir sayısı varsa, ayarı <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 CPU kullanımı % 100 yakın olan çok işlemcili bir makinede verimliliği artırma sağlayabilir. Bu artış performans maliyeti ile gelir: de ölçeklenebilirlik azaltabilir bellek kullanımında artışa neden olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetim ve tanılama](../../../docs/framework/wcf/diagnostics/index.md)  
 [Büyük veri ve akış](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
