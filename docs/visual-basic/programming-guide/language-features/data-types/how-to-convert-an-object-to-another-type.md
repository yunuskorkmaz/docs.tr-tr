---
title: "Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: f168b3021ee1dbe3c82edc22fc779767c30446b8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912019"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="84900-102">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="84900-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="84900-103">Dönüştürmeniz bir `Object` başka bir veri türüne dönüştürme anahtar sözcüğü gibi kullanarak değişken [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="84900-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84900-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="84900-104">Example</span></span>  
 <span data-ttu-id="84900-105">Aşağıdaki örnek bir `Object` değişkenini bir `Integer` ve `String`.</span><span class="sxs-lookup"><span data-stu-id="84900-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="84900-106">Olduğunu biliyorsanız içeriğini bir `Object` değişken olan belirli veri türü, değişken, veri türüne dönüştürün en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="84900-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="84900-107">Kullanmaya devam ederseniz `Object` ya da değişken ücretler *kutulama* ve *kutudan çıkarma* (için bir değer türü) veya *geç bağlama* (için bir başvuru türü).</span><span class="sxs-lookup"><span data-stu-id="84900-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="84900-108">Bu işlemler, tüm ek yürütme süresi almak ve daha yavaş performans olun.</span><span class="sxs-lookup"><span data-stu-id="84900-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84900-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="84900-109">Compiling the Code</span></span>  
 <span data-ttu-id="84900-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="84900-110">This example requires:</span></span>  
  
-   <span data-ttu-id="84900-111">Bir başvuru <xref:System?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="84900-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84900-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84900-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="84900-113">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="84900-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="84900-114">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="84900-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="84900-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="84900-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="84900-116">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="84900-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="84900-117">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="84900-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="84900-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="84900-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="84900-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="84900-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="84900-120">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="84900-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
