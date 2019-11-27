---
title: 'Nasıl yapılır: bir nesneyi başka bir türe dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 19708d03b0514f4572c2baa53e05781e5949766b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350067"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="75739-102">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="75739-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="75739-103">[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)gibi bir dönüştürme anahtar sözcüğünü kullanarak bir `Object` değişkenini başka bir veri türüne dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="75739-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75739-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="75739-104">Example</span></span>  
 <span data-ttu-id="75739-105">Aşağıdaki örnek bir `Object` değişkenini `Integer` ve `String`dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="75739-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="75739-106">Bir `Object` değişkeninin içeriğinin belirli bir veri türünde olduğunu biliyorsanız, değişkeni bu veri türüne dönüştürmek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="75739-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="75739-107">`Object` değişkenini kullanmaya devam ederseniz, *kutulama* ve *kutudan* çıkarma (bir değer türü için) ya da *geç bağlama* (bir başvuru türü için) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="75739-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="75739-108">Bu işlemler, daha fazla yürütme süresi alır ve performansınızı daha yavaş hale getirir.</span><span class="sxs-lookup"><span data-stu-id="75739-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75739-109">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="75739-109">Compiling the Code</span></span>  
 <span data-ttu-id="75739-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="75739-110">This example requires:</span></span>  
  
- <span data-ttu-id="75739-111"><xref:System?displayProperty=nameWithType> ad alanına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="75739-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75739-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75739-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="75739-113">Visual Basic dönüşümler yazın</span><span class="sxs-lookup"><span data-stu-id="75739-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="75739-114">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="75739-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="75739-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="75739-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="75739-116">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="75739-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="75739-117">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="75739-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="75739-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="75739-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="75739-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="75739-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="75739-120">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="75739-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
