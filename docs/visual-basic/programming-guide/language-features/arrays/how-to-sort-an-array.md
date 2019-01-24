---
title: "Nasıl yapılır: Visual Basic'te dizi Sırala"
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 0b04bfbedf9d7266d1b2e190fa85b8a64cf6efbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558442"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="41729-102">Nasıl yapılır: Visual Basic'te dizi Sırala</span><span class="sxs-lookup"><span data-stu-id="41729-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="41729-103">Bu örnek, bir dizi bildirir `String` adlı nesneleri `zooAnimals`, onu doldurur ve alfabetik olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="41729-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41729-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="41729-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41729-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="41729-105">Compiling the Code</span></span>  
 <span data-ttu-id="41729-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="41729-106">This example requires:</span></span>  
  
-   <span data-ttu-id="41729-107">Mscorlib.dll için erişim ve <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="41729-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="41729-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="41729-108">Robust Programming</span></span>  
 <span data-ttu-id="41729-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="41729-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="41729-110">Dizi boş (<xref:System.ArgumentNullException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="41729-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="41729-111">Dizi çok boyutlu (<xref:System.RankException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="41729-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="41729-112">Bir veya daha fazla öğe dizinin uygulamayın <xref:System.IComparable> arabirimi (<xref:System.InvalidOperationException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="41729-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41729-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41729-113">See also</span></span>
- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="41729-114">Diziler</span><span class="sxs-lookup"><span data-stu-id="41729-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="41729-115">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="41729-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="41729-116">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="41729-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="41729-117">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="41729-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
