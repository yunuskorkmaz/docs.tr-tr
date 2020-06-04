---
title: 'Nasıl yapılır: Bir Diziyi Başka Diziye Atama'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413085"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="11a15-102">Nasıl yapılır: Bir Diziyi Başka Diziye Atama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11a15-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="11a15-103">Diziler nesneler olduğundan, bunları diğer nesne türleri gibi atama deyimleriyle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a15-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="11a15-104">Dizi değişkeni, dizi öğeleri ve derecelendirme ve uzunluk bilgilerini constituting veri için bir işaretçi tutar ve bir atama yalnızca bu işaretçiyi kopyalar.</span><span class="sxs-lookup"><span data-stu-id="11a15-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="11a15-105">Bir diziyi başka bir diziye atamak için</span><span class="sxs-lookup"><span data-stu-id="11a15-105">To assign one array to another array</span></span>

1. <span data-ttu-id="11a15-106">İki dizinin aynı dereceye (boyut sayısına) ve uyumlu öğe veri türlerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="11a15-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="11a15-107">Kaynak diziyi hedef diziye atamak için standart atama ekstresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="11a15-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="11a15-108">Parantez ile dizi adını takip etmez.</span><span class="sxs-lookup"><span data-stu-id="11a15-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="11a15-109">Bir diziyi diğerine atadığınızda, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="11a15-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="11a15-110">**Eşit dereceleri.**</span><span class="sxs-lookup"><span data-stu-id="11a15-110">**Equal Ranks.**</span></span> <span data-ttu-id="11a15-111">Hedef dizinin derecesi (boyut sayısı), kaynak dizinin ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11a15-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="11a15-112">İki dizinin dereceleri eşitse, boyutların eşit olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="11a15-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="11a15-113">Belirli boyuttaki öğelerin sayısı atama sırasında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="11a15-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="11a15-114">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="11a15-114">**Element Types.**</span></span> <span data-ttu-id="11a15-115">Her iki dizide de *başvuru türü* öğeler olmalıdır ya da her iki dizi de *değer türü* öğelerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11a15-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="11a15-116">Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](../data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="11a15-116">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="11a15-117">Her iki dizide de değer türü öğeler varsa, öğe veri türleri tam olarak aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11a15-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="11a15-118">Bunun tek istisnası, bir dizi `Enum` öğeyi temel türünün bir dizisine atayabilmenizi sağlar `Enum` .</span><span class="sxs-lookup"><span data-stu-id="11a15-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="11a15-119">Her iki dizide de başvuru türü öğeleri varsa, kaynak öğe türünün hedef öğe türünden türetilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="11a15-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="11a15-120">Bu durumda, iki dizi öğeleriyle aynı devralma ilişkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="11a15-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="11a15-121">Buna *dizi Kovaryans*adı verilir.</span><span class="sxs-lookup"><span data-stu-id="11a15-121">This is called *array covariance*.</span></span>

<span data-ttu-id="11a15-122">Yukarıdaki kurallar ihlal edildiğinde derleyici bir hata bildirir, örneğin, veri türleri uyumlu değilse veya derecelendirmelerinin eşit olduğu durumlarda.</span><span class="sxs-lookup"><span data-stu-id="11a15-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="11a15-123">Bir atamayı denemeden önce dizilerin uyumlu olduğundan emin olmak için kodunuza hata işleme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a15-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="11a15-124">Özel durum oluşturmamak istiyorsanız [TryCast İşleci](../../../language-reference/operators/trycast-operator.md) anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a15-124">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="11a15-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a15-125">See also</span></span>

- [<span data-ttu-id="11a15-126">Diziler</span><span class="sxs-lookup"><span data-stu-id="11a15-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="11a15-127">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="11a15-127">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="11a15-128">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="11a15-128">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="11a15-129">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="11a15-129">Array Conversions</span></span>](../data-types/array-conversions.md)
