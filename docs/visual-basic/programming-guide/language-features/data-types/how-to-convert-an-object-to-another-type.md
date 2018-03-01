---
title: "Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="56a76-102">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="56a76-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="56a76-103">Dönüştürdüğünüz bir `Object` başka bir veri türüne dönüştürme anahtar sözcüğü gibi kullanarak değişken [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="56a76-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56a76-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="56a76-104">Example</span></span>  
 <span data-ttu-id="56a76-105">Aşağıdaki örnek dönüştürür bir `Object` için değişken bir `Integer` ve `String`.</span><span class="sxs-lookup"><span data-stu-id="56a76-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="56a76-106">Biliyorsanız içeriğini bir `Object` değişken olan belirli veri türü, değişken, veri türüne dönüştürün daha iyi olur.</span><span class="sxs-lookup"><span data-stu-id="56a76-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="56a76-107">Kullanmaya devam ederseniz `Object` ya da değişken, tabi *kutulama* ve *kutudan çıkarma* (için bir değer türü) veya *geç bağlama* (için bir başvuru türü).</span><span class="sxs-lookup"><span data-stu-id="56a76-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="56a76-108">Bu işlemler, tüm ek yürütme süresi kılın ve daha yavaş performans yapın.</span><span class="sxs-lookup"><span data-stu-id="56a76-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56a76-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="56a76-109">Compiling the Code</span></span>  
 <span data-ttu-id="56a76-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="56a76-110">This example requires:</span></span>  
  
-   <span data-ttu-id="56a76-111">Bir başvuru <xref:System?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="56a76-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a76-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56a76-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="56a76-113">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="56a76-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="56a76-114">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="56a76-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="56a76-115">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="56a76-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="56a76-116">Dizeler ve diğer türleri arasında dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="56a76-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="56a76-117">Dizi dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="56a76-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="56a76-118">Yapıları</span><span class="sxs-lookup"><span data-stu-id="56a76-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="56a76-119">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="56a76-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="56a76-120">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="56a76-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
