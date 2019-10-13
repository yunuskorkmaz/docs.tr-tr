---
title: WPF uygulaması dağıtma (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: daa69997f70c22a97482fd7e63d42506e7051732
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291289"
---
# <a name="deploying-a-wpf-application-wpf"></a>WPF uygulaması dağıtma (WPF)
Windows Presentation Foundation (WPF) uygulamaları derlendikten sonra, dağıtılması gerekir. Windows ve .NET Framework çeşitli dağıtım teknolojileri içerir. @No__t-0 uygulaması dağıtmak için kullanılan dağıtım teknolojisi, uygulama türüne bağlıdır. Bu konu, her dağıtım teknolojisine kısa bir genel bakış ve her bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama türünün dağıtım gereksinimleriyle birlikte nasıl kullanıldıklarından daha fazla bilgi sağlamaktadır.  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Dağıtım Teknolojileri  
 Windows ve .NET Framework aşağıdakiler dahil olmak üzere çeşitli dağıtım teknolojileri içerir:  
  
- XCopy dağıtımı.  
  
- [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] dağıtımı.  
  
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
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], uygulamaların kolayca istemcilere dağıtılabilecek ve çalıştırılabilen, kendi içinde bulunan yürütülebilir dosyalar olarak paketlenebilmesini sağlar. Ayrıca, [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] Windows ile yüklenir ve Masaüstü, Başlat menüsü ve programlar Denetim Masası ile tümleştirme imkanı sunar.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], uygulamaları yüklemeyi ve kaldırmayı basitleştirir, ancak yüklü uygulamaların sürüm açısından güncel tutulduğundan emin olmak için tesis sağlamaz.  
  
 Windows Installer hakkında daha fazla bilgi için bkz. [Windows Installer Deployment](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce dağıtımı  
 ClickOnce, Web olmayan uygulamalar için Web stili uygulama dağıtımına izin vermez. Uygulamalar Web veya dosya sunucularına yayımlanır ve buradan dağıtılır. ClickOnce, -0 tarafından yüklenen uygulamaların yaptığı @no__t istemci özelliklerinin tam aralığını desteklememesine karşın, aşağıdakileri içeren bir alt kümeyi destekler:  
  
- Başlat menüsü ve programlar Denetim Masası ile tümleştirme.  
  
- Sürüm oluşturma, geri alma ve kaldırma.  
  
- Dağıtım konumundan her zaman bir uygulama başlatan çevrimiçi kurulum modu.  
  
- Yeni sürümler yayınlandığında otomatik güncelleştirme.  
  
- Dosya uzantılarının kaydı.  
  
 ClickOnce hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>WPF uygulamalarını dağıtma  
 @No__t-0 uygulaması için dağıtım seçenekleri uygulamanın türüne bağlıdır. @No__t-0 ' dan bir dağıtım perspektifinden, üç önemli uygulama türü vardır:  
  
- Tek başına uygulamalar.  
  
- Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamaları.  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Tek başına uygulamaları dağıtma  
 Tek başına uygulamalar ClickOnce veya [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] kullanılarak dağıtılır. Her iki durumda da, tek başına uygulamalar çalıştırmak için tam güven gerektirir. @No__t-0 kullanılarak dağıtılan tek başına uygulamalara tam güven otomatik olarak verilir. ClickOnce kullanılarak dağıtılan tek başına uygulamalara otomatik olarak tam güven verilmez. Bunun yerine, ClickOnce, kullanıcıların tek başına bir uygulama yüklenmeden önce kabul etmeleri gereken bir güvenlik uyarısı iletişim kutusu görüntüler. Kabul edilirse, tek başına uygulama yüklenir ve tam güven verilir. Aksi takdirde, tek başına uygulama yüklenmez.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Yalnızca biçimlendirme XAML uygulamalarını dağıtma  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa genellikle HTML sayfaları gibi Web sunucularına yayımlanır ve Internet Explorer kullanılarak görüntülenebilir. Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa, Internet bölgesi izin kümesi tarafından tanımlanan kısıtlamalarla kısmi güvenli güvenlik korumalı alanı içinde çalışır. Bu, HTML tabanlı Web uygulamalarına eşdeğer bir güvenlik korumalı alanı sağlar.  
  
 @No__t-0 uygulamalarının güvenliği hakkında daha fazla bilgi için bkz. [güvenlik](../security-wpf.md).  
  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa XCopy veya [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] kullanılarak yerel dosya sistemine yüklenebilir. Bu sayfalar, Internet Explorer veya Windows Gezgini kullanılarak görüntülenebilir.  
  
 XAML hakkında daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>XAML tarayıcı uygulamaları dağıtma  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], aşağıdaki üç dosyanın dağıtılmasını gerektiren derlenmiş uygulamalardır:  
  
- *ApplicationName*. exe: yürütülebilir derleme uygulama dosyası.  
  
- *ApplicationName*. xbap: dağıtım bildirimi.  
  
- *ApplicationName*. exe. manifest: uygulama bildirimi.  
  
> [!NOTE]
> Dağıtım ve uygulama bildirimleri hakkında daha fazla bilgi için bkz. [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md).  
  
 Bu dosyalar [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] yapılandırıldığında üretilir. Daha fazla bilgi için bkz. [nasıl yapılır: yenı WPF tarayıcı uygulaması projesi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları gibi [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] genellikle bir Web sunucusuna yayımlanır ve Internet Explorer kullanılarak görüntülenir.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], dağıtım tekniklerinden herhangi biri kullanılarak istemcilere dağıtılabilir. Ancak, aşağıdaki özellikleri sağladığından ClickOnce önerilir:  
  
1. Yeni bir sürüm yayımlandığında otomatik güncelleştirmeler.  
  
2. Tam güvenle çalışan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] için yükseltme ayrıcalıkları.  
  
 Varsayılan olarak, ClickOnce uygulama dosyalarını. deploy uzantısıyla yayımlar. Bu sorunlu olabilir, ancak devre dışı bırakılabilir. Daha fazla bilgi için bkz. [ClickOnce dağıtımlarında sunucu ve Istemci Yapılandırma sorunları](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 @No__t dağıtma hakkında daha fazla bilgi için bkz. [WPF XAML tarayıcı uygulamalarına genel bakış](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>.NET Framework yükleme  
 @No__t-0 uygulamasını çalıştırmak için, Microsoft .NET Framework 'Ün istemcide yüklü olması gerekir. Internet Explorer, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarayıcı tarafından barındırılan uygulamalar görüntülenirken .NET Framework istemcilerin yüklü olup olmadığını otomatik olarak algılar. .NET Framework yüklü değilse, Internet Explorer kullanıcılardan yüklemeyi ister.  
  
 .NET Framework yüklenip yüklenmediğini algılamak için, Internet Explorer aşağıdaki uzantılara sahip içerik dosyaları için geri dönüş çok amaçlı Internet posta uzantıları (MIME) işleyicisi olarak kaydedilmiş bir önyükleyici uygulaması içerir:. xaml,. XPS,. xbap , ve. Application. Bu dosya türlerine gittiğinizde .NET Framework istemcide yüklü değilse, önyükleyici uygulamanın bu uygulamayı yükleme izni ister. İzin sağlanmazsa, ne .NET Framework ne de uygulama yüklenmez.  
  
 İzin verildiğinde, Internet Explorer Microsoft Arka Plan Akıllı Aktarım Hizmeti (BITS) kullanarak .NET Framework indirir ve yükler. .NET Framework başarıyla yüklendikten sonra, özgün olarak istenen dosya yeni bir tarayıcı penceresinde açılır.  
  
 Daha fazla bilgi için bkz. [.NET Framework ve uygulamaları dağıtma](../../deployment/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF uygulaması oluşturma](building-a-wpf-application-wpf.md)
- [Güvenlik](../security-wpf.md)
