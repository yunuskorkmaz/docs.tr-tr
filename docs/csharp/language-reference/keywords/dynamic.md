---
title: dinamik - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: d2aef5b2ed291aab917573408abf26b9fbedfbd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661782"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="59a86-102">dynamic (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="59a86-102">dynamic (C# Reference)</span></span>

<span data-ttu-id="59a86-103">`dynamic` Türü içinde gerçekleşir derleme zamanı tür denetimini atlamasına için işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59a86-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="59a86-104">Bunun yerine, bu işlemlerin çalışma zamanında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="59a86-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="59a86-105">`dynamic` Türü Office Otomasyon API'leri gibi COM API'leri ve aynı zamanda IronPython kitaplıkları gibi dinamik API'lerine ve erişim HTML belge nesne modeli (DOM) basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="59a86-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="59a86-106">Tür `dynamic` türü gibi davranır `object` çoğu durumda.</span><span class="sxs-lookup"><span data-stu-id="59a86-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="59a86-107">Ancak, türündeki ifadeler içeren işlemler `dynamic` değil çözümlenir veya derleyici tarafından teslim türü.</span><span class="sxs-lookup"><span data-stu-id="59a86-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="59a86-108">Çalışma zamanı derleyici paketleri birlikte bilgi işlemi ve bu bilgileri daha sonra işlemi değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59a86-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="59a86-109">Türü değişkenlerindeki işleminin bir parçası olarak `dynamic` türündeki değişkenler derlenmiş `object`.</span><span class="sxs-lookup"><span data-stu-id="59a86-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="59a86-110">Bu nedenle, yazın `dynamic` yalnızca çalışma zamanında değil derleme zamanında var.</span><span class="sxs-lookup"><span data-stu-id="59a86-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="59a86-111">Aşağıdaki örnek türünün değişkenini karşılaştırır `dynamic` türünde bir değişkene `object`.</span><span class="sxs-lookup"><span data-stu-id="59a86-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="59a86-112">Derleme zamanında her bir değişken türünü doğrulamak için üzerine fare işaretçisini getirin `dyn` veya `obj` içinde `WriteLine` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="59a86-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="59a86-113">IntelliSense gösterir **dinamik** için `dyn` ve **nesne** için `obj`.</span><span class="sxs-lookup"><span data-stu-id="59a86-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="59a86-114">`WriteLine` Deyimleri çalışma zamanı türlerini görüntüler `dyn` ve `obj`.</span><span class="sxs-lookup"><span data-stu-id="59a86-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="59a86-115">Bu noktada, her ikisi de aynı türde olan tamsayı.</span><span class="sxs-lookup"><span data-stu-id="59a86-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="59a86-116">Aşağıdaki çıkış üretilir:</span><span class="sxs-lookup"><span data-stu-id="59a86-116">The following output is produced:</span></span>

`System.Int32`

`System.Int32`

<span data-ttu-id="59a86-117">Arasındaki farkı görmek için `dyn` ve `obj` derleme zamanında bildirimler arasında aşağıdaki iki satırı ekleyin ve `WriteLine` önceki örnekte deyimleri.</span><span class="sxs-lookup"><span data-stu-id="59a86-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="59a86-118">Derleyici Hatası tamsayı ve bir nesne ifadesinde denenen eklenmesi için bildirilen `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="59a86-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="59a86-119">Ancak, herhangi bir hata için bildirilen `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="59a86-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="59a86-120">İçeren ifade `dyn` çünkü derleme zamanında işaretlenmediği türünü `dyn` olduğu `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="59a86-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

## <a name="context"></a><span data-ttu-id="59a86-121">Bağlam</span><span class="sxs-lookup"><span data-stu-id="59a86-121">Context</span></span>

<span data-ttu-id="59a86-122">`dynamic` Anahtar sözcüğü, doğrudan veya aşağıdaki durumlarda oluşturulmuş bir türü bir bileşeni olarak görünebilir:</span><span class="sxs-lookup"><span data-stu-id="59a86-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>

- <span data-ttu-id="59a86-123">Bildirimler, bir özellik, alan, dizin oluşturucu, parametre türü olarak dönüş değeri, yerel değişken veya kısıtlama türü.</span><span class="sxs-lookup"><span data-stu-id="59a86-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="59a86-124">Aşağıdaki sınıf tanımı kullanan `dynamic` birkaç farklı bildirimlerinde.</span><span class="sxs-lookup"><span data-stu-id="59a86-124">The following class definition uses `dynamic` in several different declarations.</span></span>

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- <span data-ttu-id="59a86-125">Açık tür dönüştürmeleri içinde bir dönüştürmenin hedef türü.</span><span class="sxs-lookup"><span data-stu-id="59a86-125">In explicit type conversions, as the target type of a conversion.</span></span>

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- <span data-ttu-id="59a86-126">Burada türleri hizmet değerler olarak gibi sağ tarafında bağlamda bir `is` işleci veya bir `as` işleci veya bağımsız değişken olarak `typeof` kapsamında oluşturulan bir tür.</span><span class="sxs-lookup"><span data-stu-id="59a86-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="59a86-127">Örneğin, `dynamic` aşağıdaki ifadelerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59a86-127">For example, `dynamic` can be used in the following expressions.</span></span>

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a><span data-ttu-id="59a86-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="59a86-128">Example</span></span>

<span data-ttu-id="59a86-129">Aşağıdaki örnekte `dynamic` birkaç bildirimlerinde.</span><span class="sxs-lookup"><span data-stu-id="59a86-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="59a86-130">`Main` Yöntemi de derleme zamanı tür denetimini çalışma zamanı tür denetimi ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="59a86-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

<span data-ttu-id="59a86-131">Daha fazla bilgi ve örnekler için bkz. [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="59a86-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59a86-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59a86-132">See also</span></span>

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="59a86-133">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="59a86-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="59a86-134">object</span><span class="sxs-lookup"><span data-stu-id="59a86-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)
- [<span data-ttu-id="59a86-135">is</span><span class="sxs-lookup"><span data-stu-id="59a86-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="59a86-136">as</span><span class="sxs-lookup"><span data-stu-id="59a86-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)
- [<span data-ttu-id="59a86-137">typeof</span><span class="sxs-lookup"><span data-stu-id="59a86-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
- [<span data-ttu-id="59a86-138">Nasıl yapılır: Desen eşleştirme, kullanarak güvenli bir şekilde atama, ve işleçler</span><span class="sxs-lookup"><span data-stu-id="59a86-138">How to: Safely cast Using pattern matching, as, and is Operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="59a86-139">İzlenecek yol: Dinamik nesneler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="59a86-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
