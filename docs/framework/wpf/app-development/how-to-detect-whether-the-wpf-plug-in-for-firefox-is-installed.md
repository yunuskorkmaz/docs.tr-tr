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
ms.openlocfilehash: ba411d662a8e5b0c4727e23c8d507e8924b6e9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546994"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Nasıl yapılır: Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama
Windows Presentation Foundation (WPF) Firefox eklentisi etkinleştirir [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ve kaybetmiş Mozilla Firefox tarayıcıda çalıştırmak için XAML dosyaları. Bu konu, HTML ve yöneticilerin Firefox WPF eklentisinin yüklü olup olmadığını belirlemek için kullanabileceğiniz JavaScript yazılmış bir betik sağlar.  
  
> [!NOTE]
>  Yükleme, dağıtma ve algılama hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Örnek  
 Zaman [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] olan yüklü istemci bilgisayar Firefox WPF eklentisi ile yapılandırılır. Aşağıdaki örnek betik, Firefox WPF eklentisini denetler ve uygun durum iletisini görüntüler.  
  
```  
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
  
 Firefox WPF eklentisi denetle başarılı olursa, aşağıdaki durum iletisi görüntülenir:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 Aksi takdirde, aşağıdaki durum iletisi görüntülenir:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [.NET Framework 3.5'in Yüklü Olup Olmadığını Algılama](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
