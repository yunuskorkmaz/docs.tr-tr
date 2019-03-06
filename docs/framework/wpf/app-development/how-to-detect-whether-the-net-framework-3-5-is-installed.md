---
title: 'Nasıl yapılır: .NET Framework 3.5 yüklü olup olmadığını algılama'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 2f3e3077f78aed90f4e213d61267131019664fdb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378775"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="dfed5-102">Nasıl yapılır: .NET Framework 3.5 yüklü olup olmadığını algılama</span><span class="sxs-lookup"><span data-stu-id="dfed5-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="dfed5-103">Yöneticiler Windows Presentation Foundation (WPF) uygulamaları hedefleyen bir sistemde dağıtmadan önce [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], bunlar ilk olduğunu onaylaması gerekir [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] çalışma zamanının.</span><span class="sxs-lookup"><span data-stu-id="dfed5-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], they must first confirm that the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime is present.</span></span> <span data-ttu-id="dfed5-104">Bu konu, yazılan bir betik sağlar. Yöneticiler belirlemek için kullanabileceğiniz HTML/JavaScript içinde olup olmadığını [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] bir sistemde mevcut.</span><span class="sxs-lookup"><span data-stu-id="dfed5-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfed5-105">Yükleme, dağıtma ve algılama hakkında daha ayrıntılı bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bkz: [geliştiriciler için .NET Framework yükleme](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="dfed5-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfed5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfed5-106">Example</span></span>  
 <span data-ttu-id="dfed5-107">Zaman [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] olan yüklü MSI ".NET CLR" ve sürüm numarasını UserAgent dizesi olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="dfed5-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="dfed5-108">Aşağıdaki örnek, basit bir HTML sayfasında yerleşik bir komut dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfed5-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="dfed5-109">Komut dosyası belirlemek için UserAgent dizesi arar olmadığını [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] yüklenir ve arama sonuçlarını temel bir durum iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dfed5-109">The script searches the UserAgent string to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfed5-110">Bu betik, Internet Explorer için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dfed5-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="dfed5-111">Diğer tarayıcılarda UserAgent dizesi içinde .NET CLR bilgileri içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="dfed5-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
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
  
 <span data-ttu-id="dfed5-112">".NET CLR" sürümü için arama başarılı olursa, aşağıdaki türde durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="dfed5-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="dfed5-113">Aksi takdirde, aşağıdaki türde durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="dfed5-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="dfed5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfed5-114">See also</span></span>
- [<span data-ttu-id="dfed5-115">.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="dfed5-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
