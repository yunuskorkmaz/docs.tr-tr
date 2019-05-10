---
title: ASP.NET Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 8102b91ba14b75ec9cbd2a683b68c3723a77aed0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649433"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web Hizmetlerini WCF'ye Taşıma
ASP.NET barındırma Hizmetleri Internet Information Services (IIS) içinde olanakları yanı sıra Web hizmetleri oluşturmak için .NET Framework sınıf kitaplıkları ve araçları sağlar. .NET Framework sınıf kitaplıkları, araçları ve Web Hizmetleri tarafından kullanılan dahil olmak üzere herhangi bir protokol kullanarak iletişim kurmak için barındırma özellikleri yazılım varlıkları etkinleştirmek için Windows Communication Foundation (WCF) sağlar.  ASP.NET Web hizmetlerini WCF'ye taşıma, yeni özellikler ve geliştirmeler için WCF özgü avantajlarından yararlanmak uygulamalarınızı sağlar.  
  
 WCF, ASP.NET Web hizmetlerini göre çeşitli önemli avantajları vardır. Yalnızca Web hizmetleri oluşturmak için ASP.NET Web Hizmetleri Araçları olmakla birlikte, WCF yazılım varlıkların birbirleriyle iletişim kurması için yapılması gerekir, kullanılabilen araçlar sağlar. Bu teknolojiler geliştiriciler sırayla yazılım tamamlanma süresi yanı sıra, yazılım geliştirme kaynakları maliyeti azaltır farklı yazılım iletişim senaryolara uyum sağlamak için yerinizi bilmesi gereken sayısını azaltır geliştirme projeleri.  
  
 Web hizmeti geliştirme projeler için bile, WCF, ASP.NET Web Hizmetleri desteği değerinden daha fazla Web hizmeti protokolleri destekler. Bu ek protokoller, ilgili, daha karmaşık çözümleri sağlar. diğer bir şey, güvenilir oturumlar ve işlemleri arasında.  
  
 WCF, ASP.NET Web Hizmetleri daha iletileri taşıma için daha fazla protokollerini destekler. ASP.NET Web hizmetlerini Köprü Metni Aktarım Protokolü (HTTP) kullanarak ileti gönderme yalnızca destekler. WCF İletim Denetimi Protokolü (Adlandırılmış Kanallar ve Microsoft Message Queuing (MSMQ) TCP), yanı sıra, HTTP kullanarak ileti gönderme destekler. Daha da önemlisi, WCF ek aktarım protokolleri destekleyecek şekilde genişletilebilir. Bu nedenle, yazılım WCF kullanılarak geliştirilen çok çeşitli böylece olası yatırım getirisini artırılması, diğer yazılım birlikte çalışmak üzere uyarlanabilir.  
  
 WCF dağıtımı için çok daha zengin özellikleri ve uygulamaları ASP.NET Web Hizmetleri daha yönetme sağlar. ASP.NET ayrıca sahip bir yapılandırma sistemi yanı sıra WCF yapılandırma Düzenleyicisi sunar. alıcılar ve herhangi bir sayıda aracılar, bir izleme görüntüleyicisinde, ileti günlüğe kaydetme, performans sayaçları, geniş bir dizi aracılığıyla geri gönderenlerden Etkinlik izleme ve Windows Yönetim Araçları desteği.  
  
 Veya ASP.NET Web hizmetlerini birkaç seçeneğiniz vardır kullanmayı düşündüğünü kullanıyorsanız bu olası faydaları WCF göre ASP.NET Web Hizmetleri, verilen:  
  
- ASP.NET Web Hizmetleri ve WCF tarafından proffered avantajları forego devam edin.  
  
- Gelecekte bir zamanda WCF benimseme amacıyla yapılıyorsa, ASP.NET Web hizmetlerini kullanmaya devam edin. Bu bölümdeki konular, yeni ASP.NET Web hizmeti uygulama ileride WCF uygulamaları ile birlikte kullanabilmek için için aday en üst düzeye çıkarmak açıklanmaktadır. Bu bölümdeki konular, ayrıca yeni ASP.NET Web hizmetlerini WCF'ye taşıma bunları daha kolay hale getirmek için yapı işlemleri açıklanmaktadır. Ancak, önemli olan hizmetleri güvenli hale getirme veya güvenilirlik veya işlem Güvenceleri gereklidir veya özel yönetim olanakları oluşturulması gerekir, ardından WCF benimsemek için daha iyi bir seçenektir. WCF tam olarak bu tür senaryolar için tasarlanmıştır.  
  
- Mevcut ASP.NET Web hizmeti uygulamalarınızı korumak devam edebilirsiniz. yeni geliştirme için WCF benimseyin. Bu büyük olasılıkla en iyi bir seçimdir. WCF, avantajlarını kullanmak üzere var olan uygulamaları değiştirmeyi maliyeti sparing sırasında verir. Bu senaryoda yeni WCF uygulamaları mevcut ASP.NET uygulamaları ile birlikte bulunabilir. Yeni WCF uygulamaları mevcut ASP.NET Web hizmetlerini kullanma olanağına ve WCF WCF ASP.NET uyumluluk modunun da mevcut ASP.NET uygulamalarına yeni işletimsel özelliklerine program için kullanılabilir.  
  
- WCF benimseyin ve varolan ASP.NET Web hizmeti uygulamalarını wcf'ye TAŞIMA geçirin. WCF tarafından sağlanan özellikleri ile mevcut uygulamaları geliştirmek için veya mevcut bir ASP.NET Web Hizmetleri içinde yeni işlevselliği, daha güçlü WCF uygulamaları yeniden oluşturmak için bu seçeneği tercih edebilirsiniz.  
  
> [!NOTE]
>  Bir WCF Hizmeti barındırılıyorsa dikkatli'nin alınması gereken IIS tarafından 5.x ve ASP.NET kaldırılır. Bir WCF Hizmeti IIS tarafından barındırılan zaman ASP.NET kaldırdıysanız 5.x, hizmet kodunu istenebilir. ASP.NET, IIS çalıştıran bir işletim sisteminde kaldırılması zaman 5.x ve WCF kaldırılır, .svc uzantılı bir dosya bir metin dosyası olarak kabul edilir ve herhangi bir kaynak kod dahil olmak üzere içeriği istemciye döndürülür.  
  
 Bu bölümde ayrıntılı Bu seçenekler anlatılmakta, ASP.NET Web hizmetlerini WCF'ye karşılaştırır ve kodunuzu ASP.NET Web hizmetlerini WCF'ye geçirme hakkında yönergeler açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation'ı benimsemeyi bekleme: Gelecekteki taşınmayı kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [Windows Communication Foundation'ı benimsemeyi bekleme: Gelecekteki tümleştirmeyi kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [Windows Communication Foundation'ı Benimseme](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
