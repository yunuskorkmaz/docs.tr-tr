---
description: -Platform (C# derleyici seçenekleri)
title: -Platform (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 3fdb030dfc141b011f5faa827a4e4bb45ae38d19
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466020"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="8a971-103">-Platform (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="8a971-103">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="8a971-104">Ortak dil çalışma zamanının (CLR) hangi sürümünün derlemeyi çalıştırabileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a971-104">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a971-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a971-105">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="8a971-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a971-106">Parameters</span></span>

`string` \
<span data-ttu-id="8a971-107">anycpu (varsayılan), anycpu32bitpreferred, ARM, x64, x86 veya Itanium.</span><span class="sxs-lookup"><span data-stu-id="8a971-107">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a971-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a971-108">Remarks</span></span>

- <span data-ttu-id="8a971-109">**anycpu** (varsayılan), derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-109">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="8a971-110">Uygulamanız mümkün olduğunda 64 bitlik bir işlem olarak çalışır ve yalnızca bu mod kullanılabilir olduğunda 32 bit 'e geri döner.</span><span class="sxs-lookup"><span data-stu-id="8a971-110">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="8a971-111">**anycpu32bitpreferred** , derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-111">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="8a971-112">Uygulamanız, hem 64 bit hem de 32 bit uygulamaları destekleyen sistemlerde 32 bitlik modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="8a971-112">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="8a971-113">Bu seçeneği yalnızca .NET Framework 4,5 veya üstünü hedefleyen projeler için belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a971-113">You can specify this option only for projects that target .NET Framework 4.5 or later.</span></span>

- <span data-ttu-id="8a971-114">**ARM** , derlemenizi GELIŞMIŞ bir RISC MAKINESI (ARM) işlemcisi olan bir bilgisayarda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-114">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="8a971-115">**ARM64** , derlemenizi, A64 yönerge kümesini destekleyen GELIŞMIŞ bir RISC MAKINESI (ARM) işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-115">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="8a971-116">**x64** , derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-116">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="8a971-117">**x86** , derlemenizi 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-117">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="8a971-118">**Itanium** , derlemenizi Itanium işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="8a971-118">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="8a971-119">64 bitlik bir Windows işletim sisteminde:</span><span class="sxs-lookup"><span data-stu-id="8a971-119">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="8a971-120">İle derlenen derlemeler **-Platform: x86** , WOW64 altında çalışan 32 bitlik clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8a971-120">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="8a971-121">**-Platform: anycpu** ile derlenen bir dll, yüklendiği IŞLEMLE aynı CLR üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8a971-121">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="8a971-122">**-Platform: anycpu** ile derlenen yürütülebilir dosyalar 64 bitlik clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8a971-122">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="8a971-123">**-Platform: anycpu32bitpreferred** ile derlenen yürütülebilir dosyalar 32 bit clr üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8a971-123">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="8a971-124">**Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosya için geçerlidir (. EXE) dosyalarını ve .NET Framework 4,5 veya üzeri bir sürümü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a971-124">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires .NET Framework 4.5 or later.</span></span>

<span data-ttu-id="8a971-125">Windows 64 bit işletim sisteminde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8a971-125">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8a971-126">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8a971-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="8a971-127">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="8a971-127">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="8a971-128">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8a971-128">Click the **Build** property page.</span></span>

3. <span data-ttu-id="8a971-129">**Platform hedefi** özelliğini değiştirin ve .NET Framework 4,5 veya sonraki bir sürümü hedefleyen projeler için **32 bit tercih** et onay kutusunu seçin veya temizleyin.</span><span class="sxs-lookup"><span data-stu-id="8a971-129">Modify the **Platform target** property and, for projects that target .NET Framework 4.5 or later, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="8a971-130">`-platform` Visual C# Express 'teki geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8a971-130">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="8a971-131">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A> ..</span><span class="sxs-lookup"><span data-stu-id="8a971-131">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="8a971-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a971-132">Example</span></span>

<span data-ttu-id="8a971-133">Aşağıdaki örnek, uygulamanın 64 bitlik bir Windows işletim sisteminde 64 bitlik CLR tarafından çalıştırılması gerektiğini belirtmek için **-Platform** seçeneğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a971-133">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="8a971-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a971-134">See also</span></span>

- [<span data-ttu-id="8a971-135">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8a971-135">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="8a971-136">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="8a971-136">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
