---
title: Firefox WPF eklentisinin yüklü olup olmadığını Algıla
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 91680859c1742e5d5443d626c81273a80504f4a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740401"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="16e61-102">Nasıl yapılır: Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="16e61-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="16e61-103">Firefox için Windows Presentation Foundation (WPF) eklentisi, XAML tarayıcı uygulamaları (XBAP) ve gevşek XAML dosyalarının Mozilla Firefox tarayıcısında çalıştırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="16e61-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables XAML browser applications (XBAPs) and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="16e61-104">Bu konu başlığı altında, yöneticilerin Firefox WPF eklentisinin yüklü olup olmadığını belirlemede kullanabileceğiniz HTML ve JavaScript 'te yazılmış bir komut dosyası sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16e61-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="16e61-105">.NET Framework yükleme, dağıtma ve algılama hakkında daha fazla bilgi için bkz. [geliştiricilere yönelik .NET Framework yükleme](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="16e61-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="16e61-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e61-106">Example</span></span>

<span data-ttu-id="16e61-107">.NET Framework 3,5 yüklendiğinde, istemci bilgisayar Firefox için WPF eklentisi ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="16e61-107">When the .NET Framework 3.5 is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="16e61-108">Aşağıdaki örnek betik, Firefox WPF eklentisini denetler ve ardından uygun bir durum iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="16e61-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

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

<span data-ttu-id="16e61-109">Firefox WPF eklentisi için denetim başarılı olursa aşağıdaki durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="16e61-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="16e61-110">Aksi takdirde, aşağıdaki durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="16e61-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="16e61-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16e61-111">See also</span></span>

- [<span data-ttu-id="16e61-112">.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="16e61-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="16e61-113">.NET Framework 3.5'in Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="16e61-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="16e61-114">WPF XAML Tarayıcı Uygulamalarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16e61-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
