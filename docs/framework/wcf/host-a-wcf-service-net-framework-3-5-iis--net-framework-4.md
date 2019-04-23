---
title: 'Nasıl yapılır: .NET Framework 4 Altında Çalışan IIS .NET Framework 3.5 ile Yazılmış Bir WCF Hizmetini Barındırma'
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: d4f0cb584f7759a6fe52a4bec4306a7d714d3906
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976930"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a>Nasıl yapılır: .NET Framework 4 Altında Çalışan IIS .NET Framework 3.5 ile Yazılmış Bir WCF Hizmetini Barındırma
İle yazılmış bir Windows Communication Foundation (WCF) hizmetini barındırırken [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] çalışan bir makine üzerinde [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], alabilirsiniz bir <xref:System.ServiceModel.ProtocolException> aşağıdaki metinle.  
  
```Output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 Veya hizmetin .svc dosyasına gözatmak denerseniz, aşağıdaki metni içeren bir hata sayfası görebilirsiniz.  
  
```Output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 IIS içinde çalıştığı uygulama etki alanı çalıştığı için bu hataları ortaya [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] ve WCF Hizmeti altında çalışacak şekilde bekleniyor [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Bu konu başlığı altında çalışacağı hizmetin almak için gereken değişiklikleri açıklar.  
  
 Sonrakini Bul <`compilers`> öğesi ve değişiklik CompilerVersion sağlayıcısı seçeneği 4.0 değerine sahip. Varsayılan olarak, var olan iki <`compiler`> altında öğelerin <`compilers`> öğesi. Aşağıdaki örnekte gösterildiği gibi her ikisi için CompilerVersion sağlayıcı seçeneği güncelleştirmeniz gerekir.  
  
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
  
### <a name="add-the-required-targetframework-attribute"></a>Gerekli targetFramework öznitelik Ekle  
  
1. Hizmetin Web.config dosyasını açın ve Ara <`compilation`> öğesi.  
  
2. Ekleme `targetFramework` özniteliğini <`compilation`> Aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
3. Bulma <`compilers`> öğesi ve değişiklik CompilerVersion sağlayıcısı seçeneği 4.0 değerine sahip. Varsayılan olarak, var olan iki <`compiler`> altında öğelerin <`compilers`> öğesi. Aşağıdaki örnekte gösterildiği gibi her ikisi için CompilerVersion sağlayıcı seçeneği güncelleştirmeniz gerekir.  
  
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
