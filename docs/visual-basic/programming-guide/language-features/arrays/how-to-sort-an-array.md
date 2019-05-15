---
title: "Nasıl yapılır: Visual Basic'te dizi Sırala"
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 680f488a98d6e7e31b3d077843514fd12f75481c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586436"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="9d8c7-102">Nasıl yapılır: Visual Basic'te dizi Sırala</span><span class="sxs-lookup"><span data-stu-id="9d8c7-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="9d8c7-103">Bu örnek, bir dizi bildirir `String` adlı nesneleri `zooAnimals`, onu doldurur ve alfabetik olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="9d8c7-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d8c7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d8c7-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d8c7-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9d8c7-105">Compiling the Code</span></span>  
 <span data-ttu-id="9d8c7-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9d8c7-106">This example requires:</span></span>  
  
- <span data-ttu-id="9d8c7-107">Erişim <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9d8c7-107">Access to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9d8c7-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9d8c7-108">Robust Programming</span></span>  
 <span data-ttu-id="9d8c7-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="9d8c7-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9d8c7-110">Dizi boş (<xref:System.ArgumentNullException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="9d8c7-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
- <span data-ttu-id="9d8c7-111">Dizi çok boyutlu (<xref:System.RankException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="9d8c7-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
- <span data-ttu-id="9d8c7-112">Bir veya daha fazla öğe dizinin uygulamayın <xref:System.IComparable> arabirimi (<xref:System.InvalidOperationException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="9d8c7-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8c7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d8c7-113">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9d8c7-114">Diziler</span><span class="sxs-lookup"><span data-stu-id="9d8c7-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9d8c7-115">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="9d8c7-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="9d8c7-116">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="9d8c7-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="9d8c7-117">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d8c7-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
