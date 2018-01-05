---
title: "ASP.NET Web Hizmetlerini WCF'ye Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f90f7dd508e2ff4058b787fc29d152abc18f24fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web Hizmetlerini WCF'ye Taşıma
ASP.NET Web Hizmetleri gibi Hizmetleri Internet Information Services (IIS) içinde barındırmak için tesis oluşturmak için .NET Framework sınıf kitaplıkları ve araçlar sağlar. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].NET Framework sınıf kitaplıkları, araçları ve Web Hizmetleri tarafından kullanılan dahil olmak üzere herhangi bir protokol kullanarak iletişim kurmak için yazılım varlıkları etkinleştirme barındırma olanakları sağlar.  Geçirme ASP.NET Web Hizmetleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeni özellikleri ve özgü geliştirmeleri avantajlarından yararlanmak, uygulamaların sağlayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET Web Hizmetleri göre birkaç önemli avantajı vardır. ASP.NET Web Hizmetleri Araçları yalnızca Web hizmetleri oluşturmak için durumdayken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] birbirleriyle iletişim kurmak için yazılım varlıkları yapılmalıdır zaman kullanılabilen araçlar sağlar. Bu geliştiriciler sırayla yazılım tamamlamak için geçen süre yanı sıra yazılım geliştirme kaynaklarını maliyetini azaltır farklı yazılım iletişimi senaryolara yer vermek için bilmesi için gerekli olan teknolojileri sayısını azaltır. geliştirme projelerini.  
  
 Web hizmeti geliştirme projeleri için bile [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler destek ASP.NET Web Hizmetleri daha hizmeti protokolleri diğer Web. Bu ek protokoller, ilgili, daha karmaşık çözümleri için sağlar diğer şeyleri, güvenilir oturumlar ve işlemler arasında.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET Web Hizmetleri daha iletileri taşıma için daha fazla protokollerini destekler. ASP.NET Web hizmetlerini yalnızca Köprü Metni Aktarım Protokolü (HTTP) kullanarak iletileri göndermeyi destekler. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]İletim Denetimi Protokolü (Adlandırılmış Kanallar ve Microsoft Message Queuing (MSMQ) TCP), yanı sıra, HTTP kullanarak iletileri göndermeyi destekler. Daha da önemlisi, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ek aktarım protokolleri desteklemek için genişletilebilir. Bu nedenle, geliştirilmiş yazılımlar kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çok çeşitli böylece yatırım dönüş olası artırma diğer yazılım ile birlikte çalışmak için uyarlanabilir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uygulamaları dağıtma ve ASP.NET Web hizmetleri sağladığından daha yönetme için çok daha zengin özellikleri sağlar. ASP.NET de sahip bir yapılandırma sistemi yanı sıra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma Düzenleyicisi sunar alıcıları ve aracılar, bir izleme Görüntüleyici, ileti günlüğe kaydetme, performans büyük bir dizi herhangi bir sayıda aracılığıyla geri göndericilerden gelen Etkinlik izleme sayaçlar ve Windows Yönetim Araçları için destek.  
  
 Bu olası faydaları verilen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET Web Hizmetleri göre kullanıyorsanız veya ASP.NET Web hizmetlerini kullanarak dikkate alarak, birkaç seçeneğiniz vardır:  
  
-   ASP.NET Web Hizmetleri kullanmaya ve tarafından proffered avantajları forego devam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Uygulamasını kullanma amacıyla ASP.NET Web hizmetlerini kullanmaya devam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelecekte bir zamanda. Bu bölümdeki konular, yeni ASP.NET Web hizmeti uygulama gelecekteki birlikte kullanabilmek için için aday en üst düzeye çıkarmak açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar. Bu bölümdeki konular, ayrıca yeni ASP.NET Web Hizmetleri için bunları kolaylaştırmak amacıyla nasıl oluşturulacağını açıklayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ancak, hizmetleri güvenli hale getirme önemli ya da güvenilirlik veya işlem çıkışların gerekli ise ya da özel yönetim olanakları olmasını oluşturulması sonra benimsemek için daha iyi bir seçenektir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tam olarak bu tür senaryoları için tasarlanmıştır.  
  
-   Benimsemeyi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mevcut ASP.NET Web hizmeti uygulamalarınızı sürdürmek devam ederken yeni geliştirme. Bu büyük olasılıkla en iyi bir seçimdir. Avantajları verir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], kullanmak için var olan uygulamaları değiştirmeyi maliyetini sparing oluştu. Bu senaryoda, yeni [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları mevcut ASP.NET uygulamaları ile birlikte bulunabilir. Yeni [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları mevcut ASP.NET Web hizmetlerini kullanmak mümkün olacaktır ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeni işlemsel özellikleri tarafından virtue, varolan ASP.NET uygulamalarına programlamak için kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda.  
  
-   Benimsemeyi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET Web hizmeti uygulamalarınız için geçiş [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Tarafından sağlanan özellikleri ile mevcut uygulamaları geliştirmek için bu seçeneği tercih edebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], veya işlevselliğini mevcut ASP.NET Web Hizmetleri içinde yeni, daha güçlü oluşturmaya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
> [!NOTE]
>  Durumunda dikkatli'nin alınması gereken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet barındırılır IIS tarafından 5.x ve ASP.NET kaldırılır. Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti IIS tarafından barındırılan ASP.NET kaldırılırsa 5.x, hizmet için kod istenebilir. ASP.NET IIS çalıştıran bir işletim sisteminde kaldırılması zaman 5.x ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olduğu kaldırılırken .svc uzantılı bir dosya bir metin dosyası olarak kabul edilir ve tüm kaynak kodu da dahil olmak üzere içeriği, istemciye döndürülür.  
  
 Bu bölümde bu seçenekler ayrıntılı açıklar, ASP.NET Web Hizmetleri için karşılaştırır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET Web Hizmetleri kodunuzu geçirmek yönergeler sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Windows Communication Foundation'ı Benimseme](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
