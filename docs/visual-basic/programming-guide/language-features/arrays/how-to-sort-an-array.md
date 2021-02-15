---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Visual Basic bir diziyi sıralama'
title: 'Nasıl yapılır: Dizi Sıralama'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: ea030b63dbbb5f5ea1d6160757afe2e9b58f7c21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462769"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="ee5e1-103">Nasıl yapılır: Visual Basic bir diziyi sıralama</span><span class="sxs-lookup"><span data-stu-id="ee5e1-103">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="ee5e1-104">Bu makalede, Visual Basic bir dize dizisinin nasıl sıralanacağını gösteren bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ee5e1-104">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="ee5e1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee5e1-105">Example</span></span>

<span data-ttu-id="ee5e1-106">Bu örnek `String` , adlı bir nesne dizisi bildirir `zooAnimals` , onu doldurur ve alfabetik olarak sıralar:</span><span class="sxs-lookup"><span data-stu-id="ee5e1-106">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="ee5e1-107">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="ee5e1-107">Robust programming</span></span>

<span data-ttu-id="ee5e1-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ee5e1-108">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="ee5e1-109">Dizi boş ( <xref:System.ArgumentNullException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="ee5e1-109">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="ee5e1-110">Dizi çok boyutlu ( <xref:System.RankException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="ee5e1-110">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="ee5e1-111">Dizinin bir veya daha fazla öğesi <xref:System.IComparable> arabirimini uygulamıyor ( <xref:System.InvalidOperationException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="ee5e1-111">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee5e1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee5e1-112">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ee5e1-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="ee5e1-113">Arrays</span></span>](index.md)
- [<span data-ttu-id="ee5e1-114">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="ee5e1-114">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="ee5e1-115">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="ee5e1-115">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="ee5e1-116">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="ee5e1-116">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
