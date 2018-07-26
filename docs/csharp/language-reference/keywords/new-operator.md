---
title: new İşleci (C# Başvurusu)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243953"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="fcab9-102">new İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fcab9-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="fcab9-103">Nesneleri oluşturmak ve oluşturucuları çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fcab9-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="fcab9-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fcab9-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="fcab9-105">Ayrıca, anonim türlerin örneklerini oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="fcab9-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="fcab9-106">`new` İşleci değer türleri için varsayılan oluşturucuyu çağırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fcab9-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="fcab9-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fcab9-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="fcab9-108">Önceki deyim içinde `i` değerine ayarlanır `0`, türü için varsayılan değer olan `int`.</span><span class="sxs-lookup"><span data-stu-id="fcab9-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="fcab9-109">Deyimi aşağıdaki aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="fcab9-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="fcab9-110">Varsayılan değerlerin tam listesi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="fcab9-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="fcab9-111">İçin varsayılan oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapı](../../../csharp/language-reference/keywords/struct.md) her değer türü örtük olarak bir genel varsayılan oluşturucuya sahip olduğundan.</span><span class="sxs-lookup"><span data-stu-id="fcab9-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="fcab9-112">Parametreli oluşturucular ilk değerleri ayarlamak için bir yapı türü bildirmek mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekiyorsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fcab9-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="fcab9-113">Hem yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak edilir, ancak içeren bağlamları kaldırıldığında, bu başvuru türü nesneler çöp tarafından yok ise değer türü nesneler yok edilir Toplayıcı bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen bir zaman.</span><span class="sxs-lookup"><span data-stu-id="fcab9-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="fcab9-114">Dosya tanıtıcıları veya ağ bağlantıları gibi kaynakları içeren türleri için içerdikleri kaynakları hemen serbest emin olmak için belirleyici temizleme kullanmayı tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="fcab9-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="fcab9-115">Daha fazla bilgi için [using deyimi](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fcab9-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="fcab9-116">`new` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="fcab9-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="fcab9-117">Varsa `new` işleci başarısız bellek ayırmaya, özel durum oluşturduğunda <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="fcab9-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcab9-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcab9-118">Example</span></span>  
 <span data-ttu-id="fcab9-119">Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanılarak başlatılan `new` işleci ve ardından değerler atanır.</span><span class="sxs-lookup"><span data-stu-id="fcab9-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="fcab9-120">Varsayılan ve atanan değerleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fcab9-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="fcab9-121">Varsayılan değer bir dize örneği bildiriminde `null`.</span><span class="sxs-lookup"><span data-stu-id="fcab9-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="fcab9-122">Bu nedenle, bu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="fcab9-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fcab9-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fcab9-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fcab9-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcab9-124">See Also</span></span>  
 [<span data-ttu-id="fcab9-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fcab9-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fcab9-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fcab9-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fcab9-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fcab9-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fcab9-128">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fcab9-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="fcab9-129">new</span><span class="sxs-lookup"><span data-stu-id="fcab9-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="fcab9-130">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="fcab9-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
