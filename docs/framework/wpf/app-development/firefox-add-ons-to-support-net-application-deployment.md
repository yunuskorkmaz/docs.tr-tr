---
title: .NET Uygulaması Dağıtımını Destekleyen Firefox Eklentileri
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: e8f6947a0fe39998d9dc229ad7b95bfd2d426f6c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391413"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET Uygulaması Dağıtımını Destekleyen Firefox Eklentileri
Windows Presentation Foundation (WPF) Firefox ve .NET Framework Assistant Firefox için eklenti etkinleştirme [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve Mozilla Firefox tarayıcısı ile çalışmak için ClickOnce uygulamaları.  
  
## <a name="wpf-plug-in-for-firefox"></a>Firefox WPF eklentisinin  
 Firefox WPF eklentisinin sağlayan [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları için gittiğinizde ve üst düzey veya HTML IFRAME Firefox tarayıcısı'nı çalıştırın. Bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] olduğu bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir Web sunucusuna yayımlanması ve içinde başlatılan uygulama tarayıcılar desteklenir. Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için gittiğinizde ve bir XML dosyası gibi desteklenen tarayıcılar görüntülenen yalnızca XAML dosyası.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox ile yüklü eklenti [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Windows 7 içerir [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], yer almaz ancak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox için eklenti. Yükleyemezsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Windows 7, Firefox için eklenti.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] İçermemesi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox için eklenti. Ancak, her iki [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] ve [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] olan yüklü Firefox WPF eklentisinin ile yüklenen [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Bu nedenle [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] uygulamaları hala çalışır çünkü WPF konağı doğru framework sürümünü yükler. Daha fazla bilgi için [WPF Konağı (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>Firefox için .NET Framework Assistant  
 .NET Framework Assistant Firefox için Firefox tarayıcıdan çalıştırmak tek başına ClickOnce uygulamaları etkinleştirir. .NET Framework Assistant aynı şekilde önce ve sonra Firefox tarayıcısı yüklendiğinde Firefox işlevleri için. Firefox tarayıcısı ne zaman başlatılır ve [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] olan yüklü Firefox bulur ve Firefox için .NET Framework Yardımcısı'nı yükler. Kullanıcılar, .NET Framework Assistant aşağıdakileri yapmak Firefox için yapılandırabilirsiniz:  
  
-   ClickOnce uygulamasını çalıştırmadan önce sor  
  
-   .NET Framework'ün yüklü tüm sürümlerini ya da yalnızca en son sürümünü bildirin.  
  
 .NET Framework Assistant Firefox için birlikte [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Firefox için .NET Framework Assistant kaldırma hakkında daha fazla bilgi için bkz: [Firefox için .NET Framework Assistant kaldırma](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulaması Dağıtma](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
