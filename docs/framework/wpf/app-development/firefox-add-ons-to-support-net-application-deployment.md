---
title: .NET Uygulaması Dağıtımını Destekleyen Firefox Eklentileri
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: f05f5afa0c0a7ef858442bd98233865834b8b89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547449"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET Uygulaması Dağıtımını Destekleyen Firefox Eklentileri
Windows Presentation Foundation (WPF) Firefox ve .NET Framework Yardımcısı Firefox için eklenti etkinleştirmek [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve Mozilla Firefox tarayıcı ile çalışmak için ClickOnce uygulamaları.  
  
## <a name="wpf-plug-in-for-firefox"></a>WPF Firefox eklentisi  
 Firefox WPF eklentisinin etkinleştirir [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için dosyaları için gittiğinizde ve üst düzey veya HTML IFRAME Firefox tarayıcıda çalışacak. Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] olan bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir Web sunucusuna yayımlanması ve içinde başlatılan uygulama Desteklenen tarayıcılar. Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için gittiğinizde ve bir XML dosyası gibi desteklenen tarayıcılar görüntülenen yalnızca XAML bir dosyasıdır.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox yüklü olduğu için eklenti [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Windows 7 içeren [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], yer almaz ancak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox için eklenti. Yükleme yapamayacağınızı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox Windows 7 için eklenti.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] İçermemesi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox için eklenti. Bununla birlikte, her iki [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] olan yüklü, Firefox WPF eklentisinin ile yüklenen [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Bu nedenle [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] uygulamaları WPF konağı framework'ün doğru sürümünü yükleyecektir olduğundan hala çalışır. Daha fazla bilgi için bkz: [WPF Konağı (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>Firefox için .NET Framework Assistant  
 .NET Framework Yardımcısı Firefox için Firefox tarayıcıdan çalıştırmak tek başına ClickOnce uygulamalarını sağlar. .NET Framework Assistant aynı önce ve sonra Firefox tarayıcısı yüklendiğinde Firefox işlevler için. Firefox tarayıcısı başlatıldığı zaman ve [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] olan yüklü, Firefox bulur ve Firefox için .NET Framework Yardımcısı'nı yükler. Kullanıcılar .NET Framework Yardımcısı'nı aşağıdakileri yapmak Firefox için yapılandırabilirsiniz:  
  
-   ClickOnce uygulamasını çalıştırmadan önce sizden onay.  
  
-   .NET Framework'ün yüklü tüm sürümlerini ya da yalnızca en son sürümünü bildirin.  
  
 .NET Framework için Yardımcısı Firefox dahil olan [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Firefox için .NET Framework Yardımcısı'nı kaldırma hakkında daha fazla bilgi için bkz: [Firefox için .NET Framework Yardımcısı'nı kaldırmak nasıl](http://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulaması Dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
