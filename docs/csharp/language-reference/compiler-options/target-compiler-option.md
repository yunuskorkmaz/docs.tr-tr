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
ms.openlocfilehash: 073660fa732c04cdc987af5617b894a277ebcc0f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970123"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="7921e-102">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="7921e-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="7921e-103">**-Target** derleyici seçeneği dört formdan birinde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="7921e-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="7921e-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="7921e-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="7921e-105">Uygulamalar için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] bir. exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7921e-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="7921e-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="7921e-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="7921e-107">Bir. exe dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7921e-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="7921e-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="7921e-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="7921e-109">Bir kod kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7921e-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="7921e-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="7921e-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="7921e-111">Bir modül oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7921e-111">To create a module.</span></span>  
  
 [<span data-ttu-id="7921e-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="7921e-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="7921e-113">Bir Windows programı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7921e-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="7921e-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="7921e-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="7921e-115">Ara. winmdobj dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7921e-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="7921e-116">**-Target: Module**belirtmediğiniz takdirde **-target** bir .NET Framework derleme bildiriminin bir çıkış dosyasına yerleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7921e-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="7921e-117">Daha fazla bilgi için bkz. .NET ve [ortak özniteliklerde](../../programming-guide/concepts/attributes/common-attributes.md) [derlemeler](../../../standard/assembly/index.md) .</span><span class="sxs-lookup"><span data-stu-id="7921e-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="7921e-118">Derleme bildirimi, derleme içindeki ilk. exe çıkış dosyasına veya. exe çıkış dosyası yoksa ilk DLL 'de yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7921e-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="7921e-119">Örneğin, aşağıdaki komut satırında bildirim yerleştirilecek `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="7921e-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="7921e-120">Derleyici, derleme başına yalnızca bir derleme bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7921e-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="7921e-121">Bir derlemedeki tüm dosyalar hakkındaki bilgiler, derleme bildirimine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7921e-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="7921e-122">**-Target: Module** ile oluşturulanlar hariç tüm çıkış dosyaları bir derleme bildirimi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7921e-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="7921e-123">Komut satırında birden çok çıkış dosyası üretilirken, yalnızca bir derleme bildirimi oluşturulabilir ve komut satırında belirtilen ilk çıkış dosyasına gitmelidir.</span><span class="sxs-lookup"><span data-stu-id="7921e-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="7921e-124">İlk çıkış dosyasının ne olduğuna bakılmaksızın ( **-target: exe**, **-target: winexe**, **-target: Library** veya **-target: Module**), aynı derlemede üretilen diğer çıkış dosyaları modüller olmalıdır ( **-target: Module**).</span><span class="sxs-lookup"><span data-stu-id="7921e-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="7921e-125">Bir derleme oluşturursanız, kodunuzun tümünün veya bir kısmının <xref:System.CLSCompliantAttribute> öznitelik ile CLS uyumlu olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7921e-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="7921e-126">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için <xref:VSLangProj80.ProjectProperties3.OutputType%2A>bkz.</span><span class="sxs-lookup"><span data-stu-id="7921e-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7921e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7921e-127">See also</span></span>

- [<span data-ttu-id="7921e-128">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7921e-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7921e-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="7921e-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="7921e-130">-subsystemversion (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="7921e-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
