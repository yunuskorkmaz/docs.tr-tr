---
title: New işleci (C# Başvurusu)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 362217b247bd2ab7a2eec2f86cbaaf1a0652a3ad
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45741766"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="ee380-102">New işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ee380-102">new operator (C# Reference)</span></span>

<span data-ttu-id="ee380-103">Nesneleri oluşturmak ve oluşturucuları çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee380-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="ee380-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ee380-104">For example:</span></span>

```csharp
Class1 obj  = new Class1();
```

<span data-ttu-id="ee380-105">Ayrıca, anonim türlerin örneklerini oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="ee380-105">It is also used to create instances of anonymous types:</span></span>

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

<span data-ttu-id="ee380-106">`new` İşleci değer türleri için varsayılan oluşturucuyu çağırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee380-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="ee380-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ee380-107">For example:</span></span>

```csharp
int i = new int();
```

<span data-ttu-id="ee380-108">Önceki deyim içinde `i` değerine ayarlanır `0`, türü için varsayılan değer olan `int`.</span><span class="sxs-lookup"><span data-stu-id="ee380-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="ee380-109">Deyimi aşağıdaki aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ee380-109">The statement has the same effect as the following:</span></span>

```csharp
int i = 0;
```

<span data-ttu-id="ee380-110">Varsayılan değerlerin tam listesi için bkz. [varsayılan değerler tablosu](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ee380-110">For a complete list of default values, see [Default Values Table](default-values-table.md).</span></span>

<span data-ttu-id="ee380-111">İçin varsayılan oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapı](struct.md) her değer türü örtük olarak bir genel varsayılan oluşturucuya sahip olduğundan.</span><span class="sxs-lookup"><span data-stu-id="ee380-111">Remember that it is an error to declare a default constructor for a [struct](struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="ee380-112">Parametreli oluşturucular ilk değerleri ayarlamak için bir yapı türü bildirmek mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekiyorsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ee380-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>

<span data-ttu-id="ee380-113">Hem yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak edilir, ancak içeren bağlamları kaldırıldığında, bu başvuru türü nesneler çöp tarafından yok ise değer türü nesneler yok edilir Toplayıcı bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen bir zaman.</span><span class="sxs-lookup"><span data-stu-id="ee380-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="ee380-114">Dosya tanıtıcıları veya ağ bağlantıları gibi kaynakları içeren türleri için içerdikleri kaynakları hemen serbest emin olmak için belirleyici temizleme kullanmayı tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="ee380-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="ee380-115">Daha fazla bilgi için [using deyimi](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee380-115">For more information, see [using Statement](using-statement.md).</span></span>

<span data-ttu-id="ee380-116">`new` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="ee380-116">The `new` operator cannot be overloaded.</span></span>

<span data-ttu-id="ee380-117">Varsa `new` işleci başarısız bellek ayırmaya, özel durum oluşturduğunda <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="ee380-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="ee380-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee380-118">Example</span></span>

<span data-ttu-id="ee380-119">Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanılarak başlatılan `new` işleci ve ardından değerler atanır.</span><span class="sxs-lookup"><span data-stu-id="ee380-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="ee380-120">Varsayılan ve atanan değerleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee380-120">The default and the assigned values are displayed.</span></span>

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

<span data-ttu-id="ee380-121">Varsayılan değer bir dize örneği bildiriminde `null`.</span><span class="sxs-lookup"><span data-stu-id="ee380-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="ee380-122">Bu nedenle, bu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="ee380-122">Therefore, it is not displayed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee380-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ee380-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ee380-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee380-124">See also</span></span>

- [<span data-ttu-id="ee380-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ee380-125">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ee380-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ee380-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ee380-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ee380-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ee380-128">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ee380-128">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="ee380-129">new</span><span class="sxs-lookup"><span data-stu-id="ee380-129">new</span></span>](new.md)
- [<span data-ttu-id="ee380-130">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="ee380-130">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)