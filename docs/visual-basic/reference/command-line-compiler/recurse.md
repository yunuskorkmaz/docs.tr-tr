---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 7ded2b7d102430d8d4e545da5ab6ce8bafe3609e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095439"
---
# <a name="-recurse"></a><span data-ttu-id="e563b-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="e563b-102">-recurse</span></span>

<span data-ttu-id="e563b-103">Belirtilen dizinin ya da proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="e563b-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e563b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e563b-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e563b-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e563b-105">Arguments</span></span>  

 `dir`  
 <span data-ttu-id="e563b-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e563b-106">Optional.</span></span> <span data-ttu-id="e563b-107">Aramanın başlamasını istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="e563b-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="e563b-108">Belirtilmemişse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="e563b-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="e563b-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e563b-109">Required.</span></span> <span data-ttu-id="e563b-110">Aranacak dosya (lar).</span><span class="sxs-lookup"><span data-stu-id="e563b-110">The file(s) to search for.</span></span> <span data-ttu-id="e563b-111">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e563b-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e563b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e563b-112">Remarks</span></span>  

 <span data-ttu-id="e563b-113">Kullanarak proje dizinindeki tüm eşleşen dosyaları derlemek için dosya adında joker karakterler kullanabilirsiniz `-recurse` .</span><span class="sxs-lookup"><span data-stu-id="e563b-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="e563b-114">Çıkış dosyası adı belirtilmemişse, derleyici, çıktı dosyasının adını işlenen ilk girdi dosyasında temel alır.</span><span class="sxs-lookup"><span data-stu-id="e563b-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="e563b-115">Bu genellikle alfabetik olarak görüntülendiklerinde derlenen dosyalar listesindeki ilk dosyadır.</span><span class="sxs-lookup"><span data-stu-id="e563b-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="e563b-116">Bu nedenle, seçeneğini kullanarak bir çıkış dosyası belirtmek en iyisidir `-out` .</span><span class="sxs-lookup"><span data-stu-id="e563b-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e563b-117">`-recurse`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e563b-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e563b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e563b-118">Example</span></span>  

 <span data-ttu-id="e563b-119">Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="e563b-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="e563b-120">Aşağıdaki komut dizindeki tüm Visual Basic dosyalarını `Test\ABC` ve altındaki tüm dizinleri derler ve sonra üretir `Test.ABC.dll` .</span><span class="sxs-lookup"><span data-stu-id="e563b-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e563b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e563b-121">See also</span></span>

- [<span data-ttu-id="e563b-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e563b-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e563b-123">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e563b-123">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="e563b-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="e563b-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
