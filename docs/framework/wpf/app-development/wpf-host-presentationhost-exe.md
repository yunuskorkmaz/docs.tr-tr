---
title: "WPF Konağı (PresentationHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b7662213d7204675de7e8681b6fc8141f04dd21
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-host-presentationhostexe"></a>WPF Konağı (PresentationHost.exe)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Konağı (PresentationHost.exe) olan sağlayan uygulama [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uyumlu tarayıcıda barındırılan uygulamalar (de dahil olmak üzere [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] ve üzeri). Varsayılan olarak, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] konağı olarak kabuğa kayıtlı ve [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] işleyicisi için tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeren içerik:  
  
-   Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (.xaml).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)](.xbap).  
  
 Bu tür dosyalar için [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ana bilgisayar:  
  
-   Kayıtlı başlatır [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] konak işleyicisine [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] içeriği.  
  
-   Gerekli doğru sürümlerini yükler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ve [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] derlemeler.  
  
-   Dağıtım bölgesi için uygun izin düzeylerinin yerinde olmasını sağlar.  
  
 Bu konu, PresentationHost.exe ile kullanılabilen komut satırı parametreleri açıklar.  
  
## <a name="usage"></a>Kullanım  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|filename|Etkinleştirilecek dosyasının yolu. Aynı zamanda olabilir bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-hata ayıklama|Bir uygulama etkinleştirilirken değil kendisine yürütün veya mağaza'dan çalıştırın. Bu, yalnızca yerel bir dosya etkinleştirildiğinde çalışır.|  
|-debugSecurityZoneURL \<url >|İle kullanılan bir [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] PresentationHost.exe'ye izin olarak dağıtıldıysa uygulama hata ayıklaması belirtmek için değer belirtilen [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Bu dağıtım bölgesini ve kaynak site belirler.|  
|-katıştırma|OLE için gereklidir. Varsa `-event` veya `-debug` parametresi belirtilirse, belirtmek gerekli değildir `-embedding` parametresi, çünkü bu parametre dahili olarak ayarlanır.|  
|-olay \<eventname >|Bu ada sahip olayı açın ve PresentationHost.exe başlatılmış ve hazır konak olduğu sinyali [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği. PresentationHost.exe sonlandırılacak olay açılırken bir hata varsa, eğer gibi zaten oluşturulmadı.|  
|-launchApplication \<url >|Tek başına başlatır [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] belirtilen URL'den uygulama. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]ve .NET uygulamaları ile ilgili WinINet güvenlik ilkesi uygulanır.|  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="shell-handler"></a>Kabuk işleyicisi  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME işleyicisi  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio hata ayıklama  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio bölgesinde hata ayıklaması  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../../docs/framework/wpf/security-wpf.md)
