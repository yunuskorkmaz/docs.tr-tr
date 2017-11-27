---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a><span data-ttu-id="4a271-102">/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="4a271-102">/moduleassemblyname</span></span>
<span data-ttu-id="4a271-103">Bu modül bir parçası olacak bütünleştirilmiş kodun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a271-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a271-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a271-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a271-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a271-105">Arguments</span></span>  
  
|<span data-ttu-id="4a271-106">Terim</span><span class="sxs-lookup"><span data-stu-id="4a271-106">Term</span></span>|<span data-ttu-id="4a271-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="4a271-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="4a271-108">Bu modül bir parçası olacak derleme adı.</span><span class="sxs-lookup"><span data-stu-id="4a271-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a271-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a271-109">Remarks</span></span>  
 <span data-ttu-id="4a271-110">Derleyici işlemleri `/moduleassemblyname` seçeneği yalnızca IF `/target:module` seçeneği belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="4a271-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="4a271-111">Bu modül oluşturmak derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="4a271-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="4a271-112">Derleyici tarafından oluşturulan modülü ile belirtilen derleme için geçerli `/moduleassemblyname` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4a271-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="4a271-113">Farklı bir derlemede modülü yerleştirirseniz, çalışma zamanı hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="4a271-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="4a271-114">`/moduleassemblyname` Seçeneği yalnızca aşağıdaki doğru olduğunda gereklidir:</span><span class="sxs-lookup"><span data-stu-id="4a271-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="4a271-115">Modül bir veri türü erişmesi gereken bir `Friend` başvurulan bir derleme türü.</span><span class="sxs-lookup"><span data-stu-id="4a271-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="4a271-116">Başvurulan derlemeyi içine modülü oluşturulacak derlemeye arkadaş derleme erişimi verildi.</span><span class="sxs-lookup"><span data-stu-id="4a271-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="4a271-117">Bir modül oluşturma hakkında daha fazla bilgi için bkz: [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="4a271-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="4a271-118">Arkadaş derlemeleri hakkında daha fazla bilgi için bkz: [arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="4a271-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a271-119">`/moduleassemblyname` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; bir komut isteminden derleme zaman yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a271-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a271-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a271-120">See Also</span></span>  
 [<span data-ttu-id="4a271-121">Nasıl yapılır: birden fazla dosya derleme</span><span class="sxs-lookup"><span data-stu-id="4a271-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="4a271-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4a271-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4a271-123">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a271-123">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="4a271-124">/ main</span><span class="sxs-lookup"><span data-stu-id="4a271-124">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="4a271-125">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a271-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="4a271-126">/ addmodule</span><span class="sxs-lookup"><span data-stu-id="4a271-126">/addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="4a271-127">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="4a271-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="4a271-128">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="4a271-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="4a271-129">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="4a271-129">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
