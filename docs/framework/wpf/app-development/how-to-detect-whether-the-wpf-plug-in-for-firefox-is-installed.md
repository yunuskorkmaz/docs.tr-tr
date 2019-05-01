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
ms.openlocfilehash: 138c212e79654b8ac875628692b49bb6a38cb695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947881"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Nasıl yapılır: Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama

Windows Presentation Foundation (WPF) için Firefox eklentisini sağlayan [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve XAML dosyalarının Mozilla Firefox tarayıcınızda çalıştırın kaybedilir. Bu konu, HTML ve JavaScript Yöneticiler Firefox WPF eklentisinin yüklü olup olmadığını belirlemek için kullanabileceğiniz yazılmış bir komut dosyası sağlar.

> [!NOTE]
> Yükleme, dağıtma ve algılama hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bkz: [geliştiriciler için .NET Framework yükleme](../../install/guide-for-developers.md).

## <a name="example"></a>Örnek

Zaman [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] olan yüklü istemci bilgisayar için Firefox WPF eklentisinin ile yapılandırılır. Aşağıdaki örnek betik, Firefox WPF eklentisinin için denetler ve ardından uygun durum iletisini görüntüler.

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

Firefox için WPF eklentisi onay başarılı olursa, aşağıdaki durum iletisi görüntülenir:

`The WPF plug-in for Firefox is installed.`

Aksi takdirde, aşağıdaki durum iletisi görüntülenir:

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [.NET Framework 3.5'in Yüklü Olup Olmadığını Algılama](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](wpf-xaml-browser-applications-overview.md)
