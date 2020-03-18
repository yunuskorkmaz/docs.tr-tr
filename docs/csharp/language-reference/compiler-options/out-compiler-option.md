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
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970373"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="2e79e-102">-out (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2e79e-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="2e79e-103">**-out** seçeneği çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e79e-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e79e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e79e-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e79e-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2e79e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2e79e-106">Derleyici tarafından oluşturulan çıktı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="2e79e-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e79e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e79e-107">Remarks</span></span>  
 <span data-ttu-id="2e79e-108">Komut satırında, derlemeniz için birden çok çıktı dosyası belirtmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2e79e-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="2e79e-109">**Derleyici- out** seçeneğini izleyen bir veya daha fazla kaynak kodu dosyasını bulmayı bekler.</span><span class="sxs-lookup"><span data-stu-id="2e79e-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="2e79e-110">Daha sonra, tüm kaynak kodu dosyaları bu **-out** seçeneği tarafından belirtilen çıktı dosyasına derlenir.</span><span class="sxs-lookup"><span data-stu-id="2e79e-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="2e79e-111">Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="2e79e-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="2e79e-112">Çıktı dosyasının adını belirtmezseniz:</span><span class="sxs-lookup"><span data-stu-id="2e79e-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="2e79e-113">Bir .exe adını **Ana** yöntemi içeren kaynak kod dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="2e79e-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="2e79e-114">Bir .dll veya .netmodule adını ilk kaynak kodu dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="2e79e-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="2e79e-115">Bir çıktı dosyasını derlemek için kullanılan bir kaynak kodu dosyası, başka bir çıktı dosyasının derlemesi için aynı derlemede kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e79e-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="2e79e-116">Komut satırı derlemesinde birden çok çıktı dosyası üretirken, çıktı dosyalarından yalnızca birinin derleme olabileceğini ve yalnızca belirtilen ilk çıktı dosyasının (örtülü veya açıkça **-out**ile) derleme olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e79e-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="2e79e-117">Derlemenin bir parçası olarak üretilen tüm modüller, derlemede üretilen herhangi bir derlemeyle ilişkili dosyalar haline gelir.</span><span class="sxs-lookup"><span data-stu-id="2e79e-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="2e79e-118">İlişkili dosyaları görmek için derleme bildirimini görüntülemek için [ildasm.exe'yi](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e79e-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="2e79e-119">Exe'nin bir arkadaş derlemesinin hedefi olabilmesi için -out derleyici seçeneği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2e79e-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="2e79e-120">Daha fazla bilgi için [Arkadaş Derlemeleri'ne](../../../standard/assembly/friend.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2e79e-120">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2e79e-121">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2e79e-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2e79e-122">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="2e79e-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="2e79e-123">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2e79e-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="2e79e-124">Derleme **adı** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2e79e-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="2e79e-125">Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> ayarlamak için: proje türü (exe, kitaplık vb.) ve derleme adının birleşimi ile belirlenen salt okunur bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2e79e-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="2e79e-126">Çıktı dosya adını ayarlamak için bu özelliklerden birinin veya her ikisinin değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e79e-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e79e-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e79e-127">Example</span></span>  
 <span data-ttu-id="2e79e-128">Derlemek `t.cs` ve çıktı `t.exe`dosyası oluşturmak `t2.cs` gibi oluşturmak ve `mymodule.netmodule`modül çıktı dosyası oluşturmak:</span><span class="sxs-lookup"><span data-stu-id="2e79e-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e79e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e79e-129">See also</span></span>

- [<span data-ttu-id="2e79e-130">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2e79e-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2e79e-131">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="2e79e-131">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="2e79e-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="2e79e-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
