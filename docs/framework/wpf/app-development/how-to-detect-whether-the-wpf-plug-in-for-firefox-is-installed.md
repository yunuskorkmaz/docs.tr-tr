---
title: 'Nasıl yapılır: Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: fdc7b516c316c7efc7056b549baf43191a5aedd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423756"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Nasıl yapılır: Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama

Firefox için Windows Presentation Foundation (WPF) eklentisi, XAML tarayıcı uygulamaları (XBAP) ve gevşek XAML dosyalarının Mozilla Firefox tarayıcısında çalıştırılmasını sağlar. Bu konu başlığı altında, yöneticilerin Firefox WPF eklentisinin yüklü olup olmadığını belirlemede kullanabileceğiniz HTML ve JavaScript 'te yazılmış bir komut dosyası sağlanmaktadır.

> [!NOTE]
> .NET Framework yükleme, dağıtma ve algılama hakkında daha fazla bilgi için bkz. [geliştiricilere yönelik .NET Framework yükleme](../../install/guide-for-developers.md).

## <a name="example"></a>Örnek

.NET Framework 3,5 yüklendiğinde, istemci bilgisayar Firefox için WPF eklentisi ile yapılandırılır. Aşağıdaki örnek betik, Firefox WPF eklentisini denetler ve ardından uygun bir durum iletisi görüntüler.

```html
<HTML>

  <HEAD>
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />
    <SCRIPT type="text/javascript">
    <!--
    function OnLoad()
    {

       // Check for the WPF plug-in for Firefox and report
       var msg = "The WPF plug-in for Firefox is ";
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];
       if( wpfPlugin != null ) {
          document.writeln(msg + " installed.");
       }
       else {
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");
       }
    }
    -->
    </SCRIPT>
  </HEAD>

  <BODY onload="OnLoad()" />

</HTML>
```

Firefox WPF eklentisi için denetim başarılı olursa aşağıdaki durum iletisi görüntülenir:

`The WPF plug-in for Firefox is installed.`

Aksi takdirde, aşağıdaki durum iletisi görüntülenir:

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [.NET Framework 3.5'in Yüklü Olup Olmadığını Algılama](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](wpf-xaml-browser-applications-overview.md)
