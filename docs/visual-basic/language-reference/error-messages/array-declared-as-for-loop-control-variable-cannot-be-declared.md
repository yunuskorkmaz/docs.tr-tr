---
title: For döngüsü denetim değişkeni olarak bildirilen dizi başlangıç boyutuyla bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843584"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="dd9da-102">For döngüsü denetim değişkeni olarak bildirilen dizi başlangıç boyutuyla bildirilemez</span><span class="sxs-lookup"><span data-stu-id="dd9da-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="dd9da-103">A `For Each` döngü kullanan bir dizi olarak kendi *öğesi* yineleme değişkeni, ancak bu diziyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="dd9da-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="dd9da-104">Aşağıdaki deyimleri nasıl bu hatayı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd9da-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="dd9da-105">İlk `For Each` deyimdir erişim öğeleri doğru şekilde `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="dd9da-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="dd9da-106">İkinci `For Each` deyimi bu hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd9da-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="dd9da-107">**Hata Kimliği:** BC32039</span><span class="sxs-lookup"><span data-stu-id="dd9da-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd9da-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dd9da-108">To correct this error</span></span>  
  
-   <span data-ttu-id="dd9da-109">Başlatma bildirimden kaldırmak *öğesi* yineleme değişkeni.</span><span class="sxs-lookup"><span data-stu-id="dd9da-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9da-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd9da-110">See also</span></span>

- [<span data-ttu-id="dd9da-111">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="dd9da-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="dd9da-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="dd9da-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="dd9da-113">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="dd9da-113">Collections</span></span>](../../../standard/collections/index.md)
