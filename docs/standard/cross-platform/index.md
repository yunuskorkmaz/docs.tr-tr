---
title: .NET Framework ile Birden Çok Platform için Geliştirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 92ed36d632aefbb566bedd87ddf6a2100807aac6
ms.sourcegitcommit: 68b60d38043e50104ccc90c76f8599b1ffe18346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2018
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>.NET Framework ile Birden Çok Platform için Geliştirme
.NET Framework ve Visual Studio kullanarak, hem Microsoft hem de Microsoft olmayan platformlar için uygulamaları geliştirebilirsiniz.  
  
## <a name="options-for-cross-platform-development"></a>Platformlar arası geliştirme için seçenekleri  
 Birden çok platform için geliştirmek için kaynak kodu veya ikili dosyaları paylaşabilir ve .NET Framework kod ve Windows çalışma zamanı API'ları arasındaki aramaları yapabilir.  
  
|İsterseniz...|Kullanım...|  
|-----------------------|------------|  
|Kaynak kodu Windows Phone 8.1 ve Windows 8.1 uygulamalar arasında paylaşma|**Paylaşılan projeleri** (Visual Studio 2013, güncelleştirme 2 şablonunda Evrensel uygulamaları).<br /><br /> -Şu anda Visual Basic desteği yok.<br /># Kullanarak-platforma özgü kodu ayırabilirsiniz`if` deyimleri.<br /><br /> Ayrıntılar için bkz:<br /><br /> -   [Visual Studio kullanarak hedef Windows ve Windows Phone uygulamaları oluşturma](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (MSDN makalesi)<br />-   [Evrensel XAML uygulamaları oluşturmak için Visual Studio kullanarak](https://blogs.msdn.microsoft.com/visualstudio/2014/04/14/using-visual-studio-to-build-universal-xaml-apps/) (blog yayını)<br />-   [XAML Yakınsanan uygulamaları oluşturmak için Visual Studio kullanarak](https://channel9.msdn.com/Events/Build/2014/3-591) (video)|  
|Farklı platformlarda hedef uygulamalar arasında ikili dosyaları paylaşma|**Taşınabilir Sınıf Kitaplığı projelerinde** platform belirsiz kodu.<br /><br /> -Bu yaklaşım, genellikle iş mantığını uygular kodu için kullanılır.<br />-Visual Basic veya C# kullanabilirsiniz.<br />-API desteği, platforma göre değişir.<br />-Windows 8.1 ve Windows Phone 8.1 hedefleyen taşınabilir Sınıf Kitaplığı projelerinde Windows çalışma zamanı API'ları ve XAML destekler. Bu özellikler taşınabilir sınıf kitaplığı eski sürümlerinde kullanılamaz.<br />-Gerekli olursa, arabirimleri veya soyut sınıflar kullanarak platforma özgü kodu soyut.<br /><br /> Ayrıntılar için bkz:<br /><br /> -   [Taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)<br />-   [Sizin için taşınabilir sınıf kitaplıkları iş yapmak için nasıl](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/) (blog yayını)<br />-   [MVVM ile taşınabilir sınıf kitaplığı kullanma](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md) <br />-   [Birden çok platformu hedefleyen kitaplıklar için uygulama kaynakları](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.NET taşınabilirlik Çözümleyicisi](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) (Visual Studio uzantısı)|  
|Kaynak kodu Windows 8.1 dışındaki platformları için uygulamaları ve Windows Phone 8.1 arasında paylaşma|**Bağlantı olarak Ekle** özelliği.<br /><br /> -Bu yaklaşım, hem uygulamalar için ortak ancak değil taşınabilir bir nedenden dolayı uygulama mantığı için uygundur. C# veya Visual Basic kodu için bu özelliği kullanabilirsiniz.<br />     Örneğin, Windows Phone 8 ve Windows 8, Windows çalışma zamanı API'leri paylaşmak, ancak bu platformlar için taşınabilir sınıf kitaplıkları Windows çalışma zamanı desteklemez. Kullanabileceğiniz `Add as link` ortak Windows çalışma zamanı kodun bir Windows Phone 8 uygulaması Windows 8'i hedefleyen bir Windows mağazası uygulama arasında paylaşmak için.<br /><br /> Ayrıntılar için bkz:<br /><br /> -   [Bağlantı olarak Ekle kod paylaşmak](http://msdn.microsoft.com/library/windowsphone/develop/jj714082\(v=vs.105\).aspx) (MSDN makalesi)<br />-   [Nasıl yapılır: Varolan öğeleri için bir proje eklemek](http://msdn.microsoft.com/library/vstudio/9f4t9t92\(v=vs.100\).aspx) (MSDN makalesi)|  
|Windows mağazası uygulamaları .NET Framework kullanılarak yazma veya .NET Framework kodundan Windows çalışma zamanı API'larını çağırma|**Windows çalışma zamanı API'leri** .NET Framework C# veya Visual Basic kodu ve Windows mağazası uygulamaları oluşturmak için .NET Framework'ü kullanın. İki Platform arasında API farklılıkları haberdar olmanız gerekir. Ancak, bu farklılıkları ile çalışmanıza yardımcı sınıfları vardır.<br /><br /> Ayrıntılar için bkz:<br /><br /> -   [Windows mağazası uygulamaları ve Windows çalışma zamanı için .NET framework desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md) <br />-   [Windows çalışma zamanı için bir URI geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md) <br />-   <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> [`System.IO.WindowsRuntimeStreamExtensions`](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx) (MSDN API başvuru sayfası)<br />-   <!--zz <xref:System.WindowsRuntimeSystemExtensions>--> [`System.WindowsRuntimeSystemExtensions`](https://msdn.microsoft.com/library/system.windowsruntimesystemextensions(v=vs.110).aspx) (MSDN API başvuru sayfası)|  
|Microsoft dışı platformlar için .NET Framework uygulamalar oluşturma|**Taşınabilir sınıf kitaplığı başvuru derlemeleri** .NET Framework ve Visual Studio uzantısı veya üçüncü taraf aracı Xamarin gibi.<br /><br /> Ayrıntılar için bkz:<br /><br /> -   [Taşınabilir sınıf kitaplığı tüm platformlarda artık kullanılabilir.](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx) (blog yayını)<br />-   [Xamarin belgeleri](/xamarin)|  
|Platformlar arası geliştirme için JavaScript ve HTML kullanın|**Evrensel uygulama şablonları** Visual Studio 2013'te güncelleştirme Windows 8.1 ve Windows Phone 8.1 için Windows çalışma zamanı API'leri karşı geliştirmek için 2. Şu anda, JavaScript ve HTML .NET Framework API'leri ile platformlar arası uygulamalar geliştirmek için kullanamazsınız.<br /><br /> Ayrıntılar için bkz:<br /><br /> -   [JavaScript proje şablonları](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx)<br />-   [Windows çalışma zamanı uygulamasını Windows Phone için JavaScript kullanarak bağlantı noktası oluşturma](http://msdn.microsoft.com/library/windows/apps/dn636144.aspx)|
