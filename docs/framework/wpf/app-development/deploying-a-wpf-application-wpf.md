---
title: Bir WPF Uygulamasını Dağıtma (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: a1441f0cc3a7ac715a173be12e68c055ce36ff00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460140"
---
# <a name="deploying-a-wpf-application-wpf"></a>Bir WPF Uygulamasını Dağıtma (WPF)
Windows Presentation Foundation (WPF) uygulamaları derlendikten sonra, dağıtılması gerekir. Windows ve .NET Framework çeşitli dağıtım teknolojileri içerir. Bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamasını dağıtmak için kullanılan dağıtım teknolojisi, uygulama türüne bağlıdır. Bu konuda her dağıtım teknolojisine ve bunların her bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama türünün dağıtım gereksinimleriyle birlikte nasıl kullanıldığı hakkında kısa bir genel bakış sunulmaktadır.  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Dağıtım Teknolojileri  
 Windows ve .NET Framework aşağıdakiler dahil olmak üzere çeşitli dağıtım teknolojileri içerir:  
  
- XCopy dağıtımı.  
  
- Windows Installer dağıtımı.  
  
- ClickOnce dağıtımı.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy dağıtımı  
 XCopy dağıtımı, dosyaları bir konumdan diğerine kopyalamak için XCopy komut satırı programının kullanımına başvurur. XCopy dağıtımı aşağıdaki koşullarda uygundur:  
  
- Uygulama kendi kendine dahil değildir. Çalıştırması için istemcisini güncelleştirmesi gerekmez.  
  
- Uygulama dosyaları bir konumdan diğerine (örneğin, bir derleme konumundan (yerel disk, UNC dosya paylaşımından vb.) bir yayımlama konumuna (Web sitesi, UNC dosya paylaşımında vb.) taşınmalıdır.  
  
- Uygulama kabuk tümleştirmesi gerektirmez (Başlat Menüsü Kısayolu, masaüstü simgesi vb.).  
  
 XCopy basit dağıtım senaryolarında uygun olsa da, daha karmaşık dağıtım özellikleri gerektiğinde sınırlandırılır. Özellikle, XCopy kullanılması genellikle dağıtımı kolay bir şekilde yönetmek için betikleri oluşturma, yürütme ve sürdürme yükünü doğurur. Ayrıca, XCopy sürümü oluşturma, kaldırma veya geri alma 'yı desteklemez.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 Windows Installer, uygulamaların kolayca istemcilere dağıtılabilecek ve çalıştırılabilen, kendi içinde bulunan yürütülebilir dosyalar olarak paketlenebilmesini sağlar. Ayrıca, Windows Installer Windows ile yüklenir ve Masaüstü, Başlat menüsü ve programlar Denetim Masası ile tümleştirmeyi mümkün bir şekilde sunar.  
  
 Windows Installer, uygulamaları yüklemeyi ve kaldırmayı basitleştirir, ancak yüklü uygulamaların sürüm oluşturma açısından güncel kalmasını sağlamak için tesis sağlamaz.  
  
 Windows Installer hakkında daha fazla bilgi için bkz. [Windows Installer Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 ClickOnce, Web olmayan uygulamalar için Web stili uygulama dağıtımına izin vermez. Uygulamalar Web veya dosya sunucularına yayımlanır ve buradan dağıtılır. ClickOnce, Windows Installer yüklü uygulamaların yaptığı istemci özelliklerinin tam aralığını desteklememesine karşın, aşağıdakileri içeren bir alt kümeyi destekler:  
  
- Başlat menüsü ve programlar Denetim Masası ile tümleştirme.  
  
- Sürüm oluşturma, geri alma ve kaldırma.  
  
- Dağıtım konumundan her zaman bir uygulama başlatan çevrimiçi kurulum modu.  
  
- Yeni sürümler yayınlandığında otomatik güncelleştirme.  
  
- Dosya uzantılarının kaydı.  
  
 ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>WPF uygulamalarını dağıtma  
 Bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulaması için dağıtım seçenekleri, uygulamanın türüne bağlıdır. Dağıtım perspektifinden [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] üç önemli uygulama türüne sahiptir:  
  
- Tek başına uygulamalar.  
  
- Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamalar.  
  
- XAML tarayıcı uygulamaları (XBAP 'ler).  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Tek başına uygulamaları dağıtma  
 Tek başına uygulamalar ClickOnce veya Windows Installer kullanılarak dağıtılır. Her iki durumda da, tek başına uygulamalar çalıştırmak için tam güven gerektirir. Windows Installer kullanılarak dağıtılan tek başına uygulamalara tam güven otomatik olarak verilir. ClickOnce kullanılarak dağıtılan tek başına uygulamalara otomatik olarak tam güven verilmez. Bunun yerine, ClickOnce, kullanıcıların tek başına bir uygulama yüklenmeden önce kabul etmeleri gereken bir güvenlik uyarısı iletişim kutusu görüntüler. Kabul edilirse, tek başına uygulama yüklenir ve tam güven verilir. Aksi takdirde, tek başına uygulama yüklenmez.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Yalnızca biçimlendirme XAML uygulamalarını dağıtma  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları genellikle HTML sayfaları gibi Web sunucularına yayımlanır ve Internet Explorer kullanılarak görüntülenebilir. Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalar, Internet bölgesi izin kümesi tarafından tanımlanan kısıtlamalarla kısmi güven güvenlik korumalı alanı içinde çalışır. Bu, HTML tabanlı Web uygulamalarına eşdeğer bir güvenlik korumalı alanı sağlar.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarına yönelik güvenlik hakkında daha fazla bilgi için bkz. [güvenlik](../security-wpf.md).  
  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalar yerel dosya sistemine XCopy veya Windows Installer kullanılarak yüklenebilir. Bu sayfalar, Internet Explorer veya Windows Gezgini kullanılarak görüntülenebilir.  
  
 XAML hakkında daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>XAML tarayıcı uygulamaları dağıtma  
 XBAP 'ler, aşağıdaki üç dosyanın dağıtılmasını gerektiren derlenmiş uygulamalardır:  
  
- *ApplicationName*. exe: yürütülebilir derleme uygulama dosyası.  
  
- *ApplicationName*. xbap: dağıtım bildirimi.  
  
- *ApplicationName*. exe. manifest: uygulama bildirimi.  
  
> [!NOTE]
> Dağıtım ve uygulama bildirimleri hakkında daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).  
  
 Bu dosyalar bir XBAP yapılandırıldığında üretilir. Daha fazla bilgi için bkz. [nasıl yapılır: yenı WPF tarayıcı uygulaması projesi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalar gibi, XBAP 'ler genellikle bir Web sunucusuna yayımlanır ve Internet Explorer kullanılarak görüntülenir.  
  
 XBAP 'ler, dağıtım tekniklerinden herhangi biri kullanılarak istemcilere dağıtılabilir. Ancak, aşağıdaki özellikleri sağladığından ClickOnce önerilir:  
  
1. Yeni bir sürüm yayımlandığında otomatik güncelleştirmeler.  
  
2. Tam güvenle çalışan XBAP için yükseltme ayrıcalıkları.  
  
 Varsayılan olarak, ClickOnce uygulama dosyalarını. deploy uzantısıyla yayımlar. Bu sorunlu olabilir, ancak devre dışı bırakılabilir. Daha fazla bilgi için bkz. [ClickOnce dağıtımlarında sunucu ve Istemci Yapılandırma sorunları](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 XAML tarayıcı uygulamaları (XBAP) dağıtımı hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>.NET Framework2ü yükleme  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamasını çalıştırmak için, Microsoft .NET Framework 'Ün istemcide yüklü olması gerekir. Internet Explorer, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda barındırılan uygulamalar görüntülenirken istemcilerin .NET Framework yüklenip yüklenmediğini otomatik olarak algılar. .NET Framework yüklü değilse, Internet Explorer kullanıcılardan yüklemeyi ister.  
  
 .NET Framework yüklenip yüklenmediğini algılamak için, Internet Explorer aşağıdaki uzantılara sahip içerik dosyaları için geri dönüş çok amaçlı Internet posta uzantıları (MIME) işleyicisi olarak kaydedilmiş bir önyükleyici uygulaması içerir:. xaml,. XPS,. xbap , ve. Application. Bu dosya türlerine gittiğinizde .NET Framework istemcide yüklü değilse, önyükleyici uygulamanın bu uygulamayı yükleme izni ister. İzin sağlanmazsa, ne .NET Framework ne de uygulama yüklenmez.  
  
 İzin verildiğinde, Internet Explorer Microsoft Arka Plan Akıllı Aktarım Hizmeti (BITS) kullanarak .NET Framework indirir ve yükler. .NET Framework başarıyla yüklendikten sonra, özgün olarak istenen dosya yeni bir tarayıcı penceresinde açılır.  
  
 Daha fazla bilgi için bkz. [.NET Framework ve uygulamaları dağıtma](../../deployment/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Derleme](building-a-wpf-application-wpf.md)
- [Security](../security-wpf.md)
