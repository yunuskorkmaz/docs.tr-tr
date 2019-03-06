---
title: "Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma"
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 94d362767b92799fa54f46e71724284a92b5bf7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358827"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] Internet bölgesi izinleri kümesi için kısıtlı bir kısmi güven güvenliği korumalı alan içinde çalıştırın. Bu izin kümesi, Web hizmeti çağrıları yalnızca şu adreste bulunabilir Hizmetleri Web sınırlar [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] kaynak uygulamanın siteyi. Olduğunda bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hataları ayıklanmakta Visual Studio 2005'ten yine de bu Web hizmeti olarak başvuruları aynı kaynak siteyi sahip olmadığı kabul edilir. Bu neden güvenlik özel durumlarını ne zaman yükseltilecek [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmak çalışır. Ancak, bir Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje, aynı kaynak siteyi çağırdığı hata ayıklama sırasında Web hizmeti olarak olması benzetimini yapmak için yapılandırılabilir. Böylece [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] güvenli bir şekilde güvenlik özel durumları neden olmadan Web hizmetini çağırmak için.

## <a name="configuring-visual-studio"></a>Visual Studio'yu yapılandırma
 Hata ayıklamak için Visual Studio 2005 yapılandırmak için bir [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bir Web hizmeti çağırır:

1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.

2.  İçinde **Proje Tasarımcısı**, tıklayın **hata ayıklama** sekmesi.

3.  İçinde **başlatma eylemi** bölümünden **harici program Başlat** ve şunu girin:

     `C:\WINDOWS\System32\PresentationHost.exe`

4.  İçinde **Başlat seçenekleri** bölümünde, aşağıdaki girin **komut satırı bağımsız değişkenleri** metin kutusunda:

     `-debug`  *Dosya adı*

     *Filename* değerini **-hata ayıklama** parametredir .xbap dosya adı; örneğin:

     `-debug c:\example.xbap`

> [!NOTE]
>  Bu Visual Studio 2005 ile oluşturulmuş çözümler için varsayılan yapılandırmadır [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonu.

1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.

2.  İçinde **Proje Tasarımcısı**, tıklayın **hata ayıklama** sekmesi.

3.  İçinde **Başlat seçenekleri** bölümünde, eklemek için aşağıdaki komut satırı parametresini **komut satırı bağımsız değişkenleri** metin kutusunda:

     `-debugSecurityZoneURL`  *URL*

     *URL* değerini **- debugSecurityZoneURL** parametresi [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] için uygulamanızın kaynak site olarak benzetimini yapmak istediğiniz konum.

 Örneğin, göz önünde bulundurun bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] şunlarla birlikte bir Web hizmeti kullanan [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Kaynak siteyi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] için bu Web hizmetidir:

 `http://services.msdn.microsoft.com`

 Sonuç olarak, tam **- debugSecurityZoneURL** komut satırı parametresi ve değeri:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Ayrıca bkz.
- [WPF Konağı (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
