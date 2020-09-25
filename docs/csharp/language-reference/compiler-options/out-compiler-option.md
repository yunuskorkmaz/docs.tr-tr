---
description: -Out (C# derleyici seçenekleri)
title: -Out (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 409760ee0b147065a2128c62c304fb5d70cfcf42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193887"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="07af7-103">-Out (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="07af7-103">-out (C# Compiler Options)</span></span>

<span data-ttu-id="07af7-104">**-Out** seçeneği, çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07af7-104">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07af7-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07af7-105">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="07af7-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="07af7-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="07af7-107">Derleyici tarafından oluşturulan çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="07af7-107">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07af7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07af7-108">Remarks</span></span>  

 <span data-ttu-id="07af7-109">Komut satırında, derlemeniz için birden çok çıkış dosyası belirtmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="07af7-109">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="07af7-110">Derleyici, **-Out** seçeneğinden sonra bir veya daha fazla kaynak kodu dosyası bulmayı bekler.</span><span class="sxs-lookup"><span data-stu-id="07af7-110">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="07af7-111">Ardından, tüm kaynak kodu dosyaları **, bu seçenek** tarafından belirtilen çıkış dosyasına derlenir.</span><span class="sxs-lookup"><span data-stu-id="07af7-111">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="07af7-112">Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="07af7-112">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="07af7-113">Çıkış dosyasının adını belirtmezseniz:</span><span class="sxs-lookup"><span data-stu-id="07af7-113">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="07af7-114">Bir. exe, **ana** yöntemi içeren kaynak kodu dosyasından adını alır.</span><span class="sxs-lookup"><span data-stu-id="07af7-114">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="07af7-115">Bir. dll veya. netmodule adı ilk kaynak kodu dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="07af7-115">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="07af7-116">Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyası, başka bir çıkış dosyasının derlenmesi için aynı derlemede kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="07af7-116">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="07af7-117">Bir komut satırı derlemesinde birden çok çıkış dosyası üretilirken, yalnızca bir tane çıkış dosyası derleme olabileceğini ve yalnızca ilk çıkış dosyasının (örtük veya açık **olarak ile)** derleme olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="07af7-117">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="07af7-118">Bir derlemenin parçası olarak üretilen tüm modüller, derlemede oluşturulan herhangi bir derlemeyle ilişkili dosyalar olur.</span><span class="sxs-lookup"><span data-stu-id="07af7-118">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="07af7-119">İlişkili dosyaları görmek üzere derleme bildirimini görüntülemek için [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="07af7-119">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="07af7-120">Bir exe 'nin bir arkadaş derlemenin hedefi olması için-out derleyici seçeneği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07af7-120">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="07af7-121">Daha fazla bilgi için bkz. [Friend derlemeleri](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="07af7-121">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="07af7-122">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="07af7-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="07af7-123">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="07af7-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="07af7-124">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="07af7-124">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="07af7-125">**Derleme adı** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="07af7-125">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="07af7-126">Bu derleyici seçeneğini program aracılığıyla ayarlamak için:, <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> Proje türünün (exe, kitaplık, vb.) ve derleme adının bir birleşimiyle belirlenen salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="07af7-126">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="07af7-127">Bu özelliklerden birinin veya her ikisinin de değiştirilmesi, çıkış dosyası adını ayarlamak için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="07af7-127">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07af7-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="07af7-128">Example</span></span>  

 <span data-ttu-id="07af7-129">`t.cs`Çıkış dosyasını derleyin ve oluşturun `t.exe` , ayrıca `t2.cs` Modül çıkış dosyası oluşturup oluşturun `mymodule.netmodule` :</span><span class="sxs-lookup"><span data-stu-id="07af7-129">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="07af7-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07af7-130">See also</span></span>

- [<span data-ttu-id="07af7-131">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="07af7-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="07af7-132">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="07af7-132">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="07af7-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="07af7-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
