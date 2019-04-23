---
title: .NET Framework Uygulamalarında Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: a57489af2f2af59f128f5d86be844b43c9c49840
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085786"
---
# <a name="caching-in-net-framework-applications"></a>.NET Framework Uygulamalarında Önbelleğe Alma
Önbelleğe alma, verileri hızlı erişim için bellekte depolamanızı sağlar. Verileri yeniden erişildiğinde uygulamaları özgün kaynaktan almak yerine önbellekten veri alabilirsiniz. Bu, performansı ve ölçeklenebilirliği artırabilir. Ayrıca, önbelleğe alma, veri kaynağının geçici olarak devre dışı olduğunda yaptığı veri yok.  
  
 .NET Framework, ASP.NET dahil olmak üzere iki Windows istemci ve sunucu uygulamaları, ölçeklenebilirliğini ve performansı artırmak için kullanabileceğiniz önbelleğe alma işlevselliği sağlar.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ve önceki sürümleri, ASP.NET bir bellek içi önbelleği uygulamasında sağlanan <xref:System.Web.Caching> ad alanı. Önceki sürümlerinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], önbelleğe yalnızca <xref:System.Web> ad alanı ve bu nedenle ASP.NET sınıfları bir bağımlılık gerekli. .NET Framework 4'te <xref:System.Runtime.Caching> ad alanı, hem Web hem de olmayan Web uygulamaları için tasarlanmış API'ler içerir.  
  
## <a name="caching-data"></a>Verileri Önbelleğe Alma  
 Sınıflarını kullanarak bilgileri önbelleğe alabilir <xref:System.Runtime.Caching> ad alanı. Bu ad alanındaki önbelleğe alma sınıflar aşağıdaki özellikleri sağlar:  
  
-   Özel önbellek uygulamaları oluşturmak için temel sağlayan soyut türler.  
  
-   Bir somut bellekteki nesne önbelleği uygulaması.  
  
 Soyut temel sınıf önbelleğe alma (<xref:System.Runtime.Caching.ObjectCache>) aşağıdaki önbelleğe alma görevlerini tanımlar:  
  
-   Oluşturma ve önbellek girişlerinin yönetme.  
  
-   Sona erme ve çıkarma bilgilerini belirtme.  
  
-   Önbellek girişlerinin değişikliklere yanıt olarak harekete geçirilen olayları tetikleme.  
  
 <xref:System.Runtime.Caching.MemoryCache> Sınıfı, bellekteki nesne önbelleği uygulaması <xref:System.Runtime.Caching.ObjectCache> sınıfı. Kullanabileceğiniz <xref:System.Runtime.Caching.MemoryCache> önbelleğe alma görevlerin çoğu için sınıf.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> Sınıf üzerinde tanımlanan ASP.NET önbellek nesnesini modellenmiş <xref:System.Web.Caching> ad alanı. Bu nedenle, iç önbelleğe alma mantığını ASP.NET'in önceki sürümlerinde sağlanan mantıksal benzer.  
  
 Bir WPF uygulamasında önbelleğe alma için kullanılacak ilişkin bir örnek için bkz. [izlenecek yol: Bir WPF uygulamasında uygulama verilerini önbelleğe alma](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>ASP.NET uygulamalarında önbelleğe alma  
 Önbelleğe almayı yer alan sınıfları <xref:System.Runtime.Caching> ad alanı, ASP.NET'te verileri önbelleğe alma için işlevselliği sağlar.  
  
> [!NOTE]
>  Uygulama hedeflerinizi [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ya da daha önce tanımlanan önbelleğe alma sınıfları kullanmalısınız <xref:System.Web.Caching> ad alanı. Daha fazla bilgi için [ASP.NET önbelleğe alma genel bakış](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
>  Yeni uygulamalar geliştirirken kullanmanızı öneririz <xref:System.Runtime.Caching.MemoryCache> sınıfı. Sağlanan API <xref:System.Runtime.Caching> ad alanı gibi sağlanan API <xref:System.Web.Caching.Cache> ad alanı. Bu nedenle, API, ASP.NET'in önceki sürümlerinde önbelleğe alma kullandıysanız tanıdık gelecektir. ASP.NET uygulamalarında önbelleğe almayı kullanmak üzere nasıl bir örnek için bkz [izlenecek yol: ASP.NET'te uygulama verilerini önbelleğe alma](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100)).  
  
### <a name="output-caching"></a>Çıktı önbelleği  
 Önbellek uygulama verileri için el ile kullandığınız <xref:System.Runtime.Caching.MemoryCache> ASP.NET'te sınıfı. ASP.NET ayrıca çıkış önbelleğe alma, bellekte oluşturulan çıktı sayfalar, denetimleri ve HTTP yanıtlarını depoladığı destekler. Bir ASP.NET Web sayfası veya Web.config dosyasındaki ayarları kullanarak bildirimli olarak çıktı önbelleği yapılandırabilirsiniz. Daha fazla bilgi için [(ASP.NET Settings Schema) önbelleğe alma için öğe outputCache](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET, özel çıkış önbelleği sağlayıcılar oluşturarak çıktı önbelleği genişletmenizi sağlar. Özel sağlayıcılar kullanarak diskleri, bulut depolama ve dağıtılmış önbellek altyapısı gibi diğer depolama cihazlarına kullanarak önbelleğe alınmış içerikleri depolayabilirsiniz. Özel çıkış önbelleği sağlayıcısı oluşturmak için türetilen bir sınıf oluşturun. <xref:System.Web.Caching.OutputCacheProvider> sınıfı ve uygulamayı özel çıktı önbelleği sağlayıcısı kullanacak şekilde yapılandırın.  
  
## <a name="caching-in-wcf-rest-services"></a>WCF REST Hizmetleri'nde önbelleğe alma  
 WCF REST Hizmetleri için .NET Framework, ASP.NET'te kullanılabilen bildirim temelli çıktı önbelleği avantajlarından yararlanmak sağlar. Bu, önbellek yanıtları WCF REST hizmet işlemlerinizi sağlar. Bir kullanıcı, önbelleğe alma işlemi için yapılandırılmış bir hizmet için bir HTTP GET isteği gönderdiğinde, ASP.NET, önbelleğe alınan yanıtı geri gönderir ve hizmet yöntemi çağrılmadı. Bir kullanıcı bir HTTP GET isteği gönderir. bir sonraki açışınızda önbellek, süresi dolduktan sonra hizmet yöntemi çağrılır ve yanıt tekrar önbelleğe alınır.  
  
 .NET Framework, HTTP GET koşullu önbelleğe alma uygulamanızı sağlar. Diğer senaryolarda, koşullu bir HTTP GET isteği genellikle Hizmetleri tarafından HTTP akıllı önbellek açıklandığı gibi uygulamak için kullanılan [HTTP belirtimini](https://go.microsoft.com/fwlink/?LinkId=165800). Daha fazla bilgi için [WCF Web HTTP Hizmetleri için önbelleğe alma desteği](https://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>.NET Framework'teki önbelleğe alma genişletme  
 .NET Framework'teki önbelleğe alma, Genişletilebilir olmak üzere tasarlanmıştır. <xref:System.Runtime.Caching.ObjectCache> Sınıfı özel önbellek uygulaması oluşturmanıza olanak sağlar. Bu sınıf Windows Formları, Windows Presentation Foundation (WPF) ve Windows Communications Foundation (WCF) dahil olmak üzere tüm yönetilen uygulamalar için kullanılabilir olan üyeleri sağlar. Bir farklı depolama mekanizmasını kullanan bir önbellek sınıfı oluşturmak için bunu yapabilirsiniz veya önbellek işlemleri üzerinde ayrıntılı denetim istiyorsanız.  
  
 Önbelleğe alma genişletmek için aşağıdakileri yapabilirsiniz:  
  
-   Öğesinden türetilen özel bir sınıf oluşturmak <xref:System.Runtime.Caching.ObjectCache> sınıf ve türetilen sınıfın özel önbellek uygulamasında belirtin.  
  
-   Türetilen bir sınıf oluşturmanız <xref:System.Runtime.Caching.MemoryCache> sınıfı ve özelleştirme veya türetilmiş sınıf genişletin. Bunu yapmak nasıl bir örnek için bkz [birden fazla önbellek nesneleri kullanarak bir ASP.NET uygulamasında uygulama verilerini önbelleğe alma](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Türetilen bir sınıf oluşturmanız <xref:System.Web.Caching.OutputCacheProvider> sınıfı ve uygulamayı özel çıktı önbelleği sağlayıcısı kullanacak şekilde yapılandırın.  
  
 Daha fazla bilgi için bkz: Giriş [ASP.NET 4 (VS 2010 ve .NET 4.0 serisi) ile Genişletilebilir çıktı önbelleği](https://go.microsoft.com/fwlink/?LinkId=185772) Scott Guthrie'nin blogundan.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [İzlenecek yol: Bir WPF uygulamasında uygulama verilerini önbelleğe alma](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [İzlenecek yol: ASP.NET'te uygulama verilerini önbelleğe alma](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))
