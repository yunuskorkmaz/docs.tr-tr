---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: fc8dfe41ea56531ff34cd5e551ef24d636227e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400506"
---
# <a name="-recurse"></a><span data-ttu-id="91249-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="91249-102">-recurse</span></span>
<span data-ttu-id="91249-103">Belirtilen dizinin ya da proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="91249-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91249-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="91249-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="91249-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="91249-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="91249-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="91249-106">Optional.</span></span> <span data-ttu-id="91249-107">Aramanın başlamasını istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="91249-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="91249-108">Belirtilmemişse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="91249-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="91249-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="91249-109">Required.</span></span> <span data-ttu-id="91249-110">Aranacak dosya (lar).</span><span class="sxs-lookup"><span data-stu-id="91249-110">The file(s) to search for.</span></span> <span data-ttu-id="91249-111">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="91249-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91249-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91249-112">Remarks</span></span>  
 <span data-ttu-id="91249-113">Kullanarak proje dizinindeki tüm eşleşen dosyaları derlemek için dosya adında joker karakterler kullanabilirsiniz `-recurse` .</span><span class="sxs-lookup"><span data-stu-id="91249-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="91249-114">Çıkış dosyası adı belirtilmemişse, derleyici, çıktı dosyasının adını işlenen ilk girdi dosyasında temel alır.</span><span class="sxs-lookup"><span data-stu-id="91249-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="91249-115">Bu genellikle alfabetik olarak görüntülendiklerinde derlenen dosyalar listesindeki ilk dosyadır.</span><span class="sxs-lookup"><span data-stu-id="91249-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="91249-116">Bu nedenle, seçeneğini kullanarak bir çıkış dosyası belirtmek en iyisidir `-out` .</span><span class="sxs-lookup"><span data-stu-id="91249-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91249-117">`-recurse`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91249-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91249-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="91249-118">Example</span></span>  
 <span data-ttu-id="91249-119">Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyalarını derler.</span><span class="sxs-lookup"><span data-stu-id="91249-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="91249-120">Aşağıdaki komut dizindeki tüm Visual Basic dosyalarını `Test\ABC` ve altındaki tüm dizinleri derler ve sonra üretir `Test.ABC.dll` .</span><span class="sxs-lookup"><span data-stu-id="91249-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="91249-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91249-121">See also</span></span>

- [<span data-ttu-id="91249-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="91249-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="91249-123">-Out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91249-123">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="91249-124">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="91249-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
