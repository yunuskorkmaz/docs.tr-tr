---
title: -target (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: a337ecbc614ff40eda42fc5263dbb52aa92b905f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874133"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="de7d8-102">-target (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="de7d8-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="de7d8-103">**-Hedef** derleyici seçeneği dört biçimlerden birinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="de7d8-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="de7d8-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="de7d8-104">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="de7d8-105">Bir .exe dosyası oluşturmak için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="de7d8-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="de7d8-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="de7d8-106">-target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="de7d8-107">Bir .exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="de7d8-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="de7d8-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="de7d8-108">-target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="de7d8-109">Bir kod kitaplığı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="de7d8-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="de7d8-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="de7d8-110">-target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="de7d8-111">Bir modül oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="de7d8-111">To create a module.</span></span>  
  
 [<span data-ttu-id="de7d8-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="de7d8-112">-target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="de7d8-113">Bir Windows programı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="de7d8-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="de7d8-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="de7d8-114">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="de7d8-115">Bir ara .winmdobj dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="de7d8-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="de7d8-116">Siz belirtmediğiniz sürece **-target: module**, **-hedef** bir .NET Framework derleme bildirimi bir çıkış dosyası yerleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="de7d8-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="de7d8-117">Daha fazla bilgi için [ortak dil çalışma zamanı derlemeleri](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) ve [ortak öznitelikleri](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="de7d8-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="de7d8-118">.Exe çıkış dosyası yoksa derleme bildirimi ilk .exe çıkış dosyası derleme veya ilk DLL yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de7d8-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="de7d8-119">Örneğin, aşağıdaki komut satırında bildirim yerleştirileceği `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="de7d8-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="de7d8-120">Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de7d8-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="de7d8-121">Bir derlemede tüm dosyaları hakkında bilgi, derleme bildirimine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de7d8-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="de7d8-122">Tüm dosyaları ile oluşturulanlar dışındaki çıktı **-target: module** bir derleme bildirimi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="de7d8-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="de7d8-123">Komut satırında birden çok çıkış dosyaları üreten, tek bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıktı dosyası içine gitmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de7d8-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="de7d8-124">Hangi ilk çıktı dosyası ne olursa olsun (**-target: exe**, **-target: winexe**, **-target: library** veya **-target: module**), diğer aynı derlemede üretilen Çıkış dosyalarını modülleri olmalıdır (**-target: module**).</span><span class="sxs-lookup"><span data-stu-id="de7d8-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="de7d8-125">Bir derlemeyi oluşturursanız, kodunuzun bir kısmını veya tamamını CLS ile uyumlu olduğunu gösterebilir <xref:System.CLSCompliantAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="de7d8-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="de7d8-126">Bu derleyici seçeneğini programlama yoluyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="de7d8-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7d8-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de7d8-127">See Also</span></span>  

- [<span data-ttu-id="de7d8-128">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="de7d8-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="de7d8-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="de7d8-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
- [<span data-ttu-id="de7d8-130">-subsystemversion (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="de7d8-130">-subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
