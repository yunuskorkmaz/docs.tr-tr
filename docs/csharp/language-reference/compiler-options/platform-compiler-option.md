---
title: "-platform (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d03e12ae60b9a0145dcb58765ae00f756f84ca56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="platform-c-compiler-options"></a><span data-ttu-id="73011-102">/platform (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="73011-102">/platform (C# Compiler Options)</span></span>
<span data-ttu-id="73011-103">Ortak dil çalışma zamanı (CLR) hangi sürümünün derlemeyi çalıştırabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73011-103">Specifies which version of the common language runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73011-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73011-104">Syntax</span></span>  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73011-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73011-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="73011-106">anycpu (varsayılan), anycpu32bitpreferred, ARM, x 64, x86 ya da Itanium.</span><span class="sxs-lookup"><span data-stu-id="73011-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73011-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73011-107">Remarks</span></span>  
  
-   <span data-ttu-id="73011-108">**anycpu** (varsayılan) herhangi bir platformda çalıştırmak için derleme derler.</span><span class="sxs-lookup"><span data-stu-id="73011-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="73011-109">Uygulamanız bir 64-bit işlem olarak mümkün olduğunda çalışır ve bu modu yalnızca 32-bit zaman geri döner.</span><span class="sxs-lookup"><span data-stu-id="73011-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="73011-110">**anycpu32bitpreferred** derlemenizi herhangi bir platformda çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="73011-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="73011-111">Uygulamanızı 32-bit modunda 64-bit ve 32-bit uygulamaları destekleyen sistemlerde çalışır.</span><span class="sxs-lookup"><span data-stu-id="73011-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="73011-112">.NET Framework 4.5 hedefleyen projeler için yalnızca bu seçenek belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73011-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="73011-113">**ARM** derlemenizi Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayarda çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="73011-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="73011-114">**x64** derlemenizi AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit ortak dil çalışma zamanı tarafından çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="73011-114">**x64** compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="73011-115">**x86** derlemenizi 32-bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="73011-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible common language runtime.</span></span>  
  
-   <span data-ttu-id="73011-116">**Itanium** derlemenizi 64-bit ortak dil çalışma zamanı tarafından Itanium işlemcili bir bilgisayarda çalıştırılması için.</span><span class="sxs-lookup"><span data-stu-id="73011-116">**Itanium** compiles your assembly to be run by the 64-bit common language runtime on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="73011-117">Bir 64-bit Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="73011-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="73011-118">Derlenmiş derlemeler **/platform:x 86** WOW64 altında çalışan 32 bit CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="73011-118">Assemblies compiled with **/platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="73011-119">DLL ile derlenmiş **/platform:anycpu** aynı CLR içine yüklendiği bir işlem olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="73011-119">A DLL compiled with the **/platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="73011-120">İle derlenmiş yürütülebilir dosyalar **/platform:anycpu** 64-bit CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="73011-120">Executables that are compiled with the **/platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="73011-121">Derlenmiş olan yürütülebilir dosyalar **/platform:anycpu32bitpreferred** 32-bit CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="73011-121">Executables compiled with **/platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="73011-122">**Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosyası için geçerlidir (. EXE) dosyaları ve .NET Framework 4.5 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="73011-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="73011-123">Bir Windows 64-bit işletim sisteminde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz: [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="73011-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="73011-124">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="73011-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="73011-125">Açık **özellikleri** projesi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="73011-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="73011-126">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="73011-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="73011-127">Değiştirme **Platform hedefi** özelliği ve .NET Framework 4.5 hedefleyen projeler seçin veya temizleyin **tercih 32-bit** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="73011-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="73011-128">**/ Platform Not** Visual C# Express geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="73011-128">**Note /platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="73011-129">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="73011-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73011-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="73011-130">Example</span></span>  
 <span data-ttu-id="73011-131">Aşağıdaki örnekte nasıl kullanılacağını gösterir **/Platform** seçeneği uygulamayı 64-bit CLR tarafından bir 64-bit Windows işletim sisteminde çalıştırılması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="73011-131">The following example shows how to use the **/platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="73011-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73011-132">See Also</span></span>  
 [<span data-ttu-id="73011-133">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="73011-133">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="73011-134">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="73011-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
