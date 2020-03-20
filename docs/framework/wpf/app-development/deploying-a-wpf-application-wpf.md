---
title: Uygulamayı dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186319"
---
# <a name="deploy-a-wpf-application"></a>WPF Uygulamasını Dağıtma

Windows Presentation Foundation (WPF) uygulamaları kurulduktan sonra dağıtılması gerekir. Windows ve .NET Framework birkaç dağıtım teknolojileri içerir. WPF uygulamasını dağıtmak için kullanılan dağıtım teknolojisi uygulama türüne bağlıdır. Bu konu, her dağıtım teknolojisine ve bunların her WPF uygulama türünün dağıtım gereksinimleriyle birlikte nasıl kullanıldığına kısa bir genel bakış sağlar.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Dağıtım Teknolojileri  
 Windows ve .NET Framework, aşağıdakiler dahil olmak üzere çeşitli dağıtım teknolojilerini içerir:  
  
- XCopy dağıtımı.  
  
- Windows Yükleyici dağıtımı.  
  
- ClickOnce dağıtım.  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>XCopy Dağıtım  
 XCopy dağıtımı, dosyaları bir konumdan diğerine kopyalamak için XCopy komut satırı programının kullanılması anlamına gelir. XCopy dağıtımı aşağıdaki koşullar altında uygundur:  
  
- Uygulama kendi kendine yeten. Çalıştırmak için istemciyi güncelleştirmek gerekmez.  
  
- Uygulama dosyaları, yapı konumundan (yerel disk, UNC dosya paylaşımı vb.) yayımlama konumuna (Web sitesi, UNC dosya paylaşımı vb.) gibi bir konumdan diğerine taşınmalıdır.  
  
- Uygulama kabuk tümleştirme (Başlat menüsü kısayolu, masaüstü simgesi vb. gerektirmez).  
  
 XCopy basit dağıtım senaryoları için uygun olsa da, daha karmaşık dağıtım yetenekleri gerektiğinde sınırlıdır. Özellikle, XCopy'i kullanmak genellikle dağıtımı sağlam bir şekilde yönetmek için komut dosyaları oluşturmak, yürütmek ve korumak için ek yükü oluşturur. Ayrıca, XCopy sürüm, yükleme yi veya geri alma desteklemez.  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows Installer  
 Windows Installer, uygulamaların istemcilere kolayca dağıtılabilen ve çalıştırılabilen bağımsız yürütülebilir uygulamalar olarak paketlenmesini sağlar. Ayrıca, Windows Installer Windows ile yüklenir ve masaüstü, Başlat menüsü ve Programlar denetim paneli ile tümleştirme sağlar.  
  
 Windows Installer, uygulamaların yüklenmesini ve yüklenmemesini kolaylaştırır, ancak yüklenen uygulamaların sürüm açısından güncel tutulmasını sağlamak için olanaklar sağlamaz.  
  
 Windows Yükleyici hakkında daha fazla bilgi için [Windows Yükleyici Dağıtımı'na](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)bakın.
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>ClickOnce Dağıtım  
 ClickOnce, Web olmayan uygulamalar için Web stili uygulama dağıtımına olanak tanır. Uygulamalar Web veya dosya sunucularına yayınlanır ve dağıtılır. ClickOnce, Windows Installer yüklü uygulamaların yaptığı tüm istemci özelliklerini desteklemese de, aşağıdakileri içeren bir alt kümeyi destekler:  
  
- Başlat menüsü ve Programlar denetim paneli ile entegrasyon.  
  
- Sürüm, geri alma ve yüklemeyi kaldırma.  
  
- Her zaman dağıtım konumundan bir uygulama başlatan çevrimiçi yükleme modu.  
  
- Yeni sürümler yayımlandığında otomatik güncelleme.  
  
- Dosya uzantılarının kaydı.  
  
 ClickOnce hakkında daha fazla bilgi için [ClickOnce Güvenlik ve Dağıtım'a](/visualstudio/deployment/clickonce-security-and-deployment)bakın.  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>WPF Uygulamalarını Dağıtma  
 WPF uygulaması için dağıtım seçenekleri uygulama türüne bağlıdır. Dağıtım açısından bakıldığında, WPF'nin üç önemli uygulama türü vardır:  
  
- Bağımsız uygulamalar.  
  
- Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamaları.  
  
- XAML tarayıcı uygulamaları (XBAPs).  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Bağımsız Uygulamaların Dağıtılması  
 Bağımsız uygulamalar ClickOnce veya Windows Installer kullanılarak dağıtılır. Her iki durumda da, bağımsız uygulamalar çalıştırmak için tam güven gerektirir. Windows Installer kullanılarak dağıtılan bağımsız uygulamalara otomatik olarak tam güven verilir. ClickOnce kullanılarak dağıtılan bağımsız uygulamalara otomatik olarak tam güven verilmez. Bunun yerine ClickOnce, tek başına bir uygulama yüklenmeden önce kullanıcıların kabul etmesi gereken bir güvenlik uyarısı iletişim kutusu görüntüler. Kabul edilirse, bağımsız uygulama yüklenir ve tam güven verilir. Değilse, bağımsız uygulama yüklenmez.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Yalnızca Biçimlendirme XAML Uygulamalarını Dağıtma  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları genellikle HTML sayfaları gibi Web sunucularına yayınlanır ve Internet Explorer kullanılarak görüntülenebilir. Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları, Internet bölgesi izin kümesi tarafından tanımlanan kısıtlamalarla kısmi güven güvenlik kum havuzu içinde çalışır. Bu, HTML tabanlı Web uygulamalarına eşdeğer bir güvenlik alanı sağlar.  
  
 WPF uygulamaları için güvenlik hakkında daha fazla bilgi için [Güvenlik'e](../security-wpf.md)bakın.  
  
 Yalnızca biçimlendirme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfaları XCopy veya Windows Installer kullanılarak yerel dosya sistemine yüklenebilir. Bu sayfalar Internet Explorer veya Windows Explorer kullanılarak görüntülenebilir.  
  
 XAML hakkında daha fazla bilgi için Bkz. [XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>XAML Tarayıcı Uygulamalarını Dağıtma  
 XBAP'lar, aşağıdaki üç dosyanın dağıtılmasını gerektiren derlenmiş uygulamalardır:  
  
- *ApplicationName*.exe: Yürütülebilir montaj başvuru dosyası.  
  
- *ApplicationName*.xbap: Dağıtım bildirimi.  
  
- *ApplicationName*.exe.manifest: Uygulama bildirimi.  
  
> [!NOTE]
> Dağıtım ve uygulama bildirimleri hakkında daha fazla bilgi için [wpf uygulaması oluşturma](building-a-wpf-application-wpf.md)bilgisine bakın.  
  
 Bu dosyalar bir XBAP oluşturulunca oluşturulur. Daha fazla bilgi için [bkz: Yeni bir WPF Tarayıcı Uygulama Projesi oluşturun.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)) Yalnızca [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme sayfaları gibi, XBAP'lar da genellikle bir Web sunucusunda yayımlanır ve Internet Explorer kullanılarak görüntülenir.  
  
 XBAP'lar dağıtım tekniklerinden herhangi birini kullanarak istemcilere dağıtılabilir. Ancak, clickonce aşağıdaki özellikleri sağladığından önerilir:  
  
1. Yeni bir sürüm yayımlandığında otomatik güncelleştirmeler.  
  
2. Tam güvenle çalışan XBAP için yükseklik ayrıcalıkları.  
  
 Varsayılan olarak ClickOnce,.deploy uzantılı uygulama dosyalarını yayımlar. Bu sorunlu olabilir, ancak devre dışı olabilir. Daha fazla bilgi için [ClickOnce Dağıtımlarında Sunucu ve İstemci Yapılandırma Sorunları'na](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)bakın.  
  
 XAML tarayıcı uygulamalarını (XBAP' lar) dağıtma hakkında daha fazla bilgi için [WPF XAML Tarayıcı Uygulamalarına Genel Bakış'a](wpf-xaml-browser-applications-overview.md)bakın.  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>.NET Framework2ü yükleme  
 WPF uygulamasını çalıştırmak için istemciye Microsoft .NET Framework'ün yüklenmesi gerekir. Internet Explorer, WPF tarayıcı tarafından barındırılan uygulamalar görüntülendiğinde istemcilerin .NET Framework ile yüklü olup olmadığını otomatik olarak algılar. .NET Framework yüklenmezse, Internet Explorer kullanıcıları yüklemelerini ister.  
  
 .NET Framework yüklü olup olmadığını algılamak için, Internet Explorer aşağıdaki uzantıları ile içerik dosyaları için geri dönüş Çok Amaçlı Internet Posta Uzantıları (MIME) işleyicisi olarak kayıtlı bir bootstrapper uygulaması içerir: .xaml, .xps, .xbap ve .application. Bu dosya türlerine gidin ve .NET Framework istemciye yüklenmezse, bootstrapper uygulaması yükleme izni ister. İzin verilmezse, ne .NET Framework ne de uygulama yüklenir.  
  
 İzin verilirse, Internet Explorer Microsoft Arka Plan Akıllı Aktarım Hizmeti 'ni (BITS) kullanarak .NET Framework'ü karşıdan yükler ve yükler. .NET Framework'ün başarılı bir şekilde yüklenmesinden sonra, ilk istenen dosya yeni bir tarayıcı penceresinde açılır.  
  
 Daha fazla bilgi için [bkz.](../../deployment/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Derleme](building-a-wpf-application-wpf.md)
- [Güvenlik](../security-wpf.md)
