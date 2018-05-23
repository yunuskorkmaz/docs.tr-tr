---
title: typeof (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="typeof-c-reference"></a><span data-ttu-id="27477-102">typeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="27477-102">typeof (C# Reference)</span></span>
<span data-ttu-id="27477-103">Elde etmek için kullanılan `System.Type` nesne türü için.</span><span class="sxs-lookup"><span data-stu-id="27477-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="27477-104">A `typeof` ifade aşağıdaki formu alır:</span><span class="sxs-lookup"><span data-stu-id="27477-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="27477-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27477-105">Remarks</span></span>  
 <span data-ttu-id="27477-106">Çalışma zamanı tür ifade elde etmek için .NET Framework yöntemini kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="27477-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="27477-107">`typeof` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="27477-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="27477-108">`typeof` İşleci açık genel türler üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27477-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="27477-109">Birden fazla tür parametresi türleriyle virgül uygun sayıda belirtiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27477-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="27477-110">Aşağıdaki örnek, bir yöntemin dönüş türünü genel olup olmadığını belirlemek gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="27477-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="27477-111">Yöntem MethodInfo türünün bir örneği olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="27477-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="27477-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="27477-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="27477-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="27477-113">Example</span></span>  
 <span data-ttu-id="27477-114">Bu örnekte <xref:System.Object.GetType%2A> yöntemi sayısal hesaplamanın sonucu kapsamak için kullanılmış türü belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="27477-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="27477-115">Bu sonuç sayısı depolama gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="27477-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="27477-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="27477-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="27477-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27477-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="27477-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="27477-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="27477-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="27477-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27477-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="27477-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="27477-121">is</span><span class="sxs-lookup"><span data-stu-id="27477-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="27477-122">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="27477-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
