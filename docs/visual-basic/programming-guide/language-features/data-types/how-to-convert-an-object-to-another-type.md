---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic bir nesneyi başka bir türe dönüştürme'
title: 'Nasıl yapılır: Nesneyi Başka Bir Türe Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: d6840cfd440483720f8ca9a0fa0140c3727a8688
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484034"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="b04e0-103">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b04e0-103">How to: Convert an Object to Another Type in Visual Basic</span></span>

<span data-ttu-id="b04e0-104">`Object` [CType işlevi](../../../language-reference/functions/ctype-function.md)gibi bir dönüştürme anahtar sözcüğünü kullanarak bir değişkeni başka bir veri türüne dönüştürürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b04e0-104">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b04e0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b04e0-105">Example</span></span>  

 <span data-ttu-id="b04e0-106">Aşağıdaki örnek bir değişkenini bir `Object` ve öğesine dönüştürür `Integer` `String` .</span><span class="sxs-lookup"><span data-stu-id="b04e0-106">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="b04e0-107">Bir `Object` değişkenin içeriğinin belirli bir veri türünde olduğunu biliyorsanız, değişkeni bu veri türüne dönüştürmek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="b04e0-107">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="b04e0-108">Değişkenini kullanmaya devam ederseniz `Object` , *kutulama* ve *kutudan* çıkarma (bir değer türü için) ya da *geç bağlama* (bir başvuru türü için) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b04e0-108">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="b04e0-109">Bu işlemler, daha fazla yürütme süresi alır ve performansınızı daha yavaş hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b04e0-109">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="b04e0-110">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="b04e0-110">Compile the code</span></span>  

 <span data-ttu-id="b04e0-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b04e0-111">This example requires:</span></span>  
  
- <span data-ttu-id="b04e0-112"><xref:System?displayProperty=nameWithType>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="b04e0-112">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04e0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b04e0-113">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="b04e0-114">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="b04e0-114">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="b04e0-115">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b04e0-115">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b04e0-116">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b04e0-116">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="b04e0-117">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b04e0-117">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="b04e0-118">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b04e0-118">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="b04e0-119">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b04e0-119">Structures</span></span>](structures.md)
- [<span data-ttu-id="b04e0-120">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b04e0-120">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="b04e0-121">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b04e0-121">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
