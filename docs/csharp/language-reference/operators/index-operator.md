---
title: '[] İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 19283a795f8cfc444dfcb186dcecc0ea86eb27fd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467438"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="35938-102">[] İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="35938-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="35938-103">Köşeli ayraçlar (`[]`) diziler, dizin oluşturucular ve öznitelikleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35938-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="35938-104">İşaretçiler ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35938-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35938-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35938-105">Remarks</span></span>  
 <span data-ttu-id="35938-106">Bir dizi türü arkasından bir türdür `[]`:</span><span class="sxs-lookup"><span data-stu-id="35938-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="35938-107">Bir dizinin bir öğesine erişmek için istenen öğenin dizini ayraç içine alınır:</span><span class="sxs-lookup"><span data-stu-id="35938-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="35938-108">Bir dizi dizini aralık dışında ise bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="35938-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="35938-109">Dizin oluşturma işleci dizi aşırı yüklenemez; Ancak, türleri, bir veya daha fazla parametre dizin oluşturucular tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35938-109">The array indexing operator cannot be overloaded; however, types can define indexers that take one or more parameters.</span></span> <span data-ttu-id="35938-110">Dizin Oluşturucu parametresi dizi dizinleri gibi köşeli ayraçlar içine alınan ancak dizin oluşturucu parametresi tamsayı dizisi dizinler, aksine herhangi bir türde olması için bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="35938-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="35938-111">Örneğin, .NET Framework tanımlayan bir `Hashtable` anahtarları ve değerleri rastgele tür ilişkilendirir türü:</span><span class="sxs-lookup"><span data-stu-id="35938-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="35938-112">Köşeli ayraçlar belirtmek için de kullanılır [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="35938-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="35938-113">Bir işaretçi dizinlemek için köşeli ayraçlar kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="35938-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="35938-114">Sınır denetimi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="35938-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="35938-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="35938-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35938-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35938-116">See Also</span></span>

- [<span data-ttu-id="35938-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="35938-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="35938-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="35938-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="35938-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="35938-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="35938-120">Diziler</span><span class="sxs-lookup"><span data-stu-id="35938-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="35938-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="35938-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="35938-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="35938-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="35938-123">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="35938-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
