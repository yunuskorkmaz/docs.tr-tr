---
title: .NET Framework Uygulamalarında Önbelleğe Alma
description: .NET uygulamalarında önbelleğe alma özelliğini kullanın. Verileri önbelleğe alma, ASP.NET uygulamaları veya WCF REST hizmetlerinde önbelleğe alma ve .NET 'te önbelleğe almayı genişletme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: 9b08a07e9b446c2998150a327dccdc8d0481722a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309774"
---
# <a name="caching-in-net-framework-applications"></a>.NET Framework Uygulamalarında Önbelleğe Alma
Önbelleğe alma, verileri hızlı erişim için bellekte depolamanıza olanak sağlar. Verilere yeniden erişildiğinde, uygulamalar verileri özgün kaynaktan almak yerine önbellekten alabilir. Bu, performansı ve ölçeklenebilirliği iyileştirebilir. Ayrıca, veri kaynağı geçici olarak kullanılamadığında önbelleğe alma verilerin kullanılabilir olmasını sağlar.  
  
 .NET Framework, ASP.NET dahil olmak üzere hem Windows istemci hem de sunucu uygulamalarının performansını ve ölçeklenebilirliğini artırmak için kullanabileceğiniz önbelleğe alma işlevselliği sağlar.  
  
> [!NOTE]
> .NET Framework 3,5 ve önceki sürümlerde, ASP.NET ad alanında bellek içi önbellek uygulamasını sağladı <xref:System.Web.Caching> . .NET Framework önceki sürümlerinde, önbelleğe alma yalnızca ad alanında kullanılabilir <xref:System.Web> ve bu nedenle ASP.net sınıflarında bir bağımlılık gerektirdi. .NET Framework 4 ' te, <xref:System.Runtime.Caching> ad alanı hem Web hem de Web 'e ait olmayan uygulamalar için tasarlanan API 'leri içerir.  
  
## <a name="caching-data"></a>Verileri Önbelleğe Alma  
 Ad alanındaki sınıfları kullanarak bilgileri önbelleğe alabilirsiniz <xref:System.Runtime.Caching> . Bu ad alanındaki önbelleğe alma sınıfları aşağıdaki özellikleri sağlar:  
  
- Özel önbellek uygulamaları oluşturmak için temel sağlayan soyut türler.  
  
- Somut bellek içi nesne önbelleği uygulama.  
  
 Soyut temel önbelleğe alma sınıfı ( <xref:System.Runtime.Caching.ObjectCache> ) aşağıdaki önbelleğe alma görevlerini tanımlar:  
  
- Önbellek girişleri oluşturma ve yönetme.  
  
- Süre sonu ve çıkarma bilgilerini belirtme.  
  
- Önbellek girdilerindeki değişikliklere yanıt olarak oluşturulan olayları tetikleyerek.  
  
 <xref:System.Runtime.Caching.MemoryCache>Sınıfı, sınıfının bellek içi nesne önbelleği uygulamasıdır <xref:System.Runtime.Caching.ObjectCache> . <xref:System.Runtime.Caching.MemoryCache>En çok önbelleğe alma görevleri için sınıfını kullanabilirsiniz.  
  
> [!NOTE]
> <xref:System.Runtime.Caching.MemoryCache>Sınıfı, ad alanında tanımlanan ASP.net Cache nesnesi üzerinde modellenir <xref:System.Web.Caching> . Bu nedenle, ASP.NET 'in önceki sürümlerinde sağlanmış mantığa benzer iç önbelleğe alma mantığı.  
  
 WPF uygulamasında önbelleğe alma için kullanmanın bir örneği için bkz. [Izlenecek yol: BIR WPF uygulamasında uygulama verilerini önbelleğe alma](../wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>ASP.NET uygulamalarında önbelleğe alma  
 Ad alanındaki önbelleğe alma sınıfları, <xref:System.Runtime.Caching> ASP.NET içinde verileri önbelleğe alma işlevselliği sağlar.  
  
> [!NOTE]
> Uygulamanız .NET Framework 3,5 veya önceki bir sürümü hedefliyorsa, ad alanında tanımlanan önbelleğe alma sınıflarını kullanmanız gerekir <xref:System.Web.Caching> . Daha fazla bilgi için bkz. [ASP.net Caching Overview](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
> Yeni uygulamalar geliştirirken sınıfını kullanmanızı öneririz <xref:System.Runtime.Caching.MemoryCache> . Ad alanında belirtilen API, <xref:System.Runtime.Caching> ad alanında sağlanmış olan API 'ye benzer <xref:System.Web.Caching.Cache> . Bu nedenle, ASP.NET 'in önceki sürümlerinde önbelleğe alma kullandıysanız API tanıdık gelecektir. ASP.NET uygulamalarında önbelleğe alma özelliğinin nasıl kullanılacağına ilişkin bir örnek için bkz. [Izlenecek yol: ASP.net Içindeki uygulama verilerini önbelleğe alma](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100)).  
  
### <a name="output-caching"></a>Çıktı Önbelleği  
 Uygulama verilerini el ile önbelleğe almak için, <xref:System.Runtime.Caching.MemoryCache> ASP.NET içinde sınıfını kullanabilirsiniz. ASP.NET ayrıca, bellek içinde sayfaların, denetimlerin ve HTTP yanıtlarının üretilen çıkışını depolayan çıkış önbelleğe almayı destekler. Çıktıyı önbelleğe alma işlemini bildirimli olarak bir ASP.NET Web sayfasında veya Web.config dosyadaki ayarları kullanarak yapılandırabilirsiniz. Daha fazla bilgi için bkz. [önbelleğe alma Için OutputCache öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET, özel çıkış önbelleği sağlayıcıları oluşturarak çıktı önbelleğe almayı genişletmenizi sağlar. Özel sağlayıcılar kullanarak, önbelleğe alınmış içeriği diskler, bulut depolaması ve dağıtılmış önbellek motorları gibi diğer depolama cihazlarını kullanarak saklayabilirsiniz. Özel bir çıktı önbelleği sağlayıcısı oluşturmak için, sınıfından türeten bir sınıf oluşturur <xref:System.Web.Caching.OutputCacheProvider> ve uygulamayı özel çıkış önbelleği sağlayıcısını kullanacak şekilde yapılandırırsınız.  
  
## <a name="caching-in-wcf-rest-services"></a>WCF REST hizmetlerinde önbelleğe alma  
 WCF REST Hizmetleri için .NET Framework, ASP.NET ' de bulunan bildirime dayalı çıktı önbelleği avantajlarından yararlanmanıza olanak sağlar. Bu, WCF REST hizmet işlemlerinizin yanıtlarını önbelleğe almanıza olanak sağlar. Kullanıcı, önbelleğe alma için yapılandırılmış bir hizmete HTTP GET isteği gönderdiğinde, ASP.NET önbelleğe alınmış yanıtı geri gönderir ve hizmet yöntemi çağrılmaz. Önbelleğin süresi dolduktan sonra, bir Kullanıcı bir HTTP GET isteği gönderdiğinde, hizmet yönteminiz çağrılır ve yanıt yeniden önbelleğe alınır.  
  
 .NET Framework Ayrıca Koşullu HTTP alma önbelleği uygulamanıza olanak sağlar. REST senaryolarında, hizmetler tarafından [http belirtiminde](https://www.w3.org/Protocols/rfc2616/rfc2616.html)açıklandığı gıbı akıllı http önbelleği uygulamak için genellikle kullanılan koşullu BIR http get isteği kullanılır. Daha fazla bilgi için bkz. [WCF Web HTTP Hizmetleri Için önbelleğe alma desteği](../wcf/feature-details/caching-support-for-wcf-web-http-services.md).  
  
## <a name="extending-caching-in-the-net-framework"></a>.NET Framework önbelleğe almayı genişletme  
 .NET Framework önbelleğe alma, genişletilebilir olacak şekilde tasarlanmıştır. <xref:System.Runtime.Caching.ObjectCache>Sınıfı, özel önbellek uygulamaları oluşturmanıza olanak sağlar. Bu sınıf, Windows Forms, Windows Presentation Foundation (WPF) ve Windows Communications Foundation (WCF) dahil olmak üzere tüm yönetilen uygulamalar için kullanılabilen üyeleri sağlar. Bunu, farklı bir depolama mekanizması kullanan bir önbellek sınıfı oluşturmak için veya önbellek işlemleri üzerinde ayrıntılı denetim istiyorsanız yapabilirsiniz.  
  
 Önbelleğe almayı genişletmek için şunları yapabilirsiniz:  
  
- Sınıfından türeten özel bir sınıf oluşturun <xref:System.Runtime.Caching.ObjectCache> ve ardından türetilmiş sınıfta özel bir önbellek uygulamasını sağlayın.  
  
- Sınıfından türeten bir sınıf oluşturun <xref:System.Runtime.Caching.MemoryCache> ve türetilmiş sınıfı özelleştirin veya genişletin. Bunun nasıl yapılacağı hakkında bir örnek için bkz. [bir ASP.NET uygulamasında birden çok Cache nesnesi kullanarak uygulama verilerini önbelleğe alma](https://docs.microsoft.com/archive/blogs/aspnetue/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application).  
  
- Sınıfından türeten bir sınıf oluşturun <xref:System.Web.Caching.OutputCacheProvider> ve uygulamayı özel çıkış önbelleği sağlayıcısını kullanacak şekilde yapılandırın.  
  
 Daha fazla bilgi için Scott Guthrie 'nin bloguna [ASP.NET 4 (VS 2010 ve .net 4,0 serisi) Ile Genişletilebilir çıkış önbelleği](https://weblogs.asp.net/scottgu/extensible-output-caching-with-asp-net-4-vs-2010-and-net-4-0-series) girişi bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](../wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [İzlenecek yol: ASP.NET içinde uygulama verilerini önbelleğe alma](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
