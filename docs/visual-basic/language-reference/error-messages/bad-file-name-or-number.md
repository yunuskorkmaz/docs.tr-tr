---
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 2e5d4a3ddd66df85dc4758e22b36ac1ed495659a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935232"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="fd82e-102">Hatalı dosya adı veya numarası</span><span class="sxs-lookup"><span data-stu-id="fd82e-102">Bad file name or number</span></span>
<span data-ttu-id="fd82e-103">Belirtilen dosyaya erişmeye çalışırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fd82e-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="fd82e-104">Bu hata için olası nedenler arasındadır:</span><span class="sxs-lookup"><span data-stu-id="fd82e-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="fd82e-105">Belirtilmedi bir dosyanın dosya adı veya numarası ile bir deyim başvurduğu `FileOpen` içinde deyim ya da, belirtilmiş bir `FileOpen` deyimi ancak olan sonradan kapalı.</span><span class="sxs-lookup"><span data-stu-id="fd82e-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="fd82e-106">Dosya numaraları aralığının dışında bir sayı içeren bir dosyaya bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd82e-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="fd82e-107">Bir deyim için bir dosya adı veya geçersiz sayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="fd82e-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd82e-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fd82e-108">To correct this error</span></span>  
  
1. <span data-ttu-id="fd82e-109">Emin dosya adı belirtilen bir `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fd82e-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="fd82e-110">Çağrılan gerçekleştiriyorsanız `FileClose` ifadesi bağımsız değişkeni olmadan yanlışlıkla tüm açık dosyalar kapattıysanız.</span><span class="sxs-lookup"><span data-stu-id="fd82e-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="fd82e-111">Kodunuzu dosya numaraları algorithmically oluşturuyorsa numaralarının geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd82e-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="fd82e-112">Dosya adları, işletim sistemi kuralları için uygun emin olmak için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="fd82e-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd82e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd82e-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="fd82e-114">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="fd82e-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
