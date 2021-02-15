---
description: Hakkında daha fazla bilgi edinin:-recurse
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2c0f1788c3811e24e2d51ff30e4cb2842aa0bd7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475883"
---
# <a name="-recurse"></a><span data-ttu-id="74dea-103">-recurse</span><span class="sxs-lookup"><span data-stu-id="74dea-103">-recurse</span></span>

<span data-ttu-id="74dea-104">Belirtilen dizinin ya da proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="74dea-104">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74dea-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="74dea-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="74dea-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="74dea-106">Arguments</span></span>  

 `dir`  
 <span data-ttu-id="74dea-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="74dea-107">Optional.</span></span> <span data-ttu-id="74dea-108">Aramanın başlamasını istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="74dea-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="74dea-109">Belirtilmemişse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="74dea-109">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="74dea-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="74dea-110">Required.</span></span> <span data-ttu-id="74dea-111">Aranacak dosya (lar).</span><span class="sxs-lookup"><span data-stu-id="74dea-111">The file(s) to search for.</span></span> <span data-ttu-id="74dea-112">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="74dea-112">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74dea-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74dea-113">Remarks</span></span>  

 <span data-ttu-id="74dea-114">Kullanarak proje dizinindeki tüm eşleşen dosyaları derlemek için dosya adında joker karakterler kullanabilirsiniz `-recurse` .</span><span class="sxs-lookup"><span data-stu-id="74dea-114">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="74dea-115">Çıkış dosyası adı belirtilmemişse, derleyici, çıktı dosyasının adını işlenen ilk girdi dosyasında temel alır.</span><span class="sxs-lookup"><span data-stu-id="74dea-115">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="74dea-116">Bu genellikle alfabetik olarak görüntülendiklerinde derlenen dosyalar listesindeki ilk dosyadır.</span><span class="sxs-lookup"><span data-stu-id="74dea-116">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="74dea-117">Bu nedenle, seçeneğini kullanarak bir çıkış dosyası belirtmek en iyisidir `-out` .</span><span class="sxs-lookup"><span data-stu-id="74dea-117">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74dea-118">`-recurse`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74dea-118">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74dea-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="74dea-119">Example</span></span>  

 <span data-ttu-id="74dea-120">Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="74dea-120">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="74dea-121">Aşağıdaki komut dizindeki tüm Visual Basic dosyalarını `Test\ABC` ve altındaki tüm dizinleri derler ve sonra üretir `Test.ABC.dll` .</span><span class="sxs-lookup"><span data-stu-id="74dea-121">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="74dea-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74dea-122">See also</span></span>

- [<span data-ttu-id="74dea-123">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="74dea-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="74dea-124">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74dea-124">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="74dea-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="74dea-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
