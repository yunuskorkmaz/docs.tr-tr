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
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>Nasıl yapılır: .NET Framework 3.5 yüklü olup olmadığını algılama
Yöneticiler Windows Presentation Foundation (WPF) uygulamaları hedefleyen bir sistemde dağıtmadan önce [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], bunlar ilk olduğunu onaylaması gerekir [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] çalışma zamanının. Bu konu, yazılan bir betik sağlar. Yöneticiler belirlemek için kullanabileceğiniz HTML/JavaScript içinde olup olmadığını [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] bir sistemde mevcut.  
  
> [!NOTE]
>  Yükleme, dağıtma ve algılama hakkında daha ayrıntılı bilgi için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bkz: [geliştiriciler için .NET Framework yükleme](../../install/guide-for-developers.md).  
  
## <a name="example"></a>Örnek  
 Zaman [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] olan yüklü MSI ".NET CLR" ve sürüm numarasını UserAgent dizesi olarak ekler. Aşağıdaki örnek, basit bir HTML sayfasında yerleşik bir komut dosyası gösterir. Komut dosyası belirlemek için UserAgent dizesi arar olmadığını [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] yüklenir ve arama sonuçlarını temel bir durum iletisi görüntüler.  
  
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
