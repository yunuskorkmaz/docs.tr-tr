---
title: "Nasıl yapılır: .NET Framework 3.0'in Yüklü Olup Olmadığını Algılama"
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: e307125a2a8de3edc4df2fc1022c6e3de1904879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960251"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a>Nasıl yapılır: .NET Framework 3.0'in Yüklü Olup Olmadığını Algılama
Yöneticiler bir sistemde Microsoft .NET Framework uygulamaları dağıtabilmek için önce .NET Framework çalışma zamanının mevcut olduğunu doğrulamamalıdır. Bu konuda, yöneticilerin bir sistemde .NET Framework olup olmadığını belirlemede kullanabilecekleri HTML/JavaScript 'te yazılmış bir komut dosyası sağlanmaktadır.  
  
> [!NOTE]
> Microsoft .NET çerçevesini yükleme, dağıtma ve algılamayla ilgili daha ayrıntılı bilgi için bkz. [Microsoft .NET Framework sürüm 3,0](https://go.microsoft.com/fwlink/?LinkId=96739)' i dağıtma.  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a>".NET CLR" Kullanıcı aracısı dizesini Algıla  
 .NET Framework yüklendiğinde, MSI ".NET CLR" ve sürüm numarasını UserAgent dizesine ekler. Aşağıdaki örnek, basit bir HTML sayfasına eklenmiş bir betiği gösterir. Betik, .NET Framework yüklenip yüklenmediğini ve aramanın sonuçlarında bir durum iletisi görüntüleyip oluşturulmayacağını anlamak için UserAgent dizesini arar.  
  
```  
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
  
 ".NET CLR" sürümü için arama başarılı olursa aşağıdaki tür durum iletisi görüntülenir:  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 Aksi takdirde, aşağıdaki tür durum iletisi görüntülenir:  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
