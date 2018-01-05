---
title: "Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f24c0625058dbd960411d5981b4e98e0e9422b99
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="03f06-102">Nasıl yapılır: Visual Basic'de Bir Diziyi Sıralama</span><span class="sxs-lookup"><span data-stu-id="03f06-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="03f06-103">Bu örnek, bir dizi bildirir `String` adlı nesneleri `zooAnimals`, bunu doldurduğundan ve alfabetik olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="03f06-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f06-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="03f06-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03f06-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="03f06-105">Compiling the Code</span></span>  
 <span data-ttu-id="03f06-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="03f06-106">This example requires:</span></span>  
  
-   <span data-ttu-id="03f06-107">Mscorlib.dll erişimi ve <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="03f06-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="03f06-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="03f06-108">Robust Programming</span></span>  
 <span data-ttu-id="03f06-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="03f06-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="03f06-110">Dizi boşsa (<xref:System.ArgumentNullException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="03f06-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="03f06-111">Dizi çok boyutlu (<xref:System.RankException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="03f06-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="03f06-112">Dizinin bir veya daha fazla öğeleri uygulamaz <xref:System.IComparable> arabirimi (<xref:System.InvalidOperationException> sınıfı)</span><span class="sxs-lookup"><span data-stu-id="03f06-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f06-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03f06-113">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="03f06-114">Diziler</span><span class="sxs-lookup"><span data-stu-id="03f06-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="03f06-115">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="03f06-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="03f06-116">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="03f06-116">Collections</span></span>](../../concepts/collections.md)  
 [<span data-ttu-id="03f06-117">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="03f06-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
