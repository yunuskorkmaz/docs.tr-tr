---
title: -platform (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 1573e28f2a6f9dec7825d364debcdf1085ef7ff2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635673"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="5ee98-102">-platform (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5ee98-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="5ee98-103">Hangi sürümü ortak dil çalışma zamanı (CLR), derleme çalıştırılıp belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ee98-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ee98-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ee98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ee98-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="5ee98-106">(varsayılan) anycpu, anycpu32bitpreferred, ARM, x 64, x86 ya da Itanium.</span><span class="sxs-lookup"><span data-stu-id="5ee98-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ee98-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ee98-107">Remarks</span></span>  
  
-   <span data-ttu-id="5ee98-108">**anycpu** (varsayılan), derlemenizi herhangi bir platform üzerinde çalıştırmasını derler.</span><span class="sxs-lookup"><span data-stu-id="5ee98-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="5ee98-109">Uygulamanız bir 64 bit işlem olarak mümkün olduğunda çalışır ve bu mod yalnızca 32-bit zaman geri döner.</span><span class="sxs-lookup"><span data-stu-id="5ee98-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="5ee98-110">**anycpu32bitpreferred** derlemenizi herhangi bir platformda çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="5ee98-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="5ee98-111">Uygulamanızı hem 64-bit ve 32-bit uygulamaları destekleyen sistemlerde 32-bit modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5ee98-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="5ee98-112">.NET Framework 4.5 hedefleyen projeler için yalnızca bu seçeneği belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ee98-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="5ee98-113">**ARM** derlemenizi Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayar üzerinde çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="5ee98-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="5ee98-114">**x64** derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayara 64 bit CLR tarafından çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="5ee98-114">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="5ee98-115">**x86** derlemenizi 32-bit, x86 ile uyumlu bir CLR tarafından çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="5ee98-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="5ee98-116">**Itanium** derlemenizi 64 bit CLR tarafından bir Itanium işlemci bir bilgisayarda çalıştırılması.</span><span class="sxs-lookup"><span data-stu-id="5ee98-116">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="5ee98-117">Bir 64 bit Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="5ee98-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="5ee98-118">Derlenmiş derlemelerde **-platform: x 86** WOW64 altında çalışan 32 bitlik CLR üzerinde yürütün.</span><span class="sxs-lookup"><span data-stu-id="5ee98-118">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="5ee98-119">Bir DLL ile derlenmiş **-platform: anycpu** içine yüklendiği işlem olarak aynı CLR üzerinde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5ee98-119">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="5ee98-120">İle derlenen yürütülebilir dosyaları **-platform: anycpu** 64 bitlik CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="5ee98-120">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="5ee98-121">Yürütülebilir dosyalar ile derlenmiş olan **-platform: anycpu32bitpreferred** 32 bitlik CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="5ee98-121">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="5ee98-122">**Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosya için geçerlidir (. EXE) dosyaları ve .NET Framework 4.5 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5ee98-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="5ee98-123">Bir Windows 64-bit işletim sisteminde çalıştırılacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="5ee98-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5ee98-124">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5ee98-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="5ee98-125">Açık **özellikleri** proje sayfası.</span><span class="sxs-lookup"><span data-stu-id="5ee98-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="5ee98-126">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="5ee98-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="5ee98-127">Değiştirme **Platform hedefi** özelliği ve .NET Framework 4.5 hedefleyen projeler için seçin veya temizleyin **32 bit tercih et** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="5ee98-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="5ee98-128">**Not - platform** Visual C# Express geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ee98-128">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="5ee98-129">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ee98-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee98-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ee98-130">Example</span></span>  
 <span data-ttu-id="5ee98-131">Aşağıdaki örnek nasıl kullanılacağını gösterir **-platform** uygulama 64 bitlik CLR tarafından bir 64 bit Windows işletim sisteminde çalıştırılması gerektiğini belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5ee98-131">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ee98-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee98-132">See also</span></span>

- [<span data-ttu-id="5ee98-133">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5ee98-133">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="5ee98-134">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5ee98-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
