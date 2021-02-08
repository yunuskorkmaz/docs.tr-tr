---
description: 'Daha fazla bilgi edinin: Hatalı dosya adı veya numarası'
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 6e568a721fb3606c5b4bc046041c9d6f24b6d126
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797074"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="022af-103">Hatalı dosya adı veya numarası</span><span class="sxs-lookup"><span data-stu-id="022af-103">Bad file name or number</span></span>

<span data-ttu-id="022af-104">Belirtilen dosyaya erişmeye çalışırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="022af-104">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="022af-105">Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:</span><span class="sxs-lookup"><span data-stu-id="022af-105">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="022af-106">Bir ifade, içinde belirtilmeyen `FileOpen` veya bir `FileOpen` ifadede belirtilen ancak daha sonra kapatılan bir dosya adı veya numarası olan bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="022af-106">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="022af-107">Bir ifade, dosya numarası aralığının dışında bir sayı içeren bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="022af-107">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="022af-108">Bir ifade, geçerli olmayan bir dosya adı veya sayı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="022af-108">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="022af-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="022af-109">To correct this error</span></span>  
  
1. <span data-ttu-id="022af-110">Dosya adının bir bildirimde belirtildiğinden emin olun `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="022af-110">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="022af-111">`FileClose`Deyiminizi bağımsız değişkenler olmadan çağırdıysanız, tüm açık dosyaları yanlışlıkla kapattığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="022af-111">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="022af-112">Kodunuz algorithmically dosya numaralarını üretiyorsa, sayıların geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="022af-112">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="022af-113">İşletim sistemi kurallarına uyduğundan emin olmak için dosya adlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="022af-113">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="022af-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="022af-114">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="022af-115">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="022af-115">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
