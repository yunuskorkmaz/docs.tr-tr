---
title: "Nasıl yapılır: .NET Framework 4 altında çalışan IIS 'de .NET Framework 3,5 ile yazılmış bir WCF hizmetini barındırma"
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 6a87fd5e3997e9d15810a5efb079da629908f854
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291530"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a>Nasıl yapılır: .NET Framework 4 altında çalışan IIS 'de .NET Framework 3,5 ile yazılmış bir WCF hizmetini barındırma
@No__t-1 çalıştıran bir makinede [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] ile yazılmış bir Windows Communication Foundation (WCF) hizmeti barındırırken, aşağıdaki metinle bir <xref:System.ServiceModel.ProtocolException> alabilirsiniz.  
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 Ya da hizmetin. svc dosyasına gözatmaya çalışırsanız, aşağıdaki metinle bir hata sayfası görebilirsiniz.  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 Bu hatalar, IIS 'nin içinde çalıştığı uygulama etki alanı [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ' dır ve WCF hizmetinin [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] altında çalıştırılmasını beklediği için oluşur. Bu konuda hizmeti çalıştırmak için gereken değişiklikler açıklanmaktadır.  
  
 Ardından < `compilers` > öğesini bulun ve CompilerVersion sağlayıcısı seçeneğini 4,0 değerine sahip olacak şekilde değiştirin. Varsayılan olarak, < `compilers` > öğesi altında iki < `compiler` > öğesi vardır. Aşağıdaki örnekte gösterildiği gibi, CompilerVersion sağlayıcı seçeneğini her ikisi için de güncelleştirmeniz gerekir.  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a>Gerekli targetFramework özniteliğini ekleyin  
  
1. Hizmetin Web. config dosyasını açın ve < `compilation` > öğesini arayın.  
  
2. Aşağıdaki örnekte gösterildiği gibi, `targetFramework` özniteliğini < `compilation` > öğesine ekleyin.  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3. < @No__t-0 > öğesini bulun ve CompilerVersion sağlayıcısı seçeneğini 4,0 değerine sahip olacak şekilde değiştirin. Varsayılan olarak, < `compilers` > öğesi altında iki < `compiler` > öğesi vardır. Aşağıdaki örnekte gösterildiği gibi, CompilerVersion sağlayıcı seçeneğini her ikisi için de güncelleştirmeniz gerekir.  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
