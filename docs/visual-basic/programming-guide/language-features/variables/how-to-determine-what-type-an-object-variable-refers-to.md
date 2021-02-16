---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir nesne değişkeninin hangi türe başvurduğunu belirleme (Visual Basic)'
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 699a8c5c075fc923a61a66f617c255f193cd8797
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481928"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="873de-103">Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="873de-103">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="873de-104">Bir nesne değişkeni, başka bir yerde depolanan veriler için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="873de-104">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="873de-105">Çalışma zamanı sırasında verilerin türü değişebilir.</span><span class="sxs-lookup"><span data-stu-id="873de-105">The type of that data can change during run time.</span></span> <span data-ttu-id="873de-106">Herhangi bir anda, geçerli <xref:System.Type.GetTypeCode%2A> çalışma zamanı türünü veya geçerli çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını bulmak Için [typeof işlecini](../../../language-reference/operators/typeof-operator.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="873de-106">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="873de-107">Şu anda başvurduğu bir nesne değişkeninin tam türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="873de-107">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="873de-108">Nesne değişkeninde, <xref:System.Object.GetType%2A> bir nesneyi almak için yöntemini çağırın <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="873de-108">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="873de-109"><xref:System.Type?displayProperty=nameWithType>Sınıfında, <xref:System.Type.GetTypeCode%2A> <xref:System.TypeCode> nesne türü için numaralandırma değerini almak üzere paylaşılan yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="873de-109">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="873de-110"><xref:System.TypeCode>Sabit listesi üyelerinin ilgi çekici olduğunu, örneğin olduğu gibi test edebilirsiniz `Double` .</span><span class="sxs-lookup"><span data-stu-id="873de-110">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="873de-111">Bir nesne değişkeninin türünün belirtilen tür ile uyumlu olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="873de-111">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="873de-112">`TypeOf`Nesneyi bir [](../../../language-reference/operators/is-operator.md) `TypeOf` ... ifadesi Ile test etmek için, işleç işleç ile birlikte kullanın `Is` .</span><span class="sxs-lookup"><span data-stu-id="873de-112">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="873de-113">`TypeOf`... `Is` İfadesi, `True` nesnenin çalışma zamanı türünün belirtilen türle uyumlu olup olmadığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="873de-113">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="873de-114">Uyumluluk ölçütü, belirtilen türün bir sınıf, yapı veya arabirim olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="873de-114">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="873de-115">Genel olarak, nesne aynı türde ise, öğesinden devralır veya belirtilen türü uygularsa türler uyumlu olur.</span><span class="sxs-lookup"><span data-stu-id="873de-115">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="873de-116">Daha fazla bilgi için bkz. [typeof işleci](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="873de-116">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="873de-117">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="873de-117">Compile the code</span></span>

<span data-ttu-id="873de-118">Belirtilen türün bir değişken veya ifade olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="873de-118">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="873de-119">Sınıf, yapı veya arabirim gibi tanımlı bir türün adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="873de-119">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="873de-120">Bu, ve gibi iç türleri `Integer` içerir `String` .</span><span class="sxs-lookup"><span data-stu-id="873de-120">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="873de-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="873de-121">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="873de-122">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="873de-122">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="873de-123">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="873de-123">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="873de-124">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="873de-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
