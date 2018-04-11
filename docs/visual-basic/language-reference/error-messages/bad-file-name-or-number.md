---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="d3d50-102">Hatalı dosya adı veya numarası</span><span class="sxs-lookup"><span data-stu-id="d3d50-102">Bad file name or number</span></span>
<span data-ttu-id="d3d50-103">Belirtilen dosyaya erişmeye çalışırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d3d50-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="d3d50-104">Bu hatanın olası nedenleri arasında aşağıdakiler vardır:</span><span class="sxs-lookup"><span data-stu-id="d3d50-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="d3d50-105">Bir ifade belirtilmedi bir dosya adı veya numarası sahip bir dosya başvuruyor `FileOpen` deyimi ya da değeri belirtilmiş bir `FileOpen` deyimi ancak edildi sonradan kapalı.</span><span class="sxs-lookup"><span data-stu-id="d3d50-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="d3d50-106">Bir deyim bir dosyayı dosya sayı aralık dışında bir sayı ile ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d3d50-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="d3d50-107">Bir deyim bir dosya adı veya geçersiz sayı başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="d3d50-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3d50-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d3d50-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="d3d50-109">Emin olun dosya adında belirtilen bir `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d3d50-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="d3d50-110">Çağrılan gerçekleştiriyorsanız `FileClose` deyimi bağımsız değişkenler olmadan, yanlışlıkla tüm açık dosyalar kapanır.</span><span class="sxs-lookup"><span data-stu-id="d3d50-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="d3d50-111">Kodunuzu dosya numaraları algorithmically oluşturuyorsa sayıları geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d3d50-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="d3d50-112">İşletim sistemi kuralları için uygun emin olmak için dosya adlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d3d50-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d50-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3d50-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="d3d50-114">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d3d50-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
