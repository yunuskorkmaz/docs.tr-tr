---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a><span data-ttu-id="f3f29-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="f3f29-102">/recurse</span></span>
<span data-ttu-id="f3f29-103">Belirtilen dizin veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derler.</span><span class="sxs-lookup"><span data-stu-id="f3f29-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3f29-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3f29-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f3f29-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="f3f29-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f3f29-106">Optional.</span></span> <span data-ttu-id="f3f29-107">Aramayı başlatmak istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="f3f29-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="f3f29-108">Belirtilmezse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="f3f29-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="f3f29-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f3f29-109">Required.</span></span> <span data-ttu-id="f3f29-110">Aranacak dosya.</span><span class="sxs-lookup"><span data-stu-id="f3f29-110">The file(s) to search for.</span></span> <span data-ttu-id="f3f29-111">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f3f29-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3f29-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3f29-112">Remarks</span></span>  
 <span data-ttu-id="f3f29-113">Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="f3f29-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="f3f29-114">Derleyici hiçbir çıktı dosyası adı belirtilirse, işlenen ilk giriş dosyası çıktı dosyası adını temel alır.</span><span class="sxs-lookup"><span data-stu-id="f3f29-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="f3f29-115">Bu genellikle ilk alfabetik olarak görüntülendiğinde derlenmiş dosyalar listesinden dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3f29-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="f3f29-116">Bu nedenle, bir çıktı dosyası kullanarak belirtmek en iyisidir `/out` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f3f29-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3f29-117">`/recurse` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3f29-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f29-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3f29-118">Example</span></span>  
 <span data-ttu-id="f3f29-119">Aşağıdaki kod tüm derler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] geçerli dizindeki dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f3f29-119">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="f3f29-120">Aşağıdaki kod tüm derler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dosyalar `Test\ABC` dizin ve herhangi bir dizinlerinde ve ardından oluşturur `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="f3f29-120">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3f29-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f29-121">See Also</span></span>  
 [<span data-ttu-id="f3f29-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f3f29-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f3f29-123">/ out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3f29-123">/out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="f3f29-124">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="f3f29-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
