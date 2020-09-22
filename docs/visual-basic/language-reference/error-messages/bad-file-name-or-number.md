---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874897"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="fa5e5-102">Hatalı dosya adı veya numarası</span><span class="sxs-lookup"><span data-stu-id="fa5e5-102">Bad file name or number</span></span>

<span data-ttu-id="fa5e5-103">Belirtilen dosyaya erişmeye çalışırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="fa5e5-104">Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:</span><span class="sxs-lookup"><span data-stu-id="fa5e5-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="fa5e5-105">Bir ifade, içinde belirtilmeyen `FileOpen` veya bir `FileOpen` ifadede belirtilen ancak daha sonra kapatılan bir dosya adı veya numarası olan bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="fa5e5-106">Bir ifade, dosya numarası aralığının dışında bir sayı içeren bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="fa5e5-107">Bir ifade, geçerli olmayan bir dosya adı veya sayı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa5e5-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fa5e5-108">To correct this error</span></span>  
  
1. <span data-ttu-id="fa5e5-109">Dosya adının bir bildirimde belirtildiğinden emin olun `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="fa5e5-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="fa5e5-110">`FileClose`Deyiminizi bağımsız değişkenler olmadan çağırdıysanız, tüm açık dosyaları yanlışlıkla kapattığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="fa5e5-111">Kodunuz algorithmically dosya numaralarını üretiyorsa, sayıların geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="fa5e5-112">İşletim sistemi kurallarına uyduğundan emin olmak için dosya adlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5e5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa5e5-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="fa5e5-114">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="fa5e5-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
