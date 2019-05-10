---
title: 'Nasıl yapılır: Bir diziyi başka diziye (Visual Basic) atama'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: a39888f19e5033a5c6622313fb7451d6463b2f7c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64858878"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="355d1-102">Nasıl yapılır: Bir diziyi başka diziye (Visual Basic) atama</span><span class="sxs-lookup"><span data-stu-id="355d1-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="355d1-103">Diziler nesneler olduğundan atama deyimleri diğer nesne türleri gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355d1-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="355d1-104">Bir dizi değişkenini dizi öğeleri ve boyut sayısı ve uzunluk bilgileri oluşturan veri için bir işaretçi tutar ve bu işaretçi atama kopyalar.</span><span class="sxs-lookup"><span data-stu-id="355d1-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="355d1-105">Bir diziyi başka diziye atama için</span><span class="sxs-lookup"><span data-stu-id="355d1-105">To assign one array to another array</span></span>

1. <span data-ttu-id="355d1-106">İki dizi aynı boyut sayısı (boyut sayısı) ve uyumlu öğe veri türleri olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="355d1-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="355d1-107">Hedef dizi için kaynak dizisi atamak için bir standart atama ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="355d1-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="355d1-108">Parantezler ile ya da dizi adı izlemeyin.</span><span class="sxs-lookup"><span data-stu-id="355d1-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="355d1-109">Bir diziyi başka birine atadığınızda, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="355d1-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="355d1-110">**Eşit sıralamalara sahip.**</span><span class="sxs-lookup"><span data-stu-id="355d1-110">**Equal Ranks.**</span></span> <span data-ttu-id="355d1-111">Hedef dizinin boyut (boyut sayısı), kaynak diziden aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="355d1-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="355d1-112">Sıralamalara sahip iki dizinin eşitse sağlanan boyutları eşit olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="355d1-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="355d1-113">Atama sırasında belirli bir boyut içindeki öğelerin sayısını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355d1-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="355d1-114">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="355d1-114">**Element Types.**</span></span> <span data-ttu-id="355d1-115">Her iki ya da bir dizi olmalıdır *başvuru türüne* öğelerin veya her iki dizide olmalıdır *değer türü* öğeleri.</span><span class="sxs-lookup"><span data-stu-id="355d1-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="355d1-116">Daha fazla bilgi için [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="355d1-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="355d1-117">Her iki dizide değer türü öğeleri varsa öğe veri türleri tam olarak aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="355d1-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="355d1-118">Bunun tek istisnası, bir dizi atayabilirsiniz olan `Enum` , temel türü bir dizi öğelerine `Enum`.</span><span class="sxs-lookup"><span data-stu-id="355d1-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="355d1-119">Her iki dizide öğe türü başvurusu varsa, kaynak öğe türü hedef öğenin türünden türetilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="355d1-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="355d1-120">Bu durumda, iki dizi öğeleri olarak aynı devralma ilişkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="355d1-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="355d1-121">Bu adlandırılır *dizi kovaryansı*.</span><span class="sxs-lookup"><span data-stu-id="355d1-121">This is called *array covariance*.</span></span>

<span data-ttu-id="355d1-122">Derleyici, veri türleri uyumlu değilse, yukarıdaki kuralları, örneğin ihlal bir hata veya sıralamalara sahip eşit bildirir.</span><span class="sxs-lookup"><span data-stu-id="355d1-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="355d1-123">Hata işleme kodunuzda ödev denemeden önce diziler uyumlu olduğundan emin olmak için ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="355d1-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="355d1-124">Ayrıca [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md) bir özel durum kaçınmak istiyorsanız anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="355d1-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="355d1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="355d1-125">See also</span></span>

- [<span data-ttu-id="355d1-126">Diziler</span><span class="sxs-lookup"><span data-stu-id="355d1-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="355d1-127">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="355d1-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="355d1-128">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="355d1-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="355d1-129">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="355d1-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
