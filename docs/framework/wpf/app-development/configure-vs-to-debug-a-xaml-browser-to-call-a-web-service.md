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
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460906"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Nasıl yapılır: Web Hizmeti Çağırmak Amacıyla XAML Tarayıcı Uygulamasında Hata Ayıklamak için Visual Studio'yu Yapılandırma
XAML tarayıcı uygulamaları (XBAP), Internet bölgesi izinleri kümesiyle kısıtlanmış bir kısmi güven güvenlik korumalı alanı içinde çalışır. Bu izin kümesi, Web hizmeti çağrılarını yalnızca XBAP uygulamasının kaynak sitesinde bulunan Web hizmetlerine kısıtlar. Visual Studio 2005 ' den bir XBAP hatası ayıklandığında, başvurduğu Web hizmetiyle aynı kaynak sitesine sahip olarak değerlendirilmez. Bu, XBAP Web hizmetini çağırmayı denediğinde güvenlik özel durumlarının oluşturulmasına neden olur. Ancak, bir Visual Studio 2005 XAML tarayıcı uygulaması (WPF) projesi, hata ayıklama sırasında çağırdığı Web hizmeti ile aynı kaynak sitesine sahip olmayı taklit etmek üzere yapılandırılabilir. Bu, XBAP 'nin güvenlik özel durumlarına neden olmadan Web hizmetini güvenle çağırmasını sağlar.

## <a name="configuring-visual-studio"></a>Visual Studio’yu yapılandırma
 Visual Studio 2005 ' i bir Web hizmeti çağıran bir XBAP hata ayıklaması için yapılandırmak için:

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.

3. **Başlat eylemi** bölümünde **dış program Başlat** ' ı seçin ve aşağıdakileri girin:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. **Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdakini girin:

     `-debug`  *dosya adı*

     **-Debug** parametresinin *filename* değeri. XBAP dosya adıdır; Örneğin:

     `-debug c:\example.xbap`

> [!NOTE]
> Bu, Visual Studio 2005 XAML tarayıcı uygulaması (WPF) proje şablonuyla oluşturulan çözümlerin varsayılan yapılandırmadır.

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Proje tasarımcısında** **Hata Ayıkla** sekmesine tıklayın.

3. **Başlangıç seçenekleri** bölümünde **komut satırı bağımsız değişkenleri** metin kutusuna aşağıdaki komut satırı parametresini ekleyin:

     `-debugSecurityZoneURL`  *URL 'si*

     **-DebugSecurityZoneURL** parametresi için *URL* değeri, uygulamanızın kaynak sitesi olarak benzetimini yapmak istediğiniz konumun URL 'sidir.

 Örnek olarak, aşağıdaki URL ile bir Web hizmeti kullanan bir XAML tarayıcı uygulaması (XBAP) göz önünde bulundurun:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Bu Web hizmetinin kaynak URL 'SI sitesi:

 `http://services.msdn.microsoft.com`

 Sonuç olarak, tam **-DebugSecurityZoneURL** komut satırı parametresi ve değeri:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Konağı (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
