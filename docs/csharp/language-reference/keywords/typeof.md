---
title: "typeof (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords: typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a><span data-ttu-id="dadf3-102">typeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dadf3-102">typeof (C# Reference)</span></span>
<span data-ttu-id="dadf3-103">Elde etmek için kullanılan `System.Type` nesne türü için.</span><span class="sxs-lookup"><span data-stu-id="dadf3-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="dadf3-104">A `typeof` ifade aşağıdaki formu alır:</span><span class="sxs-lookup"><span data-stu-id="dadf3-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="dadf3-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dadf3-105">Remarks</span></span>  
 <span data-ttu-id="dadf3-106">Çalışma zamanı tür ifade elde etmek için .NET Framework yöntemini kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="dadf3-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="dadf3-107">`typeof` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="dadf3-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="dadf3-108">`typeof` İşleci açık genel türler üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dadf3-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="dadf3-109">Birden fazla tür parametresi türleriyle virgül uygun sayıda belirtiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dadf3-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="dadf3-110">Aşağıdaki örnek, bir yöntemin dönüş türünü genel olup olmadığını belirlemek gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dadf3-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="dadf3-111">Yöntem MethodInfo türünün bir örneği olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="dadf3-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="dadf3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="dadf3-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="dadf3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="dadf3-113">Example</span></span>  
 <span data-ttu-id="dadf3-114">Bu örnekte <xref:System.Object.GetType%2A> yöntemi sayısal hesaplamanın sonucu kapsamak için kullanılmış türü belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="dadf3-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="dadf3-115">Bu sonuç sayısı depolama gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dadf3-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="dadf3-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="dadf3-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dadf3-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dadf3-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="dadf3-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dadf3-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dadf3-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dadf3-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dadf3-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="dadf3-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="dadf3-121">değil</span><span class="sxs-lookup"><span data-stu-id="dadf3-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="dadf3-122">İşleç anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="dadf3-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
