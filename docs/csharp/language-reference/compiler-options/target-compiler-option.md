---
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
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204512"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="f05a2-102">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f05a2-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="f05a2-103">**-Target** derleyici seçeneği dört formdan birinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="f05a2-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="f05a2-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="f05a2-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="f05a2-105">Windows 8. x Mağazası uygulamaları için bir. exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f05a2-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="f05a2-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="f05a2-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="f05a2-107">Bir. exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f05a2-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="f05a2-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="f05a2-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="f05a2-109">Bir kod kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f05a2-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="f05a2-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="f05a2-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="f05a2-111">Bir modül oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f05a2-111">To create a module.</span></span>  
  
 [<span data-ttu-id="f05a2-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="f05a2-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="f05a2-113">Bir Windows programı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f05a2-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="f05a2-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="f05a2-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="f05a2-115">Ara. winmdobj dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f05a2-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="f05a2-116">**-Target: Module**belirtmediğiniz takdirde **-target** bir .NET Framework derleme bildiriminin bir çıkış dosyasına yerleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f05a2-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="f05a2-117">Daha fazla bilgi için bkz. .NET ve [ortak özniteliklerde](../../programming-guide/concepts/attributes/common-attributes.md) [derlemeler](../../../standard/assembly/index.md) .</span><span class="sxs-lookup"><span data-stu-id="f05a2-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="f05a2-118">Derleme bildirimi, derleme içindeki ilk. exe çıkış dosyasına veya. exe çıkış dosyası yoksa ilk DLL 'de yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f05a2-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="f05a2-119">Örneğin, aşağıdaki komut satırında, bildirim `1.exe`yerleştirilecek:</span><span class="sxs-lookup"><span data-stu-id="f05a2-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="f05a2-120">Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f05a2-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="f05a2-121">Bir derlemedeki tüm dosyalar hakkındaki bilgiler, derleme bildirimine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f05a2-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="f05a2-122">**-Target: Module** ile oluşturulanlar hariç tüm çıkış dosyaları bir derleme bildirimi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f05a2-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="f05a2-123">Komut satırında birden çok çıkış dosyası üretilirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıkış dosyasına gitmelidir.</span><span class="sxs-lookup"><span data-stu-id="f05a2-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="f05a2-124">İlk çıkış dosyasının ne olduğuna bakılmaksızın ( **-target: exe**, **-target: winexe**, **-target: Library** veya **-target: Module**), aynı derlemede üretilen diğer çıkış dosyaları modüller olmalıdır ( **-target: Module**).</span><span class="sxs-lookup"><span data-stu-id="f05a2-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="f05a2-125">Bir derleme oluşturursanız, kodunuzun tümünün veya bir kısmının <xref:System.CLSCompliantAttribute> özniteliğiyle CLS uyumlu olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f05a2-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="f05a2-126">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="f05a2-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05a2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f05a2-127">See also</span></span>

- [<span data-ttu-id="f05a2-128">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f05a2-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f05a2-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="f05a2-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="f05a2-130">-subsystemversion (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f05a2-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
