---
title: WPF Konağı (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: ec8ec42c174d87834af5d4c651c1e8c8bde3b3e2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581697"
---
# <a name="wpf-host-presentationhostexe"></a>WPF Konağı (PresentationHost.exe)
Windows Presentation Foundation (WPF) ana bilgisayarı (PresentationHost. exe), [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarının uyumlu tarayıcılarda barındırılmasına olanak tanıyan uygulamadır (Microsoft Internet Explorer 6 ve üzeri dahil). Varsayılan olarak, Windows Presentation Foundation (WPF) ana bilgisayarı, aşağıdakiler de dahil olmak üzere tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği için kabuk ve MIME işleyicisi olarak kaydedilir:  
  
- Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (. xaml).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (. XBAP).  
  
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
|filename|Etkinleştirilecek dosyanın yolu. Ayrıca bir URI olabilir.|  
|-debug|Bir uygulamayı etkinleştirirken, bir uygulamayı üzerinde yürütmez veya mağazadan çalıştırmaz. Bu yalnızca yerel bir dosya etkinleştirildiğinde işe yarar.|  
|-debugSecurityZoneURL \<url >|Bir uygulamanın, belirtilen URL 'den dağıtılarak hata ayıklaması gerektiğini PresentationHost. exe ' ye işaret eden bir URL değeriyle birlikte kullanılır. Bu hem dağıtım bölgesini hem de kaynak sitesini belirler.|  
|-Gömme|OLE tarafından gerektirilir. @No__t_0 veya `-debug` parametresi belirtilirse, bu parametre dahili olarak ayarlandığı için `-embedding` parametresinin belirtilmesi gerekmez.|  
|-Event \<eventname >|Bu adı taşıyan olayı açın ve PresentationHost. exe başlatıldığında ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği barındırmaya hazırlandığınızda bunu işaret edin. Olay açılırken bir hata oluşursa (örneğin, zaten oluşturulmadıysa) PresentationHost. exe sonlandırılır.|  
|-launchApplication \<url >|Belirtilen URL 'den tek başına ClickOnce uygulaması başlatır. .NET uygulamaları ile ilgili Internet Explorer ve WinINet güvenlik ilkesi uygulanır.|  
  
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

- [Security](../security-wpf.md)
