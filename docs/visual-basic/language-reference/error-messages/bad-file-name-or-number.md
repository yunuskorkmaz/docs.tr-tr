---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 11e866d9a8da7ad1ecc5f788fc31f6ac96d32f2c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409835"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="b9685-102">Hatalı dosya adı veya numarası</span><span class="sxs-lookup"><span data-stu-id="b9685-102">Bad file name or number</span></span>
<span data-ttu-id="b9685-103">Belirtilen dosyaya erişmeye çalışırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b9685-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="b9685-104">Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:</span><span class="sxs-lookup"><span data-stu-id="b9685-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="b9685-105">Bir ifade, içinde belirtilmeyen `FileOpen` veya bir `FileOpen` ifadede belirtilen ancak daha sonra kapatılan bir dosya adı veya numarası olan bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="b9685-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="b9685-106">Bir ifade, dosya numarası aralığının dışında bir sayı içeren bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="b9685-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="b9685-107">Bir ifade, geçerli olmayan bir dosya adı veya sayı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b9685-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9685-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b9685-108">To correct this error</span></span>  
  
1. <span data-ttu-id="b9685-109">Dosya adının bir bildirimde belirtildiğinden emin olun `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="b9685-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="b9685-110">`FileClose`Deyiminizi bağımsız değişkenler olmadan çağırdıysanız, tüm açık dosyaları yanlışlıkla kapattığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b9685-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="b9685-111">Kodunuz algorithmically dosya numaralarını üretiyorsa, sayıların geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b9685-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="b9685-112">İşletim sistemi kurallarına uyduğundan emin olmak için dosya adlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b9685-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9685-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9685-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="b9685-114">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="b9685-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
