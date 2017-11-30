---
title: "new İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="b7140-102">new İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b7140-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="b7140-103">Nesneleri oluşturmak ve oluşturucular çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7140-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="b7140-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b7140-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="b7140-105">Anonim türler örneklerini oluşturmak için de kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b7140-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="b7140-106">`new` İşleci değer türleri için varsayılan oluşturucu çağırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7140-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="b7140-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b7140-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="b7140-108">Önceki deyiminde `i` için başlatılan `0`, türü için varsayılan değeri olduğu `int`.</span><span class="sxs-lookup"><span data-stu-id="b7140-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="b7140-109">Deyim şu aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b7140-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="b7140-110">Varsayılan değerlerin tam listesi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="b7140-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="b7140-111">İçin varsayılan bir oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapısı](../../../csharp/language-reference/keywords/struct.md) her değer türü örtük olarak ortak varsayılan bir oluşturucu olduğundan.</span><span class="sxs-lookup"><span data-stu-id="b7140-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="b7140-112">Parametreli oluşturucular ilk değerlerini ayarlamak için bir yapı türüne bildirmeniz mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekli ise gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b7140-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="b7140-113">Başvuru türü gibi sınıfları öbek üzerinde oluşturulan nesneleri sırada yapılar gibi değer türü nesneleri yığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b7140-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="b7140-114">Her iki türdeki nesneler otomatik olarak yok ancak kapsamının dışına gittiğinizde değer türleri üzerinde bağlı nesneleri yok, nesneleri temel ancak başvuru türleri bunları son referansı kaldırıldıktan sonra belirtilmeyen bir zamanda yok olur.</span><span class="sxs-lookup"><span data-stu-id="b7140-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="b7140-115">Büyük miktarlarda bellek, dosya tanıtıcısı veya ağ bağlantıları gibi sabit kaynaklarını tüketebilir başvuru türleri için bazen nesnesi mümkün olan en kısa sürede yok emin olmak için sonlandırma kullanmayı tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="b7140-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="b7140-116">Daha fazla bilgi için bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b7140-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="b7140-117">`new` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b7140-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="b7140-118">Varsa `new` işleci başarısız bellek ayıramadı, özel durum oluşturur <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="b7140-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7140-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7140-119">Example</span></span>  
 <span data-ttu-id="b7140-120">Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanarak başlatılmış `new` işleci ve değerler atanır.</span><span class="sxs-lookup"><span data-stu-id="b7140-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="b7140-121">Varsayılan ve atanmış değerler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7140-121">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="b7140-122">Varsayılan değer bir dize örneği bildiriminde `null`.</span><span class="sxs-lookup"><span data-stu-id="b7140-122">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="b7140-123">Bu nedenle, görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="b7140-123">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b7140-124">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b7140-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7140-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7140-125">See Also</span></span>  
 [<span data-ttu-id="b7140-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b7140-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b7140-127">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b7140-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b7140-128">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b7140-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b7140-129">İşleç anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b7140-129">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="b7140-130">Yeni</span><span class="sxs-lookup"><span data-stu-id="b7140-130">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="b7140-131">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="b7140-131">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
