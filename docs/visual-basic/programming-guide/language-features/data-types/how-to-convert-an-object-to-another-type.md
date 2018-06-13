---
title: "Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 367991e4bbca710df54edf73179f855ff79bb56e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647624"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="d370f-102">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d370f-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="d370f-103">Dönüştürdüğünüz bir `Object` başka bir veri türüne dönüştürme anahtar sözcüğü gibi kullanarak değişken [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="d370f-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d370f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d370f-104">Example</span></span>  
 <span data-ttu-id="d370f-105">Aşağıdaki örnek dönüştürür bir `Object` için değişken bir `Integer` ve `String`.</span><span class="sxs-lookup"><span data-stu-id="d370f-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="d370f-106">Biliyorsanız içeriğini bir `Object` değişken olan belirli veri türü, değişken, veri türüne dönüştürün daha iyi olur.</span><span class="sxs-lookup"><span data-stu-id="d370f-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="d370f-107">Kullanmaya devam ederseniz `Object` ya da değişken, tabi *kutulama* ve *kutudan çıkarma* (için bir değer türü) veya *geç bağlama* (için bir başvuru türü).</span><span class="sxs-lookup"><span data-stu-id="d370f-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="d370f-108">Bu işlemler, tüm ek yürütme süresi kılın ve daha yavaş performans yapın.</span><span class="sxs-lookup"><span data-stu-id="d370f-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d370f-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d370f-109">Compiling the Code</span></span>  
 <span data-ttu-id="d370f-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d370f-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d370f-111">Bir başvuru <xref:System?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d370f-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d370f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d370f-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="d370f-113">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d370f-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="d370f-114">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d370f-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="d370f-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d370f-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="d370f-116">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d370f-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="d370f-117">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d370f-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="d370f-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="d370f-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="d370f-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d370f-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="d370f-120">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d370f-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
