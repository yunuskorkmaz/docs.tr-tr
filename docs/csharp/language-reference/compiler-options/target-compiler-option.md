---
description: -target (C# derleyici seçenekleri)
title: -target (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: bcae4b64bdd2a939e35666a9068611b273c261da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188427"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="47b8f-103">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="47b8f-103">-target (C# Compiler Options)</span></span>

<span data-ttu-id="47b8f-104">**-Target** derleyici seçeneği aşağıdaki biçimlerden birinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="47b8f-104">The **-target** compiler option can be specified in one of the following forms:</span></span>  
  
 [<span data-ttu-id="47b8f-105">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="47b8f-105">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="47b8f-106">Windows 8. x Mağazası uygulamaları için bir. exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="47b8f-106">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="47b8f-107">-target:exe</span><span class="sxs-lookup"><span data-stu-id="47b8f-107">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="47b8f-108">Bir. exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="47b8f-108">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="47b8f-109">-target:library</span><span class="sxs-lookup"><span data-stu-id="47b8f-109">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="47b8f-110">Bir kod kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47b8f-110">To create a code library.</span></span>  
  
 [<span data-ttu-id="47b8f-111">-target:module</span><span class="sxs-lookup"><span data-stu-id="47b8f-111">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="47b8f-112">Bir modül oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="47b8f-112">To create a module.</span></span>  
  
 [<span data-ttu-id="47b8f-113">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="47b8f-113">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="47b8f-114">Bir Windows programı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="47b8f-114">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="47b8f-115">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="47b8f-115">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="47b8f-116">Ara. winmdobj dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="47b8f-116">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="47b8f-117">**-Target: Module**belirtmediğiniz takdirde **-target** bir .NET Framework derleme bildiriminin bir çıkış dosyasına yerleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="47b8f-117">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="47b8f-118">Daha fazla bilgi için bkz. .NET ve [ortak özniteliklerde](../attributes/global.md) [derlemeler](../../../standard/assembly/index.md) .</span><span class="sxs-lookup"><span data-stu-id="47b8f-118">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="47b8f-119">Derleme bildirimi, derleme içindeki ilk. exe çıkış dosyasına veya. exe çıkış dosyası yoksa ilk DLL 'de yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="47b8f-119">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="47b8f-120">Örneğin, aşağıdaki komut satırında bildirim yerleştirilecek `1.exe` :</span><span class="sxs-lookup"><span data-stu-id="47b8f-120">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="47b8f-121">Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47b8f-121">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="47b8f-122">Bir derlemedeki tüm dosyalar hakkındaki bilgiler, derleme bildirimine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="47b8f-122">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="47b8f-123">**-Target: Module** ile oluşturulanlar hariç tüm çıkış dosyaları bir derleme bildirimi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="47b8f-123">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="47b8f-124">Komut satırında birden çok çıkış dosyası üretilirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıkış dosyasına gitmelidir.</span><span class="sxs-lookup"><span data-stu-id="47b8f-124">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="47b8f-125">İlk çıkış dosyasının ne olduğuna bakılmaksızın (**-target: exe**, **-target: winexe**, **-target: Library** veya **-target: Module**), aynı derlemede üretilen diğer çıkış dosyaları modüller olmalıdır (**-target: Module**).</span><span class="sxs-lookup"><span data-stu-id="47b8f-125">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="47b8f-126">Bir derleme oluşturursanız, kodunuzun tümünün veya bir kısmının öznitelik ile CLS uyumlu olduğunu belirtebilirsiniz <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="47b8f-126">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="47b8f-127">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..</span><span class="sxs-lookup"><span data-stu-id="47b8f-127">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b8f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47b8f-128">See also</span></span>

- [<span data-ttu-id="47b8f-129">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="47b8f-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="47b8f-130">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="47b8f-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="47b8f-131">-subsystemversion (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="47b8f-131">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
