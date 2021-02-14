---
description: :-Moduleassemblyname hakkında daha fazla bilgi edinin
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 1b5daac8fea264e86b7200f3cead4cb657641000
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434322"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="084c1-103">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="084c1-103">-moduleassemblyname</span></span>

<span data-ttu-id="084c1-104">Bu modülün bir parçası olacağı derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="084c1-104">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="084c1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="084c1-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="084c1-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="084c1-106">Arguments</span></span>  
  
|<span data-ttu-id="084c1-107">Terim</span><span class="sxs-lookup"><span data-stu-id="084c1-107">Term</span></span>|<span data-ttu-id="084c1-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="084c1-108">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="084c1-109">Bu modülün bir parçası olacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="084c1-109">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="084c1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="084c1-110">Remarks</span></span>  

 <span data-ttu-id="084c1-111">Derleyici, `-moduleassemblyname` seçeneği yalnızca `-target:module` seçenek belirtilmişse işler.</span><span class="sxs-lookup"><span data-stu-id="084c1-111">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="084c1-112">Bu, derleyicinin bir modül oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="084c1-112">This causes the compiler to create a module.</span></span> <span data-ttu-id="084c1-113">Derleyici tarafından oluşturulan modül yalnızca seçeneğiyle belirtilen derleme için geçerlidir `-moduleassemblyname` .</span><span class="sxs-lookup"><span data-stu-id="084c1-113">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="084c1-114">Modülü farklı bir derlemeye yerleştirirseniz, çalışma zamanı hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="084c1-114">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="084c1-115">`-moduleassemblyname`Seçeneği yalnızca aşağıdakilerin doğru olması durumunda gereklidir:</span><span class="sxs-lookup"><span data-stu-id="084c1-115">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="084c1-116">Modüldeki bir veri türünün başvurulan derlemedeki bir türe erişmesi gerekir `Friend` .</span><span class="sxs-lookup"><span data-stu-id="084c1-116">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="084c1-117">Başvurulan derleme, modülün derleyecek olduğu derlemeye arkadaş bütünleştirilmiş kodu erişimi verdi.</span><span class="sxs-lookup"><span data-stu-id="084c1-117">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="084c1-118">Modül oluşturma hakkında daha fazla bilgi için bkz. [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="084c1-118">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="084c1-119">Arkadaş derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="084c1-119">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="084c1-120">`-moduleassemblyname`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca bir komut isteminden derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="084c1-120">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084c1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="084c1-121">See also</span></span>

- [<span data-ttu-id="084c1-122">Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="084c1-122">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="084c1-123">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="084c1-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="084c1-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="084c1-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="084c1-125">-Main</span><span class="sxs-lookup"><span data-stu-id="084c1-125">-main</span></span>](main.md)
- [<span data-ttu-id="084c1-126">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="084c1-126">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="084c1-127">-addmodule</span><span class="sxs-lookup"><span data-stu-id="084c1-127">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="084c1-128">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="084c1-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="084c1-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="084c1-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="084c1-130">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="084c1-130">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
