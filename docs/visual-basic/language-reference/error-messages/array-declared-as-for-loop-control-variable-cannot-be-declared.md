---
title: For döngüsü denetim değişkeni olarak bildirilen dizi başlangıç boyutuyla bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: f6cf397b1e76313ab399d5e39a43ae0263df619c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587990"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="f849b-102">For döngüsü denetim değişkeni olarak bildirilen dizi başlangıç boyutuyla bildirilemez</span><span class="sxs-lookup"><span data-stu-id="f849b-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="f849b-103">A `For Each` döngü kullanan bir dizi olarak kendi *öğesi* yineleme değişkeni, ancak bu diziyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="f849b-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="f849b-104">Aşağıdaki deyimleri nasıl bu hatayı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f849b-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="f849b-105">İlk `For Each` açıklamadır erişim öğeleri doğru şekilde `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="f849b-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="f849b-106">İkinci `For Each` deyimi bu hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f849b-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="f849b-107">**Hata Kimliği:** BC32039</span><span class="sxs-lookup"><span data-stu-id="f849b-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f849b-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f849b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="f849b-109">Başlatma bildiriminden kaldırmak *öğesi* yineleme değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f849b-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f849b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f849b-110">See Also</span></span>  
 [<span data-ttu-id="f849b-111">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="f849b-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="f849b-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="f849b-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="f849b-113">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="f849b-113">Collections</span></span>](../../../standard/collections/index.md)
