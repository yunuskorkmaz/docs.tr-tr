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
ms.openlocfilehash: ae2305e0f5d3ca4de386d8e7933a1107450e0be4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662562"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="1d2f2-102">-platform (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1d2f2-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="1d2f2-103">Hangi sürümü ortak dil çalışma zamanı (CLR), derleme çalıştırılıp belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d2f2-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d2f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d2f2-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="1d2f2-106">(varsayılan) anycpu, anycpu32bitpreferred, ARM, x 64, x86 ya da Itanium.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d2f2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d2f2-107">Remarks</span></span>  
  
- <span data-ttu-id="1d2f2-108">**anycpu** (varsayılan), derlemenizi herhangi bir platform üzerinde çalıştırmasını derler.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="1d2f2-109">Uygulamanız bir 64 bit işlem olarak mümkün olduğunda çalışır ve bu mod yalnızca 32-bit zaman geri döner.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
- <span data-ttu-id="1d2f2-110">**anycpu32bitpreferred** derlemenizi herhangi bir platformda çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="1d2f2-111">Uygulamanızı hem 64-bit ve 32-bit uygulamaları destekleyen sistemlerde 32-bit modunda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="1d2f2-112">.NET Framework 4.5 hedefleyen projeler için yalnızca bu seçeneği belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
- <span data-ttu-id="1d2f2-113">**ARM** derlemenizi Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayar üzerinde çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
- <span data-ttu-id="1d2f2-114">**ARM64** derlemenizi 64 bit CLR tarafından A64 yönerge kümesini destekleyen bir Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayar üzerinde çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>  

- <span data-ttu-id="1d2f2-115">**x64** derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayara 64 bit CLR tarafından çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
- <span data-ttu-id="1d2f2-116">**x86** derlemenizi 32-bit, x86 ile uyumlu bir CLR tarafından çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
- <span data-ttu-id="1d2f2-117">**Itanium** derlemenizi 64 bit CLR tarafından bir Itanium işlemci bir bilgisayarda çalıştırılması.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="1d2f2-118">Bir 64 bit Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="1d2f2-118">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="1d2f2-119">Derlenmiş derlemelerde **-platform: x 86** WOW64 altında çalışan 32 bitlik CLR üzerinde yürütün.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="1d2f2-120">Bir DLL ile derlenmiş **-platform: anycpu** içine yüklendiği işlem olarak aynı CLR üzerinde çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
- <span data-ttu-id="1d2f2-121">İle derlenen yürütülebilir dosyaları **-platform: anycpu** 64 bitlik CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="1d2f2-122">Yürütülebilir dosyalar ile derlenmiş olan **-platform: anycpu32bitpreferred** 32 bitlik CLR yürütün.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="1d2f2-123">**Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosya için geçerlidir (. EXE) dosyaları ve .NET Framework 4.5 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="1d2f2-124">Bir Windows 64-bit işletim sisteminde çalıştırılacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="1d2f2-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1d2f2-125">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1d2f2-125">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1d2f2-126">Açık **özellikleri** proje sayfası.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-126">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="1d2f2-127">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-127">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="1d2f2-128">Değiştirme **Platform hedefi** özelliği ve .NET Framework 4.5 hedefleyen projeler için seçin veya temizleyin **32 bit tercih et** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="1d2f2-129">**Not - platform** Visual C# Express geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-129">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="1d2f2-130">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2f2-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d2f2-131">Example</span></span>  
 <span data-ttu-id="1d2f2-132">Aşağıdaki örnek nasıl kullanılacağını gösterir **-platform** uygulama 64 bitlik CLR tarafından bir 64 bit Windows işletim sisteminde çalıştırılması gerektiğini belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d2f2-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d2f2-133">See also</span></span>

- [<span data-ttu-id="1d2f2-134">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1d2f2-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="1d2f2-135">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="1d2f2-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
