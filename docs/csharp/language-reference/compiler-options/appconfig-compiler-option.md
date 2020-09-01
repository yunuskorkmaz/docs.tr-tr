---
description: -appconfig (C# derleyici seçenekleri)
title: -appconfig (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 287d41105199057add1dad78d480b083adb745b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126118"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="ac23f-103">-appconfig (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ac23f-103">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="ac23f-104">**-Appconfig** derleyici seçeneği, bir C# uygulamasının derleme bağlama süresinde ortak dil çalışma zamanına (CLR) bir derlemenin uygulama yapılandırma (app.config) dosyasının konumunu belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac23f-104">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac23f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac23f-105">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac23f-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ac23f-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="ac23f-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ac23f-107">Required.</span></span> <span data-ttu-id="ac23f-108">Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="ac23f-108">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac23f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac23f-109">Remarks</span></span>  
 <span data-ttu-id="ac23f-110">Tek **appconfig** 'in kullanımı, bir derlemenin hem .NET Framework sürümüne hem de aynı anda belirli bir başvuru derlemesinin Silverlight sürümüne .NET Framework başvurması gereken gelişmiş senaryolardır.</span><span class="sxs-lookup"><span data-stu-id="ac23f-110">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="ac23f-111">Örneğin, Windows Presentation Foundation (WPF) içinde yazılmış bir XAML tasarımcısının, tasarımcı 'nın Kullanıcı arabirimi için hem WPF masaüstüne hem de Silverlight 'ın içerdiği WPF 'nin alt kümesine başvurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ac23f-111">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="ac23f-112">Aynı tasarımcı derlemesinin her iki derlemeye de erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="ac23f-112">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="ac23f-113">Varsayılan olarak, derleme bağlaması iki derlemeyi eşdeğer olarak gördüğü için ayrı başvurular bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ac23f-113">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="ac23f-114">**-Appconfig** derleyici seçeneği, `<supportPortability>` Aşağıdaki örnekte gösterildiği gibi bir etiketi kullanarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac23f-114">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="ac23f-115">Derleyici, dosyanın konumunu CLR 'nin derleme bağlama mantığına geçirir.</span><span class="sxs-lookup"><span data-stu-id="ac23f-115">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac23f-116">Uygulamanızı derlemek için Microsoft Build Engine (MSBuild) kullanıyorsanız,. csproj dosyasına bir özellik etiketi ekleyerek **-appconfig** derleyici seçeneğini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac23f-116">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="ac23f-117">Projede zaten ayarlanmış olan app.config dosyasını kullanmak için, `<UseAppConfigForCompiler>` . csproj dosyasına özellik etiketi ekleyin ve değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="ac23f-117">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="ac23f-118">Farklı bir app.config dosyası belirtmek için, özellik etiketi ekleyin `<AppConfigForCompiler>` ve değerini dosyanın konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ac23f-118">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac23f-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac23f-119">Example</span></span>  
 <span data-ttu-id="ac23f-120">Aşağıdaki örnek, bir uygulamanın hem .NET Framework .NET Framework uygulamasına hem de her iki uygulamada bulunan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına yönelik başvurularına sahip olmasını sağlayan bir app.config dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac23f-120">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="ac23f-121">**-Appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac23f-121">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac23f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac23f-122">See also</span></span>

- [<span data-ttu-id="ac23f-123">\<supportPortability> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ac23f-123">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="ac23f-124">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ac23f-124">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
