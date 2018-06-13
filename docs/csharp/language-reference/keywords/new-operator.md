---
title: new İşleci (C# Başvurusu)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268927"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="62d53-102">new İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="62d53-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="62d53-103">Nesneleri oluşturmak ve oluşturucular çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62d53-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="62d53-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="62d53-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="62d53-105">Anonim türler örneklerini oluşturmak için de kullanılır:</span><span class="sxs-lookup"><span data-stu-id="62d53-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="62d53-106">`new` İşleci değer türleri için varsayılan oluşturucu çağırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62d53-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="62d53-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="62d53-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="62d53-108">Önceki deyiminde `i` için başlatılan `0`, türü için varsayılan değeri olduğu `int`.</span><span class="sxs-lookup"><span data-stu-id="62d53-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="62d53-109">Deyim şu aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="62d53-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="62d53-110">Varsayılan değerlerin tam listesi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="62d53-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="62d53-111">İçin varsayılan bir oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapısı](../../../csharp/language-reference/keywords/struct.md) her değer türü örtük olarak ortak varsayılan bir oluşturucu olduğundan.</span><span class="sxs-lookup"><span data-stu-id="62d53-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="62d53-112">Parametreli oluşturucular ilk değerlerini ayarlamak için bir yapı türüne bildirmeniz mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekli ise gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62d53-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="62d53-113">Yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak yok edilir, ancak içeren bağlamları kaldırıldığı zaman başvuru türü nesneler tarafından çöp yok ancak değer türü nesneleri yok Toplayıcı bunları son referansı kaldırıldıktan sonra belirtilmeyen bir zaman.</span><span class="sxs-lookup"><span data-stu-id="62d53-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="62d53-114">Dosya tanıtıcıları ya da ağ bağlantıları gibi kaynakları içeren türleri içerdikleri kaynaklara mümkün olan en kısa sürede yayımlanan emin olmak için belirleyici temizleme kullanmayı tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="62d53-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="62d53-115">Daha fazla bilgi için bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62d53-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="62d53-116">`new` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="62d53-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="62d53-117">Varsa `new` işleci başarısız bellek ayıramadı, özel durum oluşturur <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="62d53-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62d53-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="62d53-118">Example</span></span>  
 <span data-ttu-id="62d53-119">Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanarak başlatılmış `new` işleci ve değerler atanır.</span><span class="sxs-lookup"><span data-stu-id="62d53-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="62d53-120">Varsayılan ve atanmış değerler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="62d53-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="62d53-121">Varsayılan değer bir dize örneği bildiriminde `null`.</span><span class="sxs-lookup"><span data-stu-id="62d53-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="62d53-122">Bu nedenle, görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="62d53-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="62d53-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="62d53-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62d53-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62d53-124">See Also</span></span>  
 [<span data-ttu-id="62d53-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="62d53-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="62d53-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="62d53-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="62d53-127">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="62d53-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="62d53-128">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="62d53-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="62d53-129">new</span><span class="sxs-lookup"><span data-stu-id="62d53-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="62d53-130">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="62d53-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
