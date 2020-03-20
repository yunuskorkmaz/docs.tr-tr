---
title: Nasıl yapılır .NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 60868661df442849db3f5421f8ea33f790fd83fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187361"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="d68c1-102">Nasıl yapılır .NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="d68c1-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="d68c1-103">Yöneticiler Microsoft .NET Framework uygulamalarını bir sistemde dağıtabilmeleri için önce .NET Framework çalışma zamanının mevcut olduğunu onaylamaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="d68c1-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="d68c1-104">Bu konu, yöneticilerin .NET Framework'ün bir sistemde bulunup bulunmadığını belirlemek için kullanabilecekleri HTML/JavaScript ile yazılmış bir komut dosyası sağlar.</span><span class="sxs-lookup"><span data-stu-id="d68c1-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d68c1-105">Microsoft .NET Framework'ün yüklenmesi, dağıtılması ve algılanması hakkında daha ayrıntılı bilgi için Microsoft [.NET Framework Version 3.0'ı dağıtmadaki](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10))tartışmaya bakın.</span><span class="sxs-lookup"><span data-stu-id="d68c1-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span></span>  
  
<a name="content_expiration"></a>
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="d68c1-106">".NET CLR" Kullanıcı Aracısı Dizesini algıla</span><span class="sxs-lookup"><span data-stu-id="d68c1-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="d68c1-107">.NET Framework yüklendiğinde, MSI UserAgent dizesine ".NET CLR" ve sürüm numarasını ekler.</span><span class="sxs-lookup"><span data-stu-id="d68c1-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="d68c1-108">Aşağıdaki örnekte, basit bir HTML sayfasına katışılmış bir komut dosyası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d68c1-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="d68c1-109">Komut dosyası, .NET Framework'ün yüklü olup olmadığını belirlemek için UserAgent dizesini arar ve arama sonuçlarında bir durum iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d68c1-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
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
  
 <span data-ttu-id="d68c1-110">".NET CLR " sürümü için arama başarılı olursa, aşağıdaki durum iletisi türü görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="d68c1-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="d68c1-111">Aksi takdirde, aşağıdaki durum iletisi türü görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="d68c1-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
