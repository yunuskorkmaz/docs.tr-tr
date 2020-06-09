---
title: ASP.NET Web Hizmetlerini WCF'ye Taşıma
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: fa707a4246d5bc9940417072c098b2973140f878
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598807"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web Hizmetlerini WCF'ye Taşıma
ASP.NET, Web hizmetleri oluşturmaya yönelik .NET Framework sınıf kitaplıkları ve araçları ve Internet Information Services (IIS) içinde barındırma hizmetleri olanakları sağlar. Windows Communication Foundation (WCF), Web Hizmetleri tarafından kullanılanlar da dahil olmak üzere, yazılım varlıklarının herhangi bir protokol kullanarak iletişim kurmasını sağlamak için .NET Framework sınıf kitaplıkları, Araçlar ve barındırma olanakları sağlar.  ASP.NET Web hizmetlerini WCF 'ye geçirmek, uygulamalarınızın WCF 'ye özgü yeni özelliklerden ve geliştirmelerden yararlanmasını sağlar.  
  
 WCF, ASP.NET Web hizmetlerine göre birçok önemli avantaj sunar. ASP.NET Web Hizmetleri Araçları yalnızca Web hizmetleri oluşturmaya yönelik olmakla birlikte, WCF, yazılım varlıklarının birbirleriyle iletişim kurmak için yapılması gerektiğinde kullanılabilecek araçlar sağlar. Bu, geliştiricilerin farklı yazılım iletişim senaryolarına uyum sağlamak için bilmesi gereken teknolojilerin sayısını azaltır ve bu da yazılım geliştirme kaynaklarının maliyetinin yanı sıra yazılım geliştirme projelerinin tamamlanma süresini azaltır.  
  
 WCF, Web hizmeti geliştirme projeleri için bile ASP.NET Web Hizmetleri desteğinden daha fazla Web hizmeti protokolünü destekler. Bu ek protokoller, diğer şeyler, güvenilir oturumlar ve işlemler arasında, ilgili daha karmaşık çözümler sunar.  
  
 WCF, ASP.NET Web hizmetlerinden daha fazla ileti aktarmak için daha fazla protokol destekler. ASP.NET Web Hizmetleri yalnızca Köprü Metni Aktarım Protokolü (HTTP) kullanarak ileti göndermeyi destekler. WCF, HTTP ve Iletim Denetimi Protokolü (TCP), adlandırılmış kanallar ve Microsoft Message Queuing (MSMQ) ile ileti göndermeyi destekler. Daha önemli olan WCF, ek aktarım protokollerini desteklemek için genişletilebilir. Bu nedenle, WCF kullanılarak geliştirilen yazılım daha fazla başka yazılımlarla birlikte çalışarak, yatırımdaki olası dönüşü artırır.  
  
 WCF, ASP.NET Web Services tarafından sağlanan uygulamaları dağıtmak ve yönetmek için çok daha zengin olanaklar sunar. ASP.NET de sahip olduğu bir yapılandırma sistemine ek olarak, WCF bir yapılandırma Düzenleyicisi, gönderenlerden gelen etkinlik izleme ve herhangi bir sayıda aracı, bir izleme Görüntüleyicisi, ileti günlüğü, çok sayıda performans sayacı ve Windows Yönetim Araçları desteği sunar.  
  
 Bu olası WCF avantajları, ASP.NET Web hizmetlerine göre, kullanıyorsanız veya ASP.NET Web hizmetlerini kullanmayı düşünüyorsanız, birkaç seçeneğiniz vardır:  
  
- ASP.NET Web Hizmetleri 'ni kullanmaya devam edin ve WCF tarafından temin edilecek avantajları kullanın.  
  
- Daha sonraki bir zamanda WCF 'yi benimseme amacıyla ASP.NET Web Hizmetleri 'ni kullanmaya devam edin. Bu bölümdeki konularda, yeni ASP.NET Web hizmeti uygulamalarını gelecek WCF uygulamalarıyla birlikte kullanabilmek için adayların nasıl en üst düzeye çıkarması açıklanmaktadır. Bu bölümdeki konular Ayrıca yeni ASP.NET Web Hizmetleri oluşturmayı, bu sayede bunları WCF 'ye geçirmeyi kolaylaştırmak için açıklar. Ancak, hizmetlerin güvenliğini sağlamak önemliyse veya güvenilirlik ya da işlem kesintileri gerekliyse veya özel yönetim tesislerinin oluşturulması gerekiyorsa, WCF 'yi benimsemeniz daha iyi bir seçenektir. WCF, tam olarak bu senaryolar için tasarlanmıştır.  
  
- Yeni geliştirme için WCF 'yi benimseyin, mevcut ASP.NET Web hizmeti uygulamalarınızı sürdürmek için devam edin. Bu seçenek büyük olasılıkla en iyi seçenektir. Bu, WCF 'nin avantajlarını verir, Sparing, var olan uygulamaları kullanmak için değiştirme maliyetlidir. Bu senaryoda, yeni WCF uygulamaları mevcut ASP.NET uygulamalarıyla birlikte bulunabilir. Yeni WCF uygulamaları var olan ASP.NET Web hizmetlerini kullanabiliyor ve WCF, WCF ASP.NET uyumluluk modunun sanallaştırılmasına göre mevcut ASP.NET uygulamalarına yeni işletimsel özellikleri programlamak için kullanılabilir.  
  
- WCF 'yi benimseyin ve var olan ASP.NET Web hizmeti uygulamalarını WCF 'ye geçirin. WCF tarafından sunulan özelliklerle mevcut uygulamaları geliştirmek veya mevcut ASP.NET Web Hizmetleri 'nin işlevlerini yeni, daha güçlü WCF uygulamaları içinde yeniden oluşturmak için bu seçeneği belirleyebilirsiniz.  
  
> [!NOTE]
> WCF hizmeti IIS 5. x ve ASP.NET tarafından barındırılıyorsa, dikkatli olunmalıdır. Bir WCF hizmeti IIS 5. x tarafından barındırılıyorsa, ASP.NET kaldırılırsa hizmetin kodu istenebilir. IIS 5. x ve WCF çalıştıran bir işletim sisteminde ASP.NET kaldırıldığında,. svc uzantılı bir dosya bir metin dosyası olarak kabul edilir ve kaynak kod dahil olmak üzere içerik istek sahibine döndürülür.  
  
 Bu bölümde bu seçenekler ayrıntılı olarak açıklanmıştır, ASP.NET Web Hizmetleri WCF ile karşılaştırılır ve ASP.NET Web Hizmetleri kodunuzu WCF 'ye geçirme hakkında yönergeler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma](anticipating-adopting-wcf-migration.md)
- [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](anticipating-adopting-the-wcf-easing-future-integration.md)
- [Windows Communication Foundation'ı Benimseme](adopting-wcf.md)
- [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma](comparing-aspnet-web-services-to-wcf-based-on-development.md)
