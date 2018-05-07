---
title: .NET Framework Uygulamalarında Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
author: tdykstra
ms.openlocfilehash: dd96caa03d04371d4f930bb311decd7672b342fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="caching-in-net-framework-applications"></a>.NET Framework Uygulamalarında Önbelleğe Alma
Önbelleğe alma, verileri hızlı erişim için bellekte depolamanızı sağlar. Verileri yeniden erişildiğinde uygulamaları özgün kaynağından veri almak yerine önbellekten veri alabilirsiniz. Bu, performans ve ölçeklenebilirlik iyileştirebilir. Ayrıca, veri kaynağı geçici olarak devre dışı olduğunda kullanılabilir hale getirir verileri önbelleğe alma.  
  
 .NET Framework performansı ve ASP.NET gibi her iki Windows istemci ve sunucu uygulamaları, ölçeklenebilirliğini artırmak için kullanabileceğiniz önbelleğe alma işlevselliği sağlar.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve önceki sürümleri, ASP.NET sağlanan bir bellek içi önbellek uygulamasında <xref:System.Web.Caching> ad alanı. Önceki sürümlerinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], önbelleğe alma yalnızca kullanılabilir <xref:System.Web> ad alanı ve bu nedenle, bir bağımlılığı ASP.NET sınıfları gerekir. .NET Framework 4'te <xref:System.Runtime.Caching> ad alanı, hem Web hem de Web olmayan uygulamalar için tasarlanan API'ları içerir.  
  
## <a name="caching-data"></a>Verileri Önbelleğe Alma  
 Sınıflarda kullanarak bilgi önbelleğe alabilir <xref:System.Runtime.Caching> ad alanı. Bu ad alanındaki önbelleğe alma sınıflar aşağıdaki özellikleri sağlar:  
  
-   Özel önbellek uygulamaları oluşturmak için temel sağlayan soyut türler.  
  
-   Somut bellekteki nesne önbelleği uygulaması.  
  
 Soyut taban sınıfı önbelleğe alma (<xref:System.Runtime.Caching.ObjectCache>) aşağıdaki önbelleğe alma görevlerini tanımlar:  
  
-   Oluşturma ve önbellek girişlerinin yönetme.  
  
-   Geçerlilik süresi ve çıkarma bilgilerini belirtme.  
  
-   Önbellek girişlerinin değişikliklere yanıt olarak gerçekleştirilen tetikleme olaylar.  
  
 <xref:System.Runtime.Caching.MemoryCache> Sınıftır bellekteki nesne önbelleği uygulaması <xref:System.Runtime.Caching.ObjectCache> sınıfı. Kullanabileceğiniz <xref:System.Runtime.Caching.MemoryCache> önbelleğe alma görevlerinin çoğu için sınıf.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> Tanımlanan ASP.NET önbellek nesnesi üzerinde sınıf Modellenen <xref:System.Web.Caching> ad alanı. Bu nedenle, iç önbelleğe alma mantığını ASP.NET önceki sürümlerinde sağlanan mantığı benzer.  
  
 Bir WPF uygulamasında önbelleğe alma için kullanma örneği için bkz: [izlenecek yol: bir WPF uygulamasında uygulama veri önbelleğe alma](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>ASP.NET uygulamalarında önbelleğe alma  
 Önbelleğe alma sınıfları <xref:System.Runtime.Caching> ad alanı verileri ASP.NET önbelleğe alma için işlevsellik sağlar.  
  
> [!NOTE]
>  Varsa, uygulama hedeflerine [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ya da daha önce tanımlanan önbelleğe alma sınıfları kullanması gerekir <xref:System.Web.Caching> ad alanı. Daha fazla bilgi için bkz: [ASP.NET önbelleğe alma genel bakış](http://msdn.microsoft.com/library/5ec28012-4972-4dc3-b3e8-9d20401fe11d).  
  
> [!NOTE]
>  Yeni uygulamaları geliştirirken kullanmanız önerilir <xref:System.Runtime.Caching.MemoryCache> sınıfı. Sağlanan API <xref:System.Runtime.Caching> ad alanı içinde sağlanan API benzer <xref:System.Web.Caching.Cache> ad alanı. Bu nedenle, API ASP.NET önceki sürümlerinin önbelleğe alınmasını kullandıysanız tanıdık gelecektir. ASP.NET uygulamalarında önbelleğe almayı kullanmak üzere nasıl bir örnek için bkz: [izlenecek yol: uygulama veri önbelleğe alma ASP.NET](http://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23).  
  
### <a name="output-caching"></a>Çıktı önbelleği  
 Önbellek uygulama verileri için el ile kullandığınız <xref:System.Runtime.Caching.MemoryCache> ASP.NET sınıfta. ASP.NET ayrıca çıktı önbelleği, sayfalar, denetimleri ve HTTP yanıtlarını oluşturulan çıktısını bellekte depolayan destekler. Bir ASP.NET Web sayfası veya Web.config dosyasında ayarlarını kullanarak bildirimli olarak çıktı önbelleği yapılandırabilirsiniz. Daha fazla bilgi için bkz: [(ASP.NET Ayarlar Şeması) önbelleğe alma için outputCache Ögesi](http://msdn.microsoft.com/library/47cd2b47-316f-4dfd-bbf8-539be3066fee).  
  
 ASP.NET çıktı önbelleğine sağlayıcılar oluşturarak çıktı önbelleği genişletmenizi sağlar. Özel sağlayıcılar kullanarak, diskleri, bulut depolama ve dağıtılmış önbellek motorları gibi diğer depolama aygıtlarını kullanarak önbelleğe alınmış içeriği depolayabilirsiniz. Özel çıkış önbelleği sağlayıcısı oluşturmak için türeyen bir sınıf oluşturun. <xref:System.Web.Caching.OutputCacheProvider> sınıfı ve uygulamayı özel çıkış önbelleği sağlayıcısı kullanacak şekilde yapılandırın.  
  
## <a name="caching-in-wcf-rest-services"></a>WCF REST Hizmetleri'nde önbelleğe alma  
 WCF REST Hizmetleri için .NET Framework, ASP.NET kullanılabilir olan, bildirim temelli çıktı önbelleği yararlanmak sağlar. Bu, önbelleği yanıtlarını WCF REST hizmeti işlemlerinden sağlar. Bir kullanıcı önbelleğe alma işlemi için yapılandırılmış bir hizmet için bir HTTP GET isteği gönderdiğinde, ASP.NET önbelleğe alınmış bir yanıtı geri gönderir ve hizmet yöntemi çağrılmaz. Bir kullanıcı bir HTTP GET isteği gönderir başlatıldığında önbellek, süresi dolduktan sonra hizmeti yöntemi olarak adlandırılır ve yanıt tekrar önbelleğe alınır.  
  
 .NET Framework HTTP GET koşullu önbelleğe alma uygulamak sağlar. REST senaryolarda koşullu bir HTTP GET isteği genellikle Hizmetleri tarafından akıllı HTTP önbelleğe alma açıklandığı gibi uygulamak için kullanılan [HTTP belirtimi](http://go.microsoft.com/fwlink/?LinkId=165800). Daha fazla bilgi için bkz: [WCF Web HTTP Hizmetleri için önbelleğe alma desteği](http://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>.NET Framework önbelleğe alma genişletme  
 .NET Framework önbelleğe alma, Genişletilebilir olmak üzere tasarlanmıştır. <xref:System.Runtime.Caching.ObjectCache> Sınıfı bir özel önbellek uygulaması oluşturmanıza olanak sağlar. Bu sınıf Windows Formları, Windows Presentation Foundation (WPF) ve Windows Communications Foundation (WCF) dahil olmak üzere tüm yönetilen uygulamalar için kullanılabilir üyeler sağlar. Farklı depolama mekanizmasını kullanan bir önbellek sınıfı oluşturmak için bunu yapabilirsiniz veya önbellek işlemleri üzerinde ayrıntılı denetim istiyorsanız.  
  
 Önbelleğe alma genişletmek için aşağıdakileri yapabilirsiniz:  
  
-   Türetilen özel bir sınıf oluşturun <xref:System.Runtime.Caching.ObjectCache> sınıf ve türetilen sınıf özel önbellek uygulamasında sağlayın.  
  
-   Türeyen bir sınıf oluşturun <xref:System.Runtime.Caching.MemoryCache> sınıfı ve özelleştirebilir veya türetilmiş sınıfını genişletir. Bunun nasıl yapılacağı örneği için bkz: [kullanarak birden fazla önbellek nesneleri bir ASP.NET uygulamasında tarafından uygulama verileri önbelleğe alma](http://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Türeyen bir sınıf oluşturun <xref:System.Web.Caching.OutputCacheProvider> sınıfı ve uygulamayı özel çıkış önbelleği sağlayıcısı kullanacak şekilde yapılandırın.  
  
 Daha fazla bilgi için bkz: Giriş [Genişletilebilir çıktı önbelleği, ASP.NET 4 (VS 2010 ve .NET 4.0 serisi)](http://go.microsoft.com/fwlink/?LinkId=185772) Scott Guthrie'nın blogunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching.MemoryCache>  
 [İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)  
 [İzlenecek yol: Uygulama verileri ASP.NET önbelleğe alma](http://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23)
