---
title: Bir WPF Uygulamasını Dağıtma (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 924553bf457a6668143785c78871ebac6e01efa4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68818033"
---
# <a name="deploying-a-wpf-application-wpf"></a>Bir WPF Uygulamasını Dağıtma (WPF)
Windows Presentation Foundation (WPF) uygulamaları derlendikten sonra, dağıtılması gerekir. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].NET Framework birçok dağıtım teknolojilerini içerir. Bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamayı dağıtmak için kullanılan dağıtım teknolojisi, uygulama türüne bağlıdır. Bu konuda her dağıtım teknolojisine ve bunların her [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir uygulama türünün dağıtım gereksinimleriyle birlikte nasıl kullanıldığı hakkında kısa bir genel bakış sunulmaktadır.  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Dağıtım Teknolojileri  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].NET Framework aşağıdakiler de dahil olmak üzere çeşitli dağıtım teknolojileri içerir:  
  
- XCopy dağıtımı.  
  
- [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]dağıtmak.  
  
- ClickOnce dağıtımı.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy dağıtımı  
 XCopy dağıtımı, dosyaları bir konumdan diğerine kopyalamak için XCopy komut satırı programının kullanımına başvurur. XCopy dağıtımı aşağıdaki koşullarda uygundur:  
  
- Uygulama kendi kendine dahil değildir. Çalıştırması için istemcisini güncelleştirmesi gerekmez.  
  
- Uygulama dosyaları bir konumdan diğerine (bir derleme konumundan (yerel disk, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] dosya paylaşımından vb.) bir yayımlama konumuna (Web sitesi, [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] dosya paylaşımında vb.) taşınmalıdır.  
  
- Uygulama kabuk tümleştirmesi gerektirmez (Başlat Menüsü Kısayolu, masaüstü simgesi vb.).  
  
 XCopy basit dağıtım senaryolarında uygun olsa da, daha karmaşık dağıtım özellikleri gerektiğinde sınırlandırılır. Özellikle, XCopy kullanılması genellikle dağıtımı kolay bir şekilde yönetmek için betikleri oluşturma, yürütme ve sürdürme yükünü doğurur. Ayrıca, XCopy sürümü oluşturma, kaldırma veya geri alma 'yı desteklemez.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]uygulamaların, kolayca istemcilere dağıtılabilecek ve çalıştırılabilen, kendi içinde bulunan yürütülebilir dosyalar olarak paketlenebilmesini sağlar. Ayrıca, [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] ile birlikte [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yüklenir ve Masaüstü, Başlat menüsü ve programlar Denetim Masası ile tümleştirme sunar.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]uygulamaları yüklemeyi ve kaldırmayı basitleştirir, ancak yüklü uygulamaların sürüm açısından güncel tutulduğundan emin olmak için tesis sağlamaz.  
  
 Windows Installer hakkında daha fazla bilgi için bkz. [Windows Installer Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 ClickOnce, Web olmayan uygulamalar için Web stili uygulama dağıtımına izin vermez. Uygulamalar Web veya dosya sunucularına yayımlanır ve buradan dağıtılır. ClickOnce, yüklenen uygulamaların tüm istemci özelliklerini [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]desteklememesine karşın, aşağıdakileri içeren bir alt kümeyi destekler:  
  
- Başlat menüsü ve programlar Denetim Masası ile tümleştirme.  
  
- Sürüm oluşturma, geri alma ve kaldırma.  
  
- Dağıtım konumundan her zaman bir uygulama başlatan çevrimiçi kurulum modu.  
  
- Yeni sürümler yayınlandığında otomatik güncelleştirme.  
  
- Dosya uzantılarının kaydı.  
  
 ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>WPF uygulamalarını dağıtma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Uygulamanın dağıtım seçenekleri uygulamanın türüne bağlıdır. Dağıtım perspektifinden [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] üç önemli uygulama türü vardır:  
  
- Tek başına uygulamalar.  
  
- Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme uygulamaları.  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Tek başına uygulamaları dağıtma  
 Tek başına uygulamalar ClickOnce veya [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]kullanılarak dağıtılır. Her iki durumda da, tek başına uygulamalar çalıştırmak için tam güven gerektirir. Kullanılarak [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]dağıtılan tek başına uygulamalara tam güven otomatik olarak verilir. ClickOnce kullanılarak dağıtılan tek başına uygulamalara otomatik olarak tam güven verilmez. Bunun yerine, ClickOnce, kullanıcıların tek başına bir uygulama yüklenmeden önce kabul etmeleri gereken bir güvenlik uyarısı iletişim kutusu görüntüler. Kabul edilirse, tek başına uygulama yüklenir ve tam güven verilir. Aksi takdirde, tek başına uygulama yüklenmez.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Yalnızca biçimlendirme XAML uygulamalarını dağıtma  
 Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sayfaları genellikle HTML sayfaları gibi Web sunucularına yayımlanır ve Internet Explorer kullanılarak görüntülenebilir. Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sayfaları, Internet bölgesi izin kümesi tarafından tanımlanan kısıtlamalarla kısmi güvenli güvenlik korumalı alanı içinde çalışır. Bu, HTML tabanlı Web uygulamalarına eşdeğer bir güvenlik korumalı alanı sağlar.  
  
 Uygulamalar için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] güvenlik hakkında daha fazla bilgi için bkz. [güvenlik](../security-wpf.md).  
  
 Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sayfaları, xcopy veya [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]kullanılarak yerel dosya sistemine yüklenebilir. Bu sayfalar, Internet Explorer veya Windows Gezgini kullanılarak görüntülenebilir.  
  
 XAML hakkında daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>XAML tarayıcı uygulamaları dağıtma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], aşağıdaki üç dosyanın dağıtılmasını gerektiren derlenmiş uygulamalardır:  
  
- *ApplicationName*. exe: Yürütülebilir derleme uygulama dosyası.  
  
- *ApplicationName*. xbap: Dağıtım bildirimi.  
  
- *ApplicationName*. exe. manifest: Uygulama bildirimi.  
  
> [!NOTE]
>  Dağıtım ve uygulama bildirimleri hakkında daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).  
  
 Bu dosyalar yapılandırıldığında üretilir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] . Daha fazla bilgi için [nasıl yapılır: Yeni bir WPF tarayıcı uygulaması projesi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))oluşturun. Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sayfaları gibi, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] genellikle bir Web sunucusuna yayımlanır ve Internet Explorer kullanılarak görüntülenir.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], herhangi bir dağıtım tekniği kullanılarak istemcilere dağıtılabilir. Ancak, aşağıdaki özellikleri sağladığından ClickOnce önerilir:  
  
1. Yeni bir sürüm yayımlandığında otomatik güncelleştirmeler.  
  
2. Tam güvenle [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] çalışan için ayrıcalık yükseltme.  
  
 Varsayılan olarak, ClickOnce uygulama dosyalarını. deploy uzantısıyla yayımlar. Bu sorunlu olabilir, ancak devre dışı bırakılabilir. Daha fazla bilgi için bkz. [ClickOnce dağıtımlarında sunucu ve Istemci Yapılandırma sorunları](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Dağıtma [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>.NET Framework2ü yükleme  
 Bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamayı çalıştırmak için Microsoft .NET Framework 'ün istemcide yüklü olması gerekir. Internet Explorer, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarayıcıda barındırılan uygulamalar görüntülenirken istemcilerin .NET Framework yüklenip yüklenmediğini otomatik olarak algılar. .NET Framework yüklü değilse, Internet Explorer kullanıcılardan yüklemeyi ister.  
  
 .NET Framework yüklenip yüklenmediğini algılamak için, Internet Explorer aşağıdaki uzantılara sahip içerik dosyaları için geri dönüş [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] işleyicisi olarak kaydedilmiş bir önyükleyici uygulaması içerir:. xaml,. XPS,. xbap ve. Application. Bu dosya türlerine gittiğinizde .NET Framework istemcide yüklü değilse, önyükleyici uygulamanın bu uygulamayı yükleme izni ister. İzin sağlanmazsa, ne .NET Framework ne de uygulama yüklenmez.  
  
 İzin verildiğinde, Internet Explorer Microsoft Arka Plan Akıllı Aktarım Hizmeti (BITS) kullanarak .NET Framework indirir ve yükler. .NET Framework başarıyla yüklendikten sonra, özgün olarak istenen dosya yeni bir tarayıcı penceresinde açılır.  
  
 Daha fazla bilgi için bkz. [.NET Framework ve uygulamaları dağıtma](../../deployment/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Derleme](building-a-wpf-application-wpf.md)
- [Güvenlik](../security-wpf.md)
