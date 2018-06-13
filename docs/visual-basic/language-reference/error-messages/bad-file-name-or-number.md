---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585573"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="040d1-102">Hatalı dosya adı veya numarası</span><span class="sxs-lookup"><span data-stu-id="040d1-102">Bad file name or number</span></span>
<span data-ttu-id="040d1-103">Belirtilen dosyaya erişmeye çalışırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="040d1-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="040d1-104">Bu hatanın olası nedenleri arasında aşağıdakiler vardır:</span><span class="sxs-lookup"><span data-stu-id="040d1-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="040d1-105">Bir ifade belirtilmedi bir dosya adı veya numarası sahip bir dosya başvuruyor `FileOpen` deyimi ya da değeri belirtilmiş bir `FileOpen` deyimi ancak edildi sonradan kapalı.</span><span class="sxs-lookup"><span data-stu-id="040d1-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="040d1-106">Bir deyim bir dosyayı dosya sayı aralık dışında bir sayı ile ifade eder.</span><span class="sxs-lookup"><span data-stu-id="040d1-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="040d1-107">Bir deyim bir dosya adı veya geçersiz sayı başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="040d1-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="040d1-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="040d1-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="040d1-109">Emin olun dosya adında belirtilen bir `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="040d1-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="040d1-110">Çağrılan gerçekleştiriyorsanız `FileClose` deyimi bağımsız değişkenler olmadan, yanlışlıkla tüm açık dosyalar kapanır.</span><span class="sxs-lookup"><span data-stu-id="040d1-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="040d1-111">Kodunuzu dosya numaraları algorithmically oluşturuyorsa sayıları geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="040d1-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="040d1-112">İşletim sistemi kuralları için uygun emin olmak için dosya adlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="040d1-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040d1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="040d1-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="040d1-114">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="040d1-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
