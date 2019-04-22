---
title: "Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 1e515c0f4ce8e787754c61a9b53d247fa93c49f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814386"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="f643b-102">Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f643b-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="f643b-103">Dönüştürmeniz bir `Object` başka bir veri türüne dönüştürme anahtar sözcüğü gibi kullanarak değişken [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="f643b-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f643b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f643b-104">Example</span></span>  
 <span data-ttu-id="f643b-105">Aşağıdaki örnek bir `Object` değişkenini bir `Integer` ve `String`.</span><span class="sxs-lookup"><span data-stu-id="f643b-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="f643b-106">Olduğunu biliyorsanız içeriğini bir `Object` değişken olan belirli veri türü, değişken, veri türüne dönüştürün en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="f643b-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="f643b-107">Kullanmaya devam ederseniz `Object` ya da değişken ücretler *kutulama* ve *kutudan çıkarma* (için bir değer türü) veya *geç bağlama* (için bir başvuru türü).</span><span class="sxs-lookup"><span data-stu-id="f643b-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="f643b-108">Bu işlemler, tüm ek yürütme süresi almak ve daha yavaş performans olun.</span><span class="sxs-lookup"><span data-stu-id="f643b-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f643b-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f643b-109">Compiling the Code</span></span>  
 <span data-ttu-id="f643b-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f643b-110">This example requires:</span></span>  
  
-   <span data-ttu-id="f643b-111">Bir başvuru <xref:System?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f643b-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f643b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f643b-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="f643b-113">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="f643b-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="f643b-114">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="f643b-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="f643b-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f643b-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="f643b-116">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f643b-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="f643b-117">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f643b-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="f643b-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="f643b-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f643b-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f643b-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f643b-120">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f643b-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
