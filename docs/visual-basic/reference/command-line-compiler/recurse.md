---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005255"
---
# <a name="-recurse"></a><span data-ttu-id="3ec86-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="3ec86-102">-recurse</span></span>
<span data-ttu-id="3ec86-103">Belirtilen dizinin ya da proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="3ec86-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ec86-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ec86-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3ec86-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="3ec86-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3ec86-106">Optional.</span></span> <span data-ttu-id="3ec86-107">Aramanın başlamasını istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="3ec86-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="3ec86-108">Belirtilmemişse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="3ec86-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="3ec86-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3ec86-109">Required.</span></span> <span data-ttu-id="3ec86-110">Aranacak dosya (lar).</span><span class="sxs-lookup"><span data-stu-id="3ec86-110">The file(s) to search for.</span></span> <span data-ttu-id="3ec86-111">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3ec86-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ec86-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ec86-112">Remarks</span></span>  
 <span data-ttu-id="3ec86-113">@No__t-0 kullanmadan proje dizinindeki tüm eşleşen dosyaları derlemek için dosya adında joker karakterler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ec86-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="3ec86-114">Çıkış dosyası adı belirtilmemişse, derleyici, çıktı dosyasının adını işlenen ilk girdi dosyasında temel alır.</span><span class="sxs-lookup"><span data-stu-id="3ec86-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="3ec86-115">Bu genellikle alfabetik olarak görüntülendiklerinde derlenen dosyalar listesindeki ilk dosyadır.</span><span class="sxs-lookup"><span data-stu-id="3ec86-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="3ec86-116">Bu nedenle, `-out` seçeneğini kullanarak bir çıkış dosyası belirtmek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="3ec86-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ec86-117">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ec86-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ec86-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ec86-118">Example</span></span>  
 <span data-ttu-id="3ec86-119">Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="3ec86-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="3ec86-120">Aşağıdaki komut, `Test\ABC` dizinindeki tüm Visual Basic dosyalarını ve altındaki tüm dizinleri derler ve ardından 1 @no__t üretir.</span><span class="sxs-lookup"><span data-stu-id="3ec86-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ec86-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ec86-121">See also</span></span>

- [<span data-ttu-id="3ec86-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3ec86-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3ec86-123">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ec86-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="3ec86-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3ec86-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
