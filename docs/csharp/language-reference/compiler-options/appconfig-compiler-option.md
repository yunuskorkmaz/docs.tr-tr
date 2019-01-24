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
ms.openlocfilehash: 102ed3977d56ace0dab63b1f066cc10a6fc5dfbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514068"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="7c3dd-102">-appconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="7c3dd-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="7c3dd-103">**- Appconfig** derleyici seçeneği, derleme bağlama zamanında ortak dil çalışma zamanı (CLR) için bir derlemenin uygulama yapılandırma (app.config) dosyasının konumunu belirtmek bir C# uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c3dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c3dd-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="7c3dd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7c3dd-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="7c3dd-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-106">Required.</span></span> <span data-ttu-id="7c3dd-107">Derleme bağlama ayarlarını içeren uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c3dd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c3dd-108">Remarks</span></span>  
 <span data-ttu-id="7c3dd-109">Bir kullanımını **- appconfig** senaryolarında bir derleme bulunduğu hem .NET Framework sürümü hem de Silverlight sürümü aynı anda belirli bir başvuru bütünleştirilmiş kodu için .NET Framework başvurmak Gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="7c3dd-110">Örneğin, Windows Presentation Foundation (WPF) yazılı bir XAML tasarımcının hem WPF Masaüstü Tasarımcısı kullanıcı arabirimi ve Silverlight ile gelen WPF alt kümesi için başvuru gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="7c3dd-111">Tasarımcı aynı derlemenin iki derleme erişmelidir.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="7c3dd-112">Varsayılan olarak, derleme bağlama iki derlemeyi eşdeğer olarak gördüğünden ayrı başvurular bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="7c3dd-113">**- Appconfig** derleyici seçeneği kullanılarak varsayılan davranışı devre dışı bırakan bir app.config dosyasının konumunu belirtmenize imkan tanır bir `<supportPortability>` , aşağıdaki örnekte gösterildiği gibi etiketleyin.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="7c3dd-114">Derleyici dosyasının konumu CLR'ın derleme bağlama mantığına geçirir.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c3dd-115">Uygulamanızı oluşturmak üzere Microsoft Build Engine (MSBuild) kullanıyorsanız, ayarlayabileceğiniz **- appconfig** için .csproj dosyasını bir özellik etiketi ekleyerek derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="7c3dd-116">Projede zaten ayarlanmış ve app.config dosyasında kullanılacak özellik etiketi ekleyin `<UseAppConfigForCompiler>` için .csproj dosyasını ve değerini ayarlamak `true`.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="7c3dd-117">Farklı bir app.config dosyası belirtmek için özellik etiketi ekleyin `<AppConfigForCompiler>` ve dosya konumuna değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c3dd-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c3dd-118">Example</span></span>  
 <span data-ttu-id="7c3dd-119">Aşağıdaki örnek bir uygulama hem .NET Framework uygulamasına hem de her iki uygulamada da bulunan herhangi bir .NET Framework derlemesinin Silverlight için .NET Framework başvuru sağlayan bir app.config dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="7c3dd-120">**- Appconfig** derleyici seçeneği bu app.config dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c3dd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c3dd-121">See also</span></span>

- [<span data-ttu-id="7c3dd-122">\<supportPortability > öğesi</span><span class="sxs-lookup"><span data-stu-id="7c3dd-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="7c3dd-123">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7c3dd-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
