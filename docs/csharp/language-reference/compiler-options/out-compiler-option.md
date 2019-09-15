---
title: -Out (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970373"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="a601e-102">-Out (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a601e-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="a601e-103">**-Out** seçeneği, çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a601e-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a601e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a601e-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="a601e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a601e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a601e-106">Derleyici tarafından oluşturulan çıkış dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="a601e-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a601e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a601e-107">Remarks</span></span>  
 <span data-ttu-id="a601e-108">Komut satırında, derlemeniz için birden çok çıkış dosyası belirtmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a601e-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="a601e-109">Derleyici, **-Out** seçeneğinden sonra bir veya daha fazla kaynak kodu dosyası bulmayı bekler.</span><span class="sxs-lookup"><span data-stu-id="a601e-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="a601e-110">Ardından, tüm kaynak kodu dosyaları **, bu seçenek** tarafından belirtilen çıkış dosyasına derlenir.</span><span class="sxs-lookup"><span data-stu-id="a601e-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="a601e-111">Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a601e-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="a601e-112">Çıkış dosyasının adını belirtmezseniz:</span><span class="sxs-lookup"><span data-stu-id="a601e-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="a601e-113">Bir. exe, **ana** yöntemi içeren kaynak kodu dosyasından adını alır.</span><span class="sxs-lookup"><span data-stu-id="a601e-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="a601e-114">Bir. dll veya. netmodule adı ilk kaynak kodu dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="a601e-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="a601e-115">Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyası, başka bir çıkış dosyasının derlenmesi için aynı derlemede kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a601e-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="a601e-116">Bir komut satırı derlemesinde birden çok çıkış dosyası üretilirken, yalnızca bir tane çıkış dosyası derleme olabileceğini ve yalnızca ilk çıkış dosyasının (örtük veya açık **olarak ile)** derleme olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a601e-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="a601e-117">Bir derlemenin parçası olarak üretilen tüm modüller, derlemede oluşturulan herhangi bir derlemeyle ilişkili dosyalar olur.</span><span class="sxs-lookup"><span data-stu-id="a601e-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="a601e-118">İlişkili dosyaları görmek üzere derleme bildirimini görüntülemek için [ıldadsm. exe](../../../framework/tools/ildasm-exe-il-disassembler.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a601e-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="a601e-119">Bir exe 'nin bir arkadaş derlemenin hedefi olması için-out derleyici seçeneği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a601e-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="a601e-120">Daha fazla bilgi için bkz. [Friend derlemeleri](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="a601e-120">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a601e-121">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a601e-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a601e-122">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="a601e-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a601e-123">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a601e-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="a601e-124">**Derleme adı** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a601e-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="a601e-125">Bu derleyici seçeneğini program aracılığıyla ayarlamak için: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> , proje türünün (exe, kitaplık, vb.) ve derleme adının bir birleşimiyle belirlenen salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="a601e-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="a601e-126">Bu özelliklerden birinin veya her ikisinin de değiştirilmesi, çıkış dosyası adını ayarlamak için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a601e-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a601e-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="a601e-127">Example</span></span>  
 <span data-ttu-id="a601e-128">Çıkış `t.cs` dosyasını `t.exe`derleyin ve oluşturun `t2.cs` , Ayrıca modül çıkış dosyası `mymodule.netmodule`oluşturup oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a601e-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a601e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a601e-129">See also</span></span>

- [<span data-ttu-id="a601e-130">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a601e-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a601e-131">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="a601e-131">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="a601e-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a601e-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
