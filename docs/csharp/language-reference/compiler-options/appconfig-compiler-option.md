---
title: -appconfig (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922517"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="48feb-102">-appconfig (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="48feb-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="48feb-103">**-Appconfig** derleyici seçeneği, bir C# uygulamanın derlemenin uygulama yapılandırma (App. config) dosyasının konumunu derleme bağlama sırasında ortak DIL çalışma zamanı (CLR) olarak belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48feb-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48feb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48feb-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="48feb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="48feb-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="48feb-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="48feb-106">Required.</span></span> <span data-ttu-id="48feb-107">Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="48feb-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48feb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48feb-108">Remarks</span></span>  
 <span data-ttu-id="48feb-109">Tek **appconfig** 'in kullanımı, bir derlemenin hem .NET Framework sürümüne hem de aynı anda belirli bir başvuru derlemesinin Silverlight sürümüne .NET Framework başvurması gereken gelişmiş senaryolardır.</span><span class="sxs-lookup"><span data-stu-id="48feb-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="48feb-110">Örneğin, Windows Presentation Foundation (WPF) içinde yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF masaüstüne hem de Silverlight 'ın içerdiği WPF 'nin alt kümesine başvurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="48feb-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="48feb-111">Aynı tasarımcı derlemesinin her iki derlemeye de erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="48feb-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="48feb-112">Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="48feb-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="48feb-113">**-Appconfig** derleyici seçeneği, aşağıdaki örnekte gösterildiği gibi bir `<supportPortability>` etiketi kullanarak varsayılan davranışı devre dışı bırakan bir App. config dosyasının konumunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="48feb-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="48feb-114">Derleyici, dosyanın konumunu CLR 'nin derleme bağlama mantığına geçirir.</span><span class="sxs-lookup"><span data-stu-id="48feb-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48feb-115">Uygulamanızı derlemek için Microsoft Build Engine (MSBuild) kullanıyorsanız,. csproj dosyasına bir özellik etiketi ekleyerek **-appconfig** derleyici seçeneğini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48feb-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="48feb-116">Projede zaten ayarlanmış olan App. config dosyasını kullanmak için,. csproj dosyasına özellik etiketi `<UseAppConfigForCompiler>` ekleyin ve değerini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48feb-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="48feb-117">Farklı bir App. config dosyası belirtmek için, özellik etiketi `<AppConfigForCompiler>` ekleyin ve değerini dosyanın konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48feb-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48feb-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="48feb-118">Example</span></span>  
 <span data-ttu-id="48feb-119">Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına .NET Framework başvurularına sahip olmasını sağlayan bir App. config dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="48feb-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="48feb-120">**-Appconfig** derleyici seçeneği bu app. config dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="48feb-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48feb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48feb-121">See also</span></span>

- [<span data-ttu-id="48feb-122">\<Supporttaşınabilirlik > öğesi</span><span class="sxs-lookup"><span data-stu-id="48feb-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="48feb-123">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="48feb-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
