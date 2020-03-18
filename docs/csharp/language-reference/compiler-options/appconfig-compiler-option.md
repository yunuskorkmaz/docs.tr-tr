---
title: -appconfig (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922517"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="ce594-102">-appconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ce594-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="ce594-103">**-appconfig** derleyici seçeneği, bir C# uygulamasının derleme bağlama zamanında ortak dil çalışma süresine (CLR) bir derlemenin uygulama yapılandırması (app.config) dosyasının konumunu belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce594-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce594-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce594-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce594-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ce594-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="ce594-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ce594-106">Required.</span></span> <span data-ttu-id="ce594-107">Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="ce594-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce594-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce594-108">Remarks</span></span>  
 <span data-ttu-id="ce594-109">**-appconfig'in** bir kullanımı, bir derlemenin hem .NET Framework sürümüne hem de belirli bir başvuru derlemesinin Silverlight için .NET Framework sürümüne aynı anda başvurmak zorunda olduğu gelişmiş senaryolardır.</span><span class="sxs-lookup"><span data-stu-id="ce594-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="ce594-110">Örneğin, Windows Sunu Vakfı'nda (WPF) yazılmış bir XAML tasarımcısının, tasarımcının kullanıcı arabirimi için hem WPF Masaüstü'ne hem de Silverlight ile birlikte verilen WPF alt kümesine başvurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ce594-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="ce594-111">Aynı tasarımcı derlemesi her iki derlemeye de erişmek zorundadır.</span><span class="sxs-lookup"><span data-stu-id="ce594-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="ce594-112">Derleme bağlama iki derlemeyi eşdeğer olarak gördüğünden, varsayılan olarak, ayrı başvurular derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ce594-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="ce594-113">**-appconfig** derleyici seçeneği, aşağıdaki örnekte gösterildiği gibi, bir `<supportPortability>` etiket kullanarak varsayılan davranışı devre dışı düşüren bir app.config dosyasının konumunu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce594-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="ce594-114">Derleyici, dosyanın konumunu CLR'nin derleme bağlama mantığına geçirir.</span><span class="sxs-lookup"><span data-stu-id="ce594-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce594-115">Uygulamanızı oluşturmak için Microsoft Build Engine 'i (MSBuild) kullanıyorsanız, .csproj dosyasına bir özellik etiketi ekleyerek **-appconfig** derleyicisi seçeneğini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce594-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="ce594-116">Projede zaten ayarlanmış olan app.config dosyasını kullanmak `<UseAppConfigForCompiler>` için ,.csproj dosyasına özellik `true`etiketi ekleyin ve değerini .</span><span class="sxs-lookup"><span data-stu-id="ce594-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="ce594-117">Farklı bir app.config dosyası belirtmek `<AppConfigForCompiler>` için özellik etiketi ekleyin ve değerini dosyanın konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ce594-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce594-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce594-118">Example</span></span>  
 <span data-ttu-id="ce594-119">Aşağıdaki örnek, bir uygulamanın hem .NET Framework uygulamasına hem de .NET Framework derlemesinde var olan herhangi bir .NET Framework derlemesinin Silverlight uygulamasına atıfta bulunmasını sağlayan bir app.config dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce594-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="ce594-120">**-appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce594-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ce594-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce594-121">See also</span></span>

- [<span data-ttu-id="ce594-122">\<destekTaşınabilirlik> Elemanı</span><span class="sxs-lookup"><span data-stu-id="ce594-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="ce594-123">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ce594-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
