---
title: "Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama"
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700972"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="a49f3-102">Nasıl yapılır: Visual Basic bir diziyi sıralama</span><span class="sxs-lookup"><span data-stu-id="a49f3-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="a49f3-103">Bu makalede, Visual Basic bir dize dizisinin nasıl sıralanacağını gösteren bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a49f3-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="a49f3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a49f3-104">Example</span></span>

<span data-ttu-id="a49f3-105">Bu örnek, `zooAnimals` adlı `String` nesnelerinin bir dizisini bildirir, onu doldurur ve alfabetik olarak sıralar:</span><span class="sxs-lookup"><span data-stu-id="a49f3-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="a49f3-106">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="a49f3-106">Robust programming</span></span>

<span data-ttu-id="a49f3-107">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="a49f3-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="a49f3-108">Dizi boş (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a49f3-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="a49f3-109">Dizi çok boyutlu (<xref:System.RankException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a49f3-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="a49f3-110">Dizinin bir veya daha fazla öğesi <xref:System.IComparable> arabirimini uygulamıyor (<xref:System.InvalidOperationException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a49f3-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="a49f3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a49f3-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a49f3-112">Diziler</span><span class="sxs-lookup"><span data-stu-id="a49f3-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="a49f3-113">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="a49f3-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="a49f3-114">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="a49f3-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="a49f3-115">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="a49f3-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
