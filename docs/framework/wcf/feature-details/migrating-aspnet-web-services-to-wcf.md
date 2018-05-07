---
title: ASP.NET Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 7d43c66952d17a91e38ae1b086478b9416321b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web Hizmetlerini WCF'ye Taşıma
ASP.NET Web Hizmetleri gibi Hizmetleri Internet Information Services (IIS) içinde barındırmak için tesis oluşturmak için .NET Framework sınıf kitaplıkları ve araçlar sağlar. Windows Communication Foundation (WCF) .NET Framework sınıf kitaplıkları, araçları ve Web Hizmetleri tarafından kullanılan dahil olmak üzere herhangi bir protokol kullanarak iletişim kurmak için yazılım varlıkları etkinleştirme barındırma olanakları sağlar.  Geçirme ASP.NET Web hizmetlerini wcf'ye yeni özellikleri ve WCF için benzersiz geliştirmeleri avantajlarından yararlanmak, uygulamalarınızın sağlar.  
  
 WCF ASP.NET Web Hizmetleri göre birkaç önemli avantajı vardır. Yalnızca Web hizmetleri oluşturmak için ASP.NET Web Hizmetleri Araçları olmakla birlikte, WCF birbirleriyle iletişim kurmak için yazılım varlıkları yapılmalıdır zaman kullanılabilen araçlar sağlar. Bu geliştiriciler sırayla yazılım tamamlamak için geçen süre yanı sıra yazılım geliştirme kaynaklarını maliyetini azaltır farklı yazılım iletişimi senaryolara yer vermek için bilmesi için gerekli olan teknolojileri sayısını azaltır. geliştirme projelerini.  
  
 WCF Web hizmeti geliştirme projeler için bile, ASP.NET Web Hizmetleri desteği'den daha fazla Web hizmeti protokolleri destekler. Bu ek protokoller, ilgili, daha karmaşık çözümleri için sağlar diğer şeyleri, güvenilir oturumlar ve işlemler arasında.  
  
 WCF, ASP.NET Web Hizmetleri daha iletileri taşıma için daha fazla protokollerini destekler. ASP.NET Web hizmetlerini yalnızca Köprü Metni Aktarım Protokolü (HTTP) kullanarak iletileri göndermeyi destekler. WCF İletim Denetimi Protokolü (Adlandırılmış Kanallar ve Microsoft Message Queuing (MSMQ) TCP), yanı sıra, HTTP kullanarak iletileri göndermeyi destekler. Daha da önemlisi, WCF ek aktarım protokolleri desteklemek için genişletilebilir. Bu nedenle, yazılım WCF kullanılarak geliştirilen çok çeşitli olası yatırım getirisi böylece artırma diğer yazılım ile birlikte çalışmak için uyarlanabilir.  
  
 WCF dağıtımı için çok daha zengin özellikleri ve uygulamaları ASP.NET Web Hizmetleri daha yönetme sağlar. ASP.NET de vardır, yapılandırma sistemi yanı sıra WCF yapılandırma Düzenleyicisi sunar alıcıları ve aracılar, bir izleme Görüntüleyici, ileti günlüğe kaydetme, performans sayaçları, büyük bir dizi herhangi bir sayıda aracılığıyla geriye etkinlik izlemeyi gönderenlerin ve Windows Yönetim Araçları için destek.  
  
 Kullanıyorsanız veya ASP.NET Web Hizmetleri, birkaç seçeneğiniz vardır kullanarak dikkate alarak bu olası faydaları ASP.NET Web göre WCF hizmetleri, verilen:  
  
-   ASP.NET Web Hizmetleri ve WCF tarafından proffered avantajları forego devam edin.  
  
-   Gelecekte bir zamanda WCF benimsenmesi amacıyla ASP.NET Web hizmetlerini kullanmaya devam. Bu bölümdeki konular, yeni ASP.NET Web hizmeti uygulama ileride WCF uygulamaları ile birlikte kullanabilmek için için aday en üst düzeye çıkarmak açıklanmaktadır. Bu bölümdeki konular, ayrıca yeni ASP.NET Web hizmetlerini WCF'ye geçirme kolaylaştırmak amacıyla yapı açıklamaktadır. Ancak, hizmetleri güvenli hale getirme önemlidir ya da güvenilirlik veya işlem çıkışların gerekli ya da özel yönetim olanakları oluşturulması gerekecek sonra WCF benimsemek için daha iyi bir seçenektir. WCF tam olarak bu tür senaryoları için tasarlanmıştır.  
  
-   Mevcut ASP.NET Web hizmeti uygulamalarınızı sürdürmek devam ederken yeni geliştirme için WCF benimser. Bu büyük olasılıkla en iyi bir seçimdir. WCF, avantajları kullanmak için var olan uygulamaları değiştirmeyi maliyetini sparing sırasında verir. Bu senaryoda yeni WCF uygulamaları mevcut ASP.NET uygulamaları ile birlikte bulunabilir. Yeni WCF uygulamaları mevcut ASP.NET Web hizmetlerini kullanmak mümkün olacaktır ve WCF WCF ASP.NET uyumluluk modu, mevcut ASP.NET uygulamalarına yeni işlemsel özellikleri programlamak için kullanılabilir.  
  
-   WCF benimsemeye ve ASP.NET Web hizmeti uygulamalarınız için WCF geçirilir. WCF tarafından sağlanan özellikleri ile mevcut uygulamaları geliştirmek için veya mevcut bir ASP.NET Web Hizmetleri içinde yeni işlevselliği, daha güçlü WCF uygulamaları yeniden oluşturmak için bu seçeneği tercih edebilirsiniz.  
  
> [!NOTE]
>  Bir WCF Hizmeti barındırılıyorsa dikkatli'nin alınması gereken IIS tarafından 5.x ve ASP.NET kaldırılır. Bir WCF Hizmeti IIS tarafından barındırılan zaman ASP.NET kaldırılırsa 5.x, hizmet için kod istenebilir. ASP.NET IIS çalıştıran bir işletim sisteminde kaldırılması zaman 5.x ve WCF kaldırılır, .svc uzantılı bir dosya bir metin dosyası olarak kabul edilir ve tüm kaynak kodu da dahil olmak üzere içeriği, istemciye döndürülür.  
  
 Bu bölümde bu seçenekler ayrıntılı açıklanmaktadır, ASP.NET Web hizmetlerini wcf'ye karşılaştırır ve ASP.NET Web Hizmetleri kodunuz için WCF geçirmek yönergeler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Windows Communication Foundation'ı Benimseme](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
