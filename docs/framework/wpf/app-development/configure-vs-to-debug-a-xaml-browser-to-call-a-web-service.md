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
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958681"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Internet bölgesi izin kümesiyle kısıtlanmış bir kısmi güven güvenlik alanı içinde çalıştırın. Bu izin kümesi, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmeti çağrılarını yalnızca uygulamanın kaynak sitesinde bulunan Web Hizmetleri ile sınırlandırır. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Visual Studio 2005 ' den hata ayıklandığında, başvurduğu Web hizmetiyle aynı kaynak sitesine sahip olduğu kabul edilmez. Bu, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web hizmetini çağırmaya çalıştığında güvenlik özel durumlarının oluşturulmasına neden olur. Ancak, bir Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projesi, hata ayıklama sırasında çağırdığı Web hizmeti ile aynı kaynak sitesine sahip olmayı taklit etmek için yapılandırılabilir. Bu, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] güvenlik özel durumlarına neden olmadan Web hizmetini güvenle çağırabilme olanağı sağlar.

## <a name="configuring-visual-studio"></a>Visual Studio’yu yapılandırma
 Visual Studio 2005 ' i bir Web hizmetini [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] çağıran bir hata ayıklamada yapılandırmak için:

1. Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.

2. **Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.

3. **Başlat eylemi** bölümünde **dış program Başlat** ' ı seçin ve aşağıdakileri girin:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. **Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdakini girin:

     `-debug`  *kısaltın*

     **-Debug** parametresinin *filename* değeri. XBAP dosya adıdır; Örneğin:

     `-debug c:\example.xbap`

> [!NOTE]
> Bu, Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] proje şablonuyla oluşturulan çözümlerin varsayılan yapılandırmadır.

1. Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.

2. **Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.

3. **Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdaki komut satırı parametresini ekleyin:

     `-debugSecurityZoneURL`  *'DEKI*

     **-DebugSecurityZoneURL** parametresi için [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] *URL* değeri, uygulamanızın kaynak sitesi olarak benzetimini yapmak istediğiniz konum içindir.

 Örnek olarak, aşağıdakileri [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]içeren bir Web hizmeti kullanan bir düşünün:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Bu Web hizmetinin kaynak [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] sitesi:

 `http://services.msdn.microsoft.com`

 Sonuç olarak, tam **-DebugSecurityZoneURL** komut satırı parametresi ve değeri:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Konağı (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
