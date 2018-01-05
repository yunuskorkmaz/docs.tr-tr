---
title: "Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 330ee213e147cfef709c919c95cb0e58159bc37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Internet bölgesi izinleri kümesi için kısıtlı bir kısmi güven güvenlik sandbox içinde çalışır. Bu izin kümesi yalnızca Web konumunda yer Hizmetleri için Web hizmeti çağrıları kısıtlayan [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kaynak uygulamanın site. Zaman bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] gelen hata ayıklaması [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]Web hizmeti olarak başvuruları aynı kaynak sitesi için dikkate alınmaz ancak. Ne zaman oluşturulması için bu nedenler güvenlik özel durumları [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmak çalışır. Ancak, bir [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje, kaynak çağırdığı hata ayıklama sırasında Web hizmeti ile aynı sitede olması benzetimini yapmak için yapılandırılabilir. Böylece [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] güvenlik özel durumları neden olmadan güvenli bir şekilde Web hizmetini çağırmak için.  
  
## <a name="configuring-visual-studio"></a>Visual Studio'yu yapılandırma  
 Yapılandırmak için [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] hata ayıklamak için bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web hizmeti çağrıları:  
  
1.  Seçili bir proje ile **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  İçinde **Proje Tasarımcısı**, tıklatın **hata ayıklama** sekmesi.  
  
3.  İçinde **eylemi Başlat** bölümünde, select **başlangıç dış program** ve aşağıdakileri girin:  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  İçinde **başlangıç seçenekleri** bölümünde, aşağıdaki girin **komut satırı bağımsız değişkenleri** metin kutusu:  
  
     `-debug`  *Dosya adı*  
  
     *Filename* değerini **-debug** parametredir .xbap filename; örneğin:  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  İle oluşturulan çözümleri için varsayılan yapılandırma budur [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonu.  
  
1.  Seçili bir proje ile **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  İçinde **Proje Tasarımcısı**, tıklatın **hata ayıklama** sekmesi.  
  
3.  İçinde **başlangıç seçenekleri** bölümünde, aşağıdaki komut satırı parametresini ekleyin **komut satırı bağımsız değişkenleri** metin kutusu:  
  
     `-debugSecurityZoneURL`  *URL*  
  
     *URL* değerini **- debugSecurityZoneURL** parametresi [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] , uygulamanızın kaynak site olarak benzetimini yapmak istediğiniz konum.  
  
 Örnek olarak, göz önünde bulundurun bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] ile aşağıdakileri bir Web hizmeti kullanan [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 Kaynak sitesi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] için bu Web hizmetidir:  
  
 `http://services.msdn.microsoft.com`  
  
 Sonuç olarak, tam **- debugSecurityZoneURL** komut satırı parametresi ve değeri:  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Konağı (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
