---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: b3778a170759f685db78e7dcde219138196f9eca
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344195"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="4af31-102">Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4af31-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="4af31-103">Bir nesne değişkeni, başka bir yerde depolanan veriler için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="4af31-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="4af31-104">Çalışma zamanı sırasında verilerin türü değişebilir.</span><span class="sxs-lookup"><span data-stu-id="4af31-104">The type of that data can change during run time.</span></span> <span data-ttu-id="4af31-105">Herhangi bir anda, geçerli çalışma zamanı türünü veya geçerli çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını [bulmak için <xref:System.Type.GetTypeCode%2A>](../../../../visual-basic/language-reference/operators/typeof-operator.md) yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4af31-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="4af31-106">Şu anda başvurduğu bir nesne değişkeninin tam türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="4af31-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="4af31-107">Nesne değişkeninde, bir <xref:System.Type?displayProperty=nameWithType> nesnesini almak için <xref:System.Object.GetType%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4af31-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="4af31-108"><xref:System.Type?displayProperty=nameWithType> sınıfında, nesne türü için <xref:System.TypeCode> numaralandırma değerini almak üzere <xref:System.Type.GetTypeCode%2A> paylaşılan yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="4af31-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="4af31-109"><xref:System.TypeCode> numaralandırma değerini, `Double`gibi, hangi numaralandırma üyelerinin ilgi alanına göre test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4af31-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="4af31-110">Bir nesne değişkeninin türünün belirtilen tür ile uyumlu olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="4af31-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="4af31-111">Nesneyi bir `TypeOf`...`Is` ifadesi ile test etmek için with [işleci](../../../../visual-basic/language-reference/operators/is-operator.md) ile birlikte `TypeOf` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4af31-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="4af31-112">`TypeOf`...`Is` ifadesi, nesnenin çalışma zamanı türü belirtilen türle uyumluysa `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="4af31-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="4af31-113">Uyumluluk ölçütü, belirtilen türün bir sınıf, yapı veya arabirim olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4af31-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="4af31-114">Genel olarak, nesne aynı türde ise, öğesinden devralır veya belirtilen türü uygularsa türler uyumlu olur.</span><span class="sxs-lookup"><span data-stu-id="4af31-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="4af31-115">Daha fazla bilgi için bkz. [typeof işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4af31-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="4af31-116">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="4af31-116">Compile the code</span></span>

<span data-ttu-id="4af31-117">Belirtilen türün bir değişken veya ifade olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4af31-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="4af31-118">Sınıf, yapı veya arabirim gibi tanımlı bir türün adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4af31-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="4af31-119">Bu, `Integer` ve `String`gibi iç türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4af31-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4af31-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4af31-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="4af31-121">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="4af31-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="4af31-122">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="4af31-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="4af31-123">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="4af31-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
