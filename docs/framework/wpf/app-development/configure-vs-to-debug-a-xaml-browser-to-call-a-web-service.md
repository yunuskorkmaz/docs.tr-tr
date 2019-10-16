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
ms.openlocfilehash: 7730ab452e227b11e5a9dd69cdabec51f333ce4f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321195"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], Internet bölgesi izin kümesiyle kısıtlanmış bir kısmi güven güvenlik alanı içinde çalışır. Bu izin kümesi, Web hizmeti çağrılarını yalnızca [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] uygulamasının kaynak sitesinde bulunan Web hizmetlerine kısıtlar. @No__t-0 ' dan Visual Studio 2005 hatası ayıklandığında, başvurduğu Web hizmetiyle aynı kaynak sitesine sahip olarak değerlendirilmez. Bu, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmaya çalıştığında güvenlik özel durumlarının oluşturulmasına neden olur. Ancak, bir Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projesi, hata ayıklama sırasında çağırdığı Web hizmeti ile aynı kaynak sitesine sahip olmayı taklit etmek için yapılandırılabilir. Bu, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ' ın güvenlik özel durumlarına neden olmadan Web hizmetini güvenle çağırmasına izin verir.

## <a name="configuring-visual-studio"></a>Visual Studio’yu yapılandırma
 Visual Studio 2005 ' i bir Web hizmeti çağıran @no__t hata ayıklaması yapmak üzere yapılandırmak için:

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.

3. **Başlat eylemi** bölümünde **dış program Başlat** ' ı seçin ve aşağıdakileri girin:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. **Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdakini girin:

     `-debug`  *dosya adı*

     **-Debug** parametresinin *filename* değeri. XBAP dosya adıdır; Örneğin:

     `-debug c:\example.xbap`

> [!NOTE]
> Bu, Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonuyla oluşturulan çözümlerin varsayılan yapılandırmadır.

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.

3. **Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdaki komut satırı parametresini ekleyin:

     `-debugSecurityZoneURL`  *URL 'si*

     **-DebugSecurityZoneURL** parametresi için *URL* değeri, uygulamanızın kaynak sitesi olarak benzetimini yapmak istediğiniz konumun URL 'sidir.

 Örnek olarak, aşağıdaki URL ile bir Web hizmeti kullanan [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] ' ı düşünün:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Bu Web hizmetinin kaynak URL 'SI sitesi:

 `http://services.msdn.microsoft.com`

 Sonuç olarak, tam **-DebugSecurityZoneURL** komut satırı parametresi ve değeri:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Konağı (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
