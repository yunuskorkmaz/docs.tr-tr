---
title: -hedef (C# Derleyici Seçenekleri)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204512"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="08966-102">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="08966-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="08966-103">**-hedef** derleyici seçeneği dört formdan birinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="08966-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="08966-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="08966-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="08966-105">Windows 8.x Store uygulamaları için bir .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="08966-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="08966-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="08966-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="08966-107">Bir .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="08966-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="08966-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="08966-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="08966-109">Kod kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="08966-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="08966-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="08966-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="08966-111">Bir modül oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="08966-111">To create a module.</span></span>  
  
 [<span data-ttu-id="08966-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="08966-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="08966-113">Bir Windows programı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="08966-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="08966-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="08966-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="08966-115">Bir ara .winmdobj dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="08966-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="08966-116">**-target:module**, -target belirtmediğiniz sürece **hedef,** bir çıktı dosyasına bir .NET Framework derleme bildiriminin yerleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="08966-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="08966-117">Daha fazla bilgi için .NET ve [Ortak Özniteliklerdeki](../../programming-guide/concepts/attributes/common-attributes.md) [Derlemeler'e](../../../standard/assembly/index.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="08966-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="08966-118">Derleme bildirimi derlemedeki ilk .exe çıktı dosyasına veya .exe çıktı dosyası yoksa ilk DLL'ye yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="08966-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="08966-119">Örneğin, aşağıdaki komut satırında, bildirim `1.exe`yerleştirilir:</span><span class="sxs-lookup"><span data-stu-id="08966-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="08966-120">Derleyici derleme başına yalnızca bir derleme bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08966-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="08966-121">Derlemedeki tüm dosyalar la ilgili bilgiler derleme manifestosuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="08966-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="08966-122">**-target:module** ile oluşturulanlar dışındaki tüm çıktı dosyaları bir derleme bildirimi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="08966-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="08966-123">Komut satırında birden çok çıktı dosyası oluşturulurken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıktı dosyasına geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="08966-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="08966-124">İlk çıktı dosyası ne olursa olsun (**-hedef:exe**, **-target:winexe**, **-target:library** veya **-target:module**), aynı derlemede üretilen diğer çıktı dosyaları modüller olmalıdır (**-target:module**).</span><span class="sxs-lookup"><span data-stu-id="08966-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="08966-125">Bir derleme oluşturursanız, kodunuzun tamamının veya bir kısmının ÖZnitelikile <xref:System.CLSCompliantAttribute> CLS uyumlu olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08966-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="08966-126">Bu derleyici seçeneğini programlı olarak ayarlama <xref:VSLangProj80.ProjectProperties3.OutputType%2A>hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="08966-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08966-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08966-127">See also</span></span>

- [<span data-ttu-id="08966-128">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="08966-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="08966-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="08966-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="08966-130">-alt sistem versiyonu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="08966-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
