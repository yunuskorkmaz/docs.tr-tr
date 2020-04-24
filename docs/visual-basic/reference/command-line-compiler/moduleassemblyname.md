---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a612a68cffd927f3e360406cca6d9daae4f66c86
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775630"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="eeec8-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="eeec8-102">-moduleassemblyname</span></span>
<span data-ttu-id="eeec8-103">Bu modülün bir parçası olacağı derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eeec8-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeec8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eeec8-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="eeec8-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="eeec8-105">Arguments</span></span>  
  
|<span data-ttu-id="eeec8-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="eeec8-106">Term</span></span>|<span data-ttu-id="eeec8-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="eeec8-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="eeec8-108">Bu modülün bir parçası olacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="eeec8-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeec8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eeec8-109">Remarks</span></span>  
 <span data-ttu-id="eeec8-110">Derleyici, `-moduleassemblyname` seçeneği yalnızca `-target:module` seçenek belirtilmişse işler.</span><span class="sxs-lookup"><span data-stu-id="eeec8-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="eeec8-111">Bu, derleyicinin bir modül oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="eeec8-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="eeec8-112">Derleyici tarafından oluşturulan modül yalnızca `-moduleassemblyname` seçeneğiyle belirtilen derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eeec8-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="eeec8-113">Modülü farklı bir derlemeye yerleştirirseniz, çalışma zamanı hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="eeec8-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="eeec8-114">`-moduleassemblyname` Seçeneği yalnızca aşağıdakilerin doğru olması durumunda gereklidir:</span><span class="sxs-lookup"><span data-stu-id="eeec8-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="eeec8-115">Modüldeki bir veri türünün başvurulan derlemedeki bir `Friend` türe erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeec8-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="eeec8-116">Başvurulan derleme, modülün derleyecek olduğu derlemeye arkadaş bütünleştirilmiş kodu erişimi verdi.</span><span class="sxs-lookup"><span data-stu-id="eeec8-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="eeec8-117">Modül oluşturma hakkında daha fazla bilgi için bkz. [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="eeec8-117">For more information about creating a module, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="eeec8-118">Arkadaş derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="eeec8-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eeec8-119">Bu `-moduleassemblyname` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca bir komut isteminden derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eeec8-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeec8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeec8-120">See also</span></span>

- [<span data-ttu-id="eeec8-121">Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="eeec8-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="eeec8-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="eeec8-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="eeec8-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeec8-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="eeec8-124">-main</span><span class="sxs-lookup"><span data-stu-id="eeec8-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="eeec8-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eeec8-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="eeec8-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="eeec8-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="eeec8-127">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="eeec8-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="eeec8-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="eeec8-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="eeec8-129">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="eeec8-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
