---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8b579c2c3ae22469706326ee17109b8e39dab60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650796"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="b5be4-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="b5be4-102">-moduleassemblyname</span></span>
<span data-ttu-id="b5be4-103">Bu modül bir parçası olacak bütünleştirilmiş kodun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5be4-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5be4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5be4-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5be4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5be4-105">Arguments</span></span>  
  
|<span data-ttu-id="b5be4-106">Terim</span><span class="sxs-lookup"><span data-stu-id="b5be4-106">Term</span></span>|<span data-ttu-id="b5be4-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="b5be4-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="b5be4-108">Bu modül bir parçası olacak derleme adı.</span><span class="sxs-lookup"><span data-stu-id="b5be4-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5be4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5be4-109">Remarks</span></span>  
 <span data-ttu-id="b5be4-110">Derleyici işlemleri `-moduleassemblyname` seçeneği yalnızca IF `-target:module` seçeneği belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="b5be4-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="b5be4-111">Bu modül oluşturmak derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="b5be4-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="b5be4-112">Derleyici tarafından oluşturulan modülü ile belirtilen derleme için geçerli `-moduleassemblyname` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b5be4-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="b5be4-113">Farklı bir derlemede modülü yerleştirirseniz, çalışma zamanı hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="b5be4-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="b5be4-114">`-moduleassemblyname` Seçeneği yalnızca aşağıdaki doğru olduğunda gereklidir:</span><span class="sxs-lookup"><span data-stu-id="b5be4-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="b5be4-115">Modül bir veri türü erişmesi gereken bir `Friend` başvurulan bir derleme türü.</span><span class="sxs-lookup"><span data-stu-id="b5be4-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="b5be4-116">Başvurulan derlemeyi içine modülü oluşturulacak derlemeye arkadaş derleme erişimi verildi.</span><span class="sxs-lookup"><span data-stu-id="b5be4-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="b5be4-117">Bir modül oluşturma hakkında daha fazla bilgi için bkz: [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="b5be4-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="b5be4-118">Arkadaş derlemeleri hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="b5be4-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5be4-119">`-moduleassemblyname` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; bir komut isteminden derleme zaman yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5be4-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5be4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5be4-120">See Also</span></span>  
 [<span data-ttu-id="b5be4-121">Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="b5be4-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="b5be4-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b5be4-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b5be4-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5be4-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="b5be4-124">-main</span><span class="sxs-lookup"><span data-stu-id="b5be4-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="b5be4-125">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5be4-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="b5be4-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="b5be4-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="b5be4-127">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="b5be4-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="b5be4-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b5be4-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="b5be4-129">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="b5be4-129">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
