---
title: 'Nasıl yapılır: bir nesneyi başka bir türe dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341582"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="84e29-102">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="84e29-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="84e29-103">[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)gibi bir dönüştürme anahtar sözcüğünü kullanarak bir `Object` değişkenini başka bir veri türüne dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="84e29-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e29-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="84e29-104">Example</span></span>  
 <span data-ttu-id="84e29-105">Aşağıdaki örnek bir `Object` değişkenini `Integer` ve `String`dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="84e29-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="84e29-106">Bir `Object` değişkeninin içeriğinin belirli bir veri türünde olduğunu biliyorsanız, değişkeni bu veri türüne dönüştürmek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="84e29-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="84e29-107">`Object` değişkenini kullanmaya devam ederseniz, *kutulama* ve *kutudan* çıkarma (bir değer türü için) ya da *geç bağlama* (bir başvuru türü için) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="84e29-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="84e29-108">Bu işlemler, daha fazla yürütme süresi alır ve performansınızı daha yavaş hale getirir.</span><span class="sxs-lookup"><span data-stu-id="84e29-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="84e29-109">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="84e29-109">Compile the code</span></span>  
 <span data-ttu-id="84e29-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="84e29-110">This example requires:</span></span>  
  
- <span data-ttu-id="84e29-111"><xref:System?displayProperty=nameWithType> ad alanına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="84e29-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e29-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84e29-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="84e29-113">Visual Basic dönüşümler yazın</span><span class="sxs-lookup"><span data-stu-id="84e29-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="84e29-114">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="84e29-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="84e29-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="84e29-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="84e29-116">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="84e29-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="84e29-117">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="84e29-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="84e29-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="84e29-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="84e29-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="84e29-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="84e29-120">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="84e29-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
