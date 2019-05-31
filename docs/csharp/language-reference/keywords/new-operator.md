---
title: New işleci - C# başvurusu
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 409a5307eaacd2eac865e2882cc7228521260dbe
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421879"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="e24ee-102">New işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e24ee-102">new operator (C# Reference)</span></span>

<span data-ttu-id="e24ee-103">Nesneleri oluşturmak ve oluşturucuları çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e24ee-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="e24ee-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e24ee-104">For example:</span></span>

```csharp
Class1 obj  = new Class1();
```

<span data-ttu-id="e24ee-105">Ayrıca, anonim türlerin örneklerini oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e24ee-105">It is also used to create instances of anonymous types:</span></span>

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

<span data-ttu-id="e24ee-106">`new` İşleci değer türleri için parametresiz oluşturucu çağırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e24ee-106">The `new` operator is also used to invoke the parameterless constructor for value types.</span></span> <span data-ttu-id="e24ee-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e24ee-107">For example:</span></span>

```csharp
int i = new int();
```

<span data-ttu-id="e24ee-108">Önceki deyim içinde `i` değerine ayarlanır `0`, türü için varsayılan değer olan `int`.</span><span class="sxs-lookup"><span data-stu-id="e24ee-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="e24ee-109">Deyimi aşağıdaki aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e24ee-109">The statement has the same effect as the following:</span></span>

```csharp
int i = 0;
```

<span data-ttu-id="e24ee-110">Varsayılan değerlerin tam listesi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="e24ee-110">For a complete list of default values, see [Default Values Table](default-values-table.md).</span></span>

<span data-ttu-id="e24ee-111">Parametresiz bir oluşturucu için bildirmek için bir hata olduğunu unutmayın bir [yapı](struct.md) her değer türü örtük olarak genel parametresiz oluşturucusu olmadığından.</span><span class="sxs-lookup"><span data-stu-id="e24ee-111">Remember that it is an error to declare a parameterless constructor for a [struct](struct.md) because every value type implicitly has a public parameterless constructor.</span></span> <span data-ttu-id="e24ee-112">Parametreli oluşturucular ilk değerleri ayarlamak için bir yapı türü bildirmek mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekiyorsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e24ee-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>

<span data-ttu-id="e24ee-113">Hem yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak edilir, ancak içeren bağlamları kaldırıldığında, bu başvuru türü nesneler çöp tarafından yok ise değer türü nesneler yok edilir Toplayıcı bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen bir zaman.</span><span class="sxs-lookup"><span data-stu-id="e24ee-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="e24ee-114">Dosya tanıtıcıları veya ağ bağlantıları gibi kaynakları içeren türleri için içerdikleri kaynakları hemen serbest emin olmak için belirleyici temizleme kullanmayı tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="e24ee-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="e24ee-115">Daha fazla bilgi için [using deyimi](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e24ee-115">For more information, see [using Statement](using-statement.md).</span></span>

<span data-ttu-id="e24ee-116">`new` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e24ee-116">The `new` operator cannot be overloaded.</span></span>

<span data-ttu-id="e24ee-117">Varsa `new` işleci başarısız bellek ayırmaya, özel durum oluşturduğunda <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="e24ee-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="e24ee-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e24ee-118">Example</span></span>

<span data-ttu-id="e24ee-119">Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanılarak başlatılan `new` işleci ve ardından değerler atanır.</span><span class="sxs-lookup"><span data-stu-id="e24ee-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="e24ee-120">Varsayılan ve atanan değerleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e24ee-120">The default and the assigned values are displayed.</span></span>

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

<span data-ttu-id="e24ee-121">Varsayılan değer bir dize örneği bildiriminde `null`.</span><span class="sxs-lookup"><span data-stu-id="e24ee-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="e24ee-122">Bu nedenle, bu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="e24ee-122">Therefore, it is not displayed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e24ee-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e24ee-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e24ee-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e24ee-124">See also</span></span>

- [<span data-ttu-id="e24ee-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e24ee-125">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e24ee-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e24ee-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e24ee-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e24ee-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e24ee-128">new</span><span class="sxs-lookup"><span data-stu-id="e24ee-128">new</span></span>](new.md)
- [<span data-ttu-id="e24ee-129">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="e24ee-129">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
