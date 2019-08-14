---
title: WPF Konağı (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: eda34c71f5735ae7ea3fcedea3a400e92756243b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972249"
---
# <a name="wpf-host-presentationhostexe"></a>WPF Konağı (PresentationHost.exe)
Windows Presentation Foundation (WPF) ana bilgisayarı (PresentationHost. exe), uygulamaların uyumlu tarayıcılarda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] barındırılmasına olanak tanıyan uygulamadır (Microsoft Internet Explorer 6 ve üzeri dahil). Varsayılan olarak, Windows Presentation Foundation (WPF) ana bilgisayarı, aşağıdakiler de dahil olmak üzere tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içerik için kabuk ve MIME işleyicisi olarak kaydedilir:  
  
- Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalar (. xaml).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)](. XBAP).  
  
 Bu türlerin dosyaları için Windows Presentation Foundation (WPF) ana bilgisayarı:  
  
- Windows Presentation Foundation (WPF) içeriğini barındırmak için kayıtlı HTML işleyicisini başlatır.  
  
- Gerekli ortak dil çalışma zamanı (CLR) ve Windows Presentation Foundation (WPF) derlemelerinin doğru sürümlerini yükler.  
  
- Dağıtım bölgesi için uygun izin düzeylerinin yerinde olmasını sağlar.  
  
 Bu konu, PresentationHost. exe ile kullanılabilecek komut satırı parametrelerini açıklar.  
  
## <a name="usage"></a>Kullanım  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|filename|Etkinleştirilecek dosyanın yolu. Aynı zamanda bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]de olabilir.|  
|-debug|Bir uygulamayı etkinleştirirken, bir uygulamayı üzerinde yürütmez veya mağazadan çalıştırmaz. Bu yalnızca yerel bir dosya etkinleştirildiğinde işe yarar.|  
|-DebugSecurityZoneURL \<URL 'si >|PresentationHost. exe [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] ' ye, bir uygulamanın, belirtilen [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]sunucudan dağıtılmışsa olarak hata ayıklaması gerektiğini belirten bir değerle birlikte kullanılır. Bu hem dağıtım bölgesini hem de kaynak sitesini belirler.|  
|-Gömme|OLE tarafından gerektirilir. Ya da parametresi belirtilirse, bu parametre dahili olarak ayarlandığı için `-embedding` parametresini belirtmeniz gerekmez. `-debug` `-event`|  
|-Event \<EventName >|Bu adı taşıyan olayı açın ve PresentationHost. exe başlatıldığında ve içeriği barındırmak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] için hazırsanız bunu işaret edin. Olay açılırken bir hata oluşursa (örneğin, zaten oluşturulmadıysa) PresentationHost. exe sonlandırılır.|  
|-launchApplication \<URL >|Belirtilen URL 'den tek başına ClickOnce uygulaması başlatır. .NET uygulamaları ile ilgili Internet Explorer ve WinINet güvenlik ilkesi uygulanır.|  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="shell-handler"></a>Kabuk Işleyicisi  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME Işleyicisi  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio hata ayıklaması  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Bölgede Visual Studio hata ayıklaması  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../security-wpf.md)
