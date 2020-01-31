---
title: WPF Konağı (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743404"
---
# <a name="wpf-host-presentationhostexe"></a>WPF Konağı (PresentationHost.exe)
Windows Presentation Foundation (WPF) ana bilgisayarı (PresentationHost. exe), WPF uygulamalarının uyumlu tarayıcılarda barındırılmasına olanak tanıyan uygulamadır (Microsoft Internet Explorer 6 ve üzeri dahil). Varsayılan olarak, Windows Presentation Foundation (WPF) ana bilgisayarı, tarayıcı tarafından barındırılan WPF içeriği için kabuk ve MIME işleyicisi olarak kaydedilir ve şunları içerir:  
  
- Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (. xaml).  
  
- XAML tarayıcısı uygulaması (XBAP) (. XBAP).  
  
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
|-debugSecurityZoneURL \<URL >|Bir uygulamanın, belirtilen URL 'den dağıtılarak hata ayıklaması gerektiğini PresentationHost. exe ' ye işaret eden bir URL değeriyle birlikte kullanılır. Bu hem dağıtım bölgesini hem de kaynak sitesini belirler.|  
|-Gömme|OLE tarafından gerektirilir. `-event` veya `-debug` parametresi belirtilirse, bu parametre dahili olarak ayarlandığı için `-embedding` parametresinin belirtilmesi gerekmez.|  
|-Event \<EventName >|Bu adı taşıyan olayı açın ve PresentationHost. exe başlatıldığında ve WPF içeriğini barındırmak için hazırsanız bunu işaret edin. Olay açılırken bir hata oluşursa (örneğin, zaten oluşturulmadıysa) PresentationHost. exe sonlandırılır.|  
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

- [Security](../security-wpf.md)
