---
title: "Nasıl yapılır: .NET Framework 3.5'in Yüklü Olup Olmadığını Algılama"
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 69dfa0eb8d9ad9b780d258a874d255484f270cfe
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690440"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>Nasıl yapılır: .NET Framework 3.5'in Yüklü Olup Olmadığını Algılama
Yöneticiler, .NET Framework 3. 5'i hedefleyen bir sistemde Windows Presentation Foundation (WPF) uygulamaları dağıtmadan önce ilk olarak, .NET Framework 3.5 çalışma zamanı mevcut olduğunu onaylamanız gerekir. Bu konu, HTML/JavaScript dilinde yazılmış bir komut dosyası sağlar. Yöneticiler, .NET Framework 3.5 bir sistemde mevcut olup olmadığını belirlemek için kullanabilirsiniz.  
  
> [!NOTE]
>  Yükleme hakkında daha ayrıntılı bilgi için bkz: dağıtma ve .NET Framework'ü algılama [geliştiriciler için .NET Framework yükleme](../../install/guide-for-developers.md).  
  
## <a name="example"></a>Örnek  
 .NET Framework 3.5 yüklendiğinde, MSI ".NET CLR" ve sürüm numarasını UserAgent dizesi olarak ekler. Aşağıdaki örnek, basit bir HTML sayfasında yerleşik bir komut dosyası gösterir. Komut dosyası, .NET Framework 3.5 yüklenir ve arama sonuçlarını temel durum iletisini görüntüler olup olmadığını belirlemek için UserAgent dizesi arar.  
  
> [!NOTE]
>  Bu betik, Internet Explorer için tasarlanmıştır. Diğer tarayıcılarda UserAgent dizesi içinde .NET CLR bilgileri içermeyebilir.  
  
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
  
 ".NET CLR" sürümü için arama başarılı olursa, aşağıdaki türde durum iletisi görüntülenir:  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 Aksi takdirde, aşağıdaki türde durum iletisi görüntülenir:  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
