---
title: "[] İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03664f5604bb7d7dce9e8ae2ff0ec045c6a203b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5d662-102">[] İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5d662-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="5d662-103">Köşeli ayraç (`[]`) dizileri, dizin oluşturucular ve öznitelikleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d662-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="5d662-104">İşaretçileri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d662-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d662-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d662-105">Remarks</span></span>  
 <span data-ttu-id="5d662-106">Bir dizi türü arkasından bir türdür `[]`:</span><span class="sxs-lookup"><span data-stu-id="5d662-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="5d662-107">Dizi bir öğe erişmek için istenen öğenin dizini ayraç içine alınır:</span><span class="sxs-lookup"><span data-stu-id="5d662-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="5d662-108">Bir dizi dizini aralık dışında ise özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="5d662-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="5d662-109">Dizin oluşturma işleci dizi aşırı yüklenemez; Ancak, türleri dizin oluşturucular ve bir veya daha fazla parametre almaz özelliklerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d662-109">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="5d662-110">Dizin Oluşturucu parametreleri dizi dizinleri gibi köşeli parantez içine alınır ancak dizin oluşturucu parametresi tamsayı dizi dizinleri aksine herhangi bir türde olması için bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5d662-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="5d662-111">Örneğin, .NET Framework tanımlayan bir `Hashtable` anahtarları ve değerleri rastgele türün ilişkilendirir türü:</span><span class="sxs-lookup"><span data-stu-id="5d662-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="5d662-112">Köşeli ayraçlar belirtmek için de kullanılır [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="5d662-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="5d662-113">Bir işaretçi kapalı dizin için köşeli ayraç kullanın:</span><span class="sxs-lookup"><span data-stu-id="5d662-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="5d662-114">Hiçbir sınırları denetimi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5d662-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5d662-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5d662-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d662-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d662-116">See Also</span></span>  
 [<span data-ttu-id="5d662-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5d662-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5d662-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d662-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d662-119">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="5d662-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="5d662-120">Diziler</span><span class="sxs-lookup"><span data-stu-id="5d662-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="5d662-121">Dizin oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5d662-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="5d662-122">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="5d662-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="5d662-123">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="5d662-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
