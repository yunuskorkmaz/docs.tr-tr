---
title: WPF Konağı (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: d3b1ebf3cd62b77a9082c0b149469462b5dffa3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577535"
---
# <a name="wpf-host-presentationhostexe"></a>WPF Konağı (PresentationHost.exe)
Windows Presentation Foundation (WPF) Konağı (PresentationHost.exe) sağlayan bir uygulama olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uyumlu tarayıcılarda uygulamaları (dahil olmak üzere [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] ve üzeri). Varsayılan olarak, Windows Presentation Foundation (WPF) konak olarak kabuğa kayıtlı ve [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] işleyicisi için tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği olarak da içerir:  
  
-   Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (.xaml).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Bu tür dosyalar için Windows Presentation Foundation (WPF) ana bilgisayar için:  
  
-   Kayıtlı başlatır [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] Windows Presentation Foundation (WPF) içeriğini barındırmak için işleyici.  
  
-   Gerekli doğru sürümlerini yükler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ve Windows Presentation Foundation (WPF) derlemeleri.  
  
-   Dağıtım bölgesi için uygun izin düzeylerini yerinde olmasını sağlar.  
  
 Bu konu ile PresentationHost.exe kullanılabilir komut satırı parametreleri açıklar.  
  
## <a name="usage"></a>Kullanım  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|filename|Etkinleştirilecek dosyasının yolu. Ayrıca olabilir bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-hata ayıklama|Bir uygulama etkinleştirilirken bırakmaz için işleme veya mağaza'dan çalıştırın. Bu, yalnızca yerel bir dosyaya etkinleştirildiğinde çalışır.|  
|-debugSecurityZoneURL \<URL'si >|İle kullanılan bir [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] PresentationHost.exe için gibi dağıtıldıysa uygulamanın hata ayıklaması belirtmek için değer belirtilen [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Bu dağıtım bölgesi hem kaynak siteyi belirler.|  
|-ekleme|OLE için gereklidir. Varsa `-event` veya `-debug` parametresi belirtilirse, belirtmek gerekli değil `-embedding` parametresi, çünkü bu parametre, dahili olarak ayarlanır.|  
|-olay \<eventname >|Bu ada sahip olayı açın ve PresentationHost.exe konak başlatıldı ve hazır olduğunda sinyal [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği. PresentationHost.exe sonlandırılacak olay açılırken bir hata olduğunda, IF gibi onu değil zaten oluşturuldu.|  
|-launchApplication \<URL'si >|Tek başına bir başlatır [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] belirtilen URL'den uygulama. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] ve .NET uygulamaları ile ilgili WinINet güvenlik ilkesi uygulanır.|  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="shell-handler"></a>Kabuk işleyicisi  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME işleyicisi  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio hata ayıklama  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio bölgede hata ayıklama  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Güvenlik](../../../../docs/framework/wpf/security-wpf.md)
