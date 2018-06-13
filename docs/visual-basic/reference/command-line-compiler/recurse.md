---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd5dde46cdea67825b14a6f5fa96a82c8bab8d3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652428"
---
# <a name="-recurse"></a><span data-ttu-id="06aba-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="06aba-102">-recurse</span></span>
<span data-ttu-id="06aba-103">Belirtilen dizin veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derler.</span><span class="sxs-lookup"><span data-stu-id="06aba-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06aba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06aba-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="06aba-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="06aba-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="06aba-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="06aba-106">Optional.</span></span> <span data-ttu-id="06aba-107">Aramayı başlatmak istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="06aba-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="06aba-108">Belirtilmezse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="06aba-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="06aba-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="06aba-109">Required.</span></span> <span data-ttu-id="06aba-110">Aranacak dosya.</span><span class="sxs-lookup"><span data-stu-id="06aba-110">The file(s) to search for.</span></span> <span data-ttu-id="06aba-111">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="06aba-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06aba-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06aba-112">Remarks</span></span>  
 <span data-ttu-id="06aba-113">Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="06aba-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="06aba-114">Derleyici hiçbir çıktı dosyası adı belirtilirse, işlenen ilk giriş dosyası çıktı dosyası adını temel alır.</span><span class="sxs-lookup"><span data-stu-id="06aba-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="06aba-115">Bu genellikle ilk alfabetik olarak görüntülendiğinde derlenmiş dosyalar listesinden dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="06aba-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="06aba-116">Bu nedenle, bir çıktı dosyası kullanarak belirtmek en iyisidir `-out` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="06aba-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06aba-117">`-recurse` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06aba-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06aba-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="06aba-118">Example</span></span>  
 <span data-ttu-id="06aba-119">Aşağıdaki komutu geçerli dizindeki tüm Visual Basic dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="06aba-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="06aba-120">Aşağıdaki komutu tüm Visual Basic dosyalarını derler `Test\ABC` dizin ve herhangi bir dizinlerinde ve ardından oluşturur `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="06aba-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="06aba-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06aba-121">See Also</span></span>  
 [<span data-ttu-id="06aba-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="06aba-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="06aba-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06aba-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="06aba-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="06aba-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
