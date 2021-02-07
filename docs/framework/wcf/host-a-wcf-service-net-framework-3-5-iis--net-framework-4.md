---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: .NET Framework 4 altında çalışan IIS 'de .NET Framework 3,5 ile yazılmış bir WCF hizmetini barındırma"
title: 'Nasıl yapılır: .NET Framework 4 Altında Çalışan IIS .NET Framework 3.5 ile Yazılmış Bir WCF Hizmetini Barındırma'
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 3ea46b589df293b39369521a133cf9facad97d93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755973"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="3a684-103">Nasıl yapılır: .NET Framework 4 Altında Çalışan IIS .NET Framework 3.5 ile Yazılmış Bir WCF Hizmetini Barındırma</span><span class="sxs-lookup"><span data-stu-id="3a684-103">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>

<span data-ttu-id="3a684-104">.NET Framework 4 çalıştıran bir makinede .NET Framework 3,5 ile yazılmış bir Windows Communication Foundation (WCF) hizmetini barındırırken <xref:System.ServiceModel.ProtocolException> aşağıdaki metinle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a684-104">When hosting a Windows Communication Foundation (WCF) service written with .NET Framework 3.5 on a machine running .NET Framework 4, you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="3a684-105">Ya da hizmetin. svc dosyasına gözatmaya çalışırsanız, aşağıdaki metinle bir hata sayfası görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a684-105">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="3a684-106">Bu hatalar, IIS 'nin içinde çalıştığı uygulama etki alanı .NET Framework 4 ' ün çalıştığı ve WCF hizmetinin .NET Framework 3,5 altında çalıştırılmasını beklediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="3a684-106">These errors occur because the application domain IIS is running within is running .NET Framework 4 and the WCF service is expecting to run under .NET Framework 3.5.</span></span> <span data-ttu-id="3a684-107">Bu konuda hizmeti çalıştırmak için gereken değişiklikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a684-107">This topic explains the modifications required to get the service to run.</span></span>
  
 <span data-ttu-id="3a684-108">Ardından <`compilers`> öğesini bulun ve CompilerVersion sağlayıcısı seçeneğini 4,0 değerine sahip olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3a684-108">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="3a684-109">Varsayılan olarak, `compiler` <> öğesi altında iki <> öğesi vardır `compilers` .</span><span class="sxs-lookup"><span data-stu-id="3a684-109">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="3a684-110">Aşağıdaki örnekte gösterildiği gibi, CompilerVersion sağlayıcı seçeneğini her ikisi için de güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a684-110">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
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
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="3a684-111">Gerekli targetFramework özniteliğini ekleyin</span><span class="sxs-lookup"><span data-stu-id="3a684-111">Add the required targetFramework attribute</span></span>  
  
1. <span data-ttu-id="3a684-112">Hizmetin Web.config dosyasını açın ve <`compilation`> öğesini arayın.</span><span class="sxs-lookup"><span data-stu-id="3a684-112">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2. <span data-ttu-id="3a684-113">`targetFramework` `compilation` Aşağıdaki örnekte gösterildiği gibi özniteliği <> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a684-113">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
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
  
3. <span data-ttu-id="3a684-114"><`compilers`> öğesini bulun ve CompilerVersion sağlayıcısı seçeneğini 4,0 değerine sahip olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3a684-114">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="3a684-115">Varsayılan olarak, `compiler` <> öğesi altında iki <> öğesi vardır `compilers` .</span><span class="sxs-lookup"><span data-stu-id="3a684-115">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="3a684-116">Aşağıdaki örnekte gösterildiği gibi, CompilerVersion sağlayıcı seçeneğini her ikisi için de güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a684-116">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
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
