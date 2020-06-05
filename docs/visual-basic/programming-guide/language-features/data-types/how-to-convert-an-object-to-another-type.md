---
title: 'Nasıl yapılır: Nesneyi Başka Bir Türe Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393967"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="51781-102">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="51781-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="51781-103">`Object` [CType işlevi](../../../language-reference/functions/ctype-function.md)gibi bir dönüştürme anahtar sözcüğünü kullanarak bir değişkeni başka bir veri türüne dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="51781-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51781-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="51781-104">Example</span></span>  
 <span data-ttu-id="51781-105">Aşağıdaki örnek bir değişkenini bir `Object` ve öğesine dönüştürür `Integer` `String` .</span><span class="sxs-lookup"><span data-stu-id="51781-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="51781-106">Bir `Object` değişkenin içeriğinin belirli bir veri türünde olduğunu biliyorsanız, değişkeni bu veri türüne dönüştürmek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="51781-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="51781-107">Değişkenini kullanmaya devam ederseniz `Object` , *kutulama* ve *kutudan* çıkarma (bir değer türü için) ya da *geç bağlama* (bir başvuru türü için) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="51781-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="51781-108">Bu işlemler, daha fazla yürütme süresi alır ve performansınızı daha yavaş hale getirir.</span><span class="sxs-lookup"><span data-stu-id="51781-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="51781-109">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="51781-109">Compile the code</span></span>  
 <span data-ttu-id="51781-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="51781-110">This example requires:</span></span>  
  
- <span data-ttu-id="51781-111"><xref:System?displayProperty=nameWithType>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="51781-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51781-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51781-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="51781-113">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="51781-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="51781-114">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="51781-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="51781-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="51781-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="51781-116">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="51781-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="51781-117">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="51781-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="51781-118">Yapılar</span><span class="sxs-lookup"><span data-stu-id="51781-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="51781-119">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="51781-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="51781-120">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="51781-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
