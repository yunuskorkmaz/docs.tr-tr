---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: f88a0001bb2ba55c0a3eac3ed208f14292d86734
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745670"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="609cf-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="609cf-102">-moduleassemblyname</span></span>
<span data-ttu-id="609cf-103">Bu modül bir parçası olacağı derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="609cf-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="609cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="609cf-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="609cf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="609cf-105">Arguments</span></span>  
  
|<span data-ttu-id="609cf-106">Terim</span><span class="sxs-lookup"><span data-stu-id="609cf-106">Term</span></span>|<span data-ttu-id="609cf-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="609cf-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="609cf-108">Bu modül bir parçası olacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="609cf-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="609cf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="609cf-109">Remarks</span></span>  
 <span data-ttu-id="609cf-110">Derleyici işlemleri `-moduleassemblyname` seçeneği yalnızca şu durumlarda `-target:module` seçeneği belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="609cf-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="609cf-111">Bu modülü oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="609cf-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="609cf-112">Yalnızca belirtilen derleme için geçerli olduğundan derleyici tarafından oluşturulan Modülü `-moduleassemblyname` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="609cf-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="609cf-113">Farklı bir derlemede modülü yerleştirirseniz, çalışma zamanı hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="609cf-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="609cf-114">`-moduleassemblyname` Seçeneği, yalnızca aşağıdaki true olduğunda gereklidir:</span><span class="sxs-lookup"><span data-stu-id="609cf-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="609cf-115">Modül bir veri türü erişmesi gereken bir `Friend` başvurulan bir derleme türü.</span><span class="sxs-lookup"><span data-stu-id="609cf-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="609cf-116">Başvurulan derleme modülü derlenecek olan derlemeye arkadaş derleme erişim verildi.</span><span class="sxs-lookup"><span data-stu-id="609cf-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="609cf-117">Bir modül oluşturma hakkında daha fazla bilgi için bkz. [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="609cf-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="609cf-118">Arkadaş bütünleştirilmiş kodları hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="609cf-118">For more information about friend assemblies, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="609cf-119">`-moduleassemblyname` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca bir komut istemi'nden derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="609cf-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609cf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609cf-120">See also</span></span>
- [<span data-ttu-id="609cf-121">Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="609cf-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="609cf-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="609cf-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="609cf-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="609cf-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="609cf-124">-main</span><span class="sxs-lookup"><span data-stu-id="609cf-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="609cf-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="609cf-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="609cf-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="609cf-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="609cf-127">.NET derlemeleri</span><span class="sxs-lookup"><span data-stu-id="609cf-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="609cf-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="609cf-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="609cf-129">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="609cf-129">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)
