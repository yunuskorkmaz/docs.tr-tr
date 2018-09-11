---
title: -out (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: ea371dc968c8d8bf1569d17531cf7f6faff1d315
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277134"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="be2b6-102">-out (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="be2b6-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="be2b6-103">**-Out** seçeneği, çıkış dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be2b6-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be2b6-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="be2b6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="be2b6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="be2b6-106">Derleyici tarafından oluşturulan çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="be2b6-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be2b6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be2b6-107">Remarks</span></span>  
 <span data-ttu-id="be2b6-108">Komut satırında, derleme için birden çok çıktı dosyaları belirtmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="be2b6-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="be2b6-109">Aşağıdaki bir veya daha fazla kaynak kodu dosyaları bulmak derleyici bekliyor **-out** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="be2b6-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="be2b6-110">Ardından, tüm kaynak kodu dosyaları tarafından belirtilen çıkış dosyası içine derlenecek **-out** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="be2b6-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="be2b6-111">Oluşturmak istediğiniz dosyanın uzantısı ve tam adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="be2b6-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="be2b6-112">Çıkış dosyasının adı belirtmezseniz:</span><span class="sxs-lookup"><span data-stu-id="be2b6-112">If you do not specify the name of the output file:</span></span>  
  
-   <span data-ttu-id="be2b6-113">Bir .exe içeren kaynak kod dosyasının adı sürer **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="be2b6-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
-   <span data-ttu-id="be2b6-114">Bir .dll veya .netmodule adı ilk kaynak kod dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="be2b6-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="be2b6-115">Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyası aynı derlemede başka bir çıkış dosyası derleme için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="be2b6-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="be2b6-116">Bir komut satırı derlemede birden fazla çıktı dosyası üretilirken bir derleme çıktı dosyalarını yalnızca biri olabilir ve yalnızca ilk çıktı dosyası belirtilen göz önünde bulundurun (örtük veya açık olarak ile **-out**) derleme olabilir .</span><span class="sxs-lookup"><span data-stu-id="be2b6-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="be2b6-117">Bir derlemenin bir parçası oluşturulan bağladığımız modüllerin de derlemede üretilen herhangi bir derleme ile ilişkili dosyaları haline gelir.</span><span class="sxs-lookup"><span data-stu-id="be2b6-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="be2b6-118">Kullanım [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) ilişkili dosyaları görmek için derleme bildirimi görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="be2b6-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="be2b6-119">-Out derleyici seçeneği, bir arkadaş derleme hedefi bir exe sırayla gereklidir.</span><span class="sxs-lookup"><span data-stu-id="be2b6-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="be2b6-120">Daha fazla bilgi için [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="be2b6-120">For more information see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="be2b6-121">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="be2b6-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="be2b6-122">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="be2b6-122">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="be2b6-123">Tıklayın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="be2b6-123">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="be2b6-124">Değiştirme **derleme adı** özelliği.</span><span class="sxs-lookup"><span data-stu-id="be2b6-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="be2b6-125">Bu derleyici seçeneğini program üzerinden ayarlamak için: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> bir proje türü (exe, kitaplık ve diğerleri) ve derleme adı birleşimi tarafından belirlenen bir salt okunur özelliği.</span><span class="sxs-lookup"><span data-stu-id="be2b6-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="be2b6-126">Birini veya her ikisini bu özellikleri değiştirerek çıkış dosyası adını ayarlamak gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="be2b6-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be2b6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="be2b6-127">Example</span></span>  
 <span data-ttu-id="be2b6-128">Derleme `t.cs` ve çıkış dosyası oluşturmak `t.exe`, derleme yanı sıra `t2.cs` ve modül çıkış dosyası oluşturma `mymodule.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="be2b6-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="be2b6-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be2b6-129">See Also</span></span>  

- [<span data-ttu-id="be2b6-130">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="be2b6-130">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="be2b6-131">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="be2b6-131">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [<span data-ttu-id="be2b6-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="be2b6-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
