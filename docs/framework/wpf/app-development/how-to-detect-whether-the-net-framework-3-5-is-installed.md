---
title: 'Nasıl yapılır: .NET Framework 3.5 yüklü olup olmadığını Algıla'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4999e3e1a9e402cb8848d030ab483f057428486
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="82043-102">Nasıl yapılır: .NET Framework 3.5 yüklü olup olmadığını Algıla</span><span class="sxs-lookup"><span data-stu-id="82043-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="82043-103">Yöneticiler Windows Presentation Foundation (WPF) uygulamaları hedefleyen bir sistemde dağıtmadan önce [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], bunlar ilk olduğunu onaylaması gerekir [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] çalışma zamanının.</span><span class="sxs-lookup"><span data-stu-id="82043-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], they must first confirm that the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime is present.</span></span> <span data-ttu-id="82043-104">Bu konuda yazılmış bir betik sağlar, yöneticilerin belirlemek için kullanabilecekleri HTML/JavaScript içinde olup olmadığını [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] bir sistemde mevcut.</span><span class="sxs-lookup"><span data-stu-id="82043-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82043-105">Yükleme, dağıtma ve algılama hakkında daha ayrıntılı bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="82043-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82043-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="82043-106">Example</span></span>  
 <span data-ttu-id="82043-107">Zaman [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] olan yüklü MSI ".NET CLR" ve sürüm numarasını UserAgent dizesi olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="82043-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="82043-108">Aşağıdaki örnekte basit bir HTML sayfasında yerleşik bir komut dosyası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82043-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="82043-109">Komut dosyası belirlemek için UserAgent dizesi arar olup olmadığını [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] yüklü olduğundan ve arama sonuçlarını durum iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82043-109">The script searches the UserAgent string to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82043-110">Bu komut dosyası, Internet Explorer için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="82043-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="82043-111">Diğer tarayıcılarda UserAgent dizesi içinde .NET CLR bilgi içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="82043-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="82043-112">".NET CLR" sürüm için arama başarılı olursa, aşağıdaki türde durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="82043-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="82043-113">Aksi takdirde, aşağıdaki türde durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="82043-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="82043-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82043-114">See Also</span></span>  
 [<span data-ttu-id="82043-115">.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="82043-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)
