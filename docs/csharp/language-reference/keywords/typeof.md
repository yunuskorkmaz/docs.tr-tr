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
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753942"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="f9d3d-102">typeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f9d3d-102">typeof (C# Reference)</span></span>
<span data-ttu-id="f9d3d-103">Elde etmek için kullanılan `System.Type` nesne türü.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="f9d3d-104">A `typeof` ifade aşağıdaki biçimleri alır:</span><span class="sxs-lookup"><span data-stu-id="f9d3d-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f9d3d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9d3d-105">Remarks</span></span>  
 <span data-ttu-id="f9d3d-106">Bir ifadenin çalışma zamanı türü elde etmek için .NET Framework yöntemi kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="f9d3d-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="f9d3d-107">`typeof` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="f9d3d-108">`typeof` İşleci açık genel türler üzerinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="f9d3d-109">Birden fazla tür parametresi ile türleri belirtiminde virgül uygun sayıda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="f9d3d-110">Aşağıdaki örnek, bir yöntemin dönüş türü genel olup olmadığını belirlemek gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f9d3d-111">Metodu için MethodInfo türünün bir örneği olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="f9d3d-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="f9d3d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9d3d-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f9d3d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9d3d-113">Example</span></span>  
 <span data-ttu-id="f9d3d-114">Bu örnekte <xref:System.Object.GetType%2A> sayısal hesaplama sonucu kapsamak için kullanılmış türünü belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="f9d3d-115">Bu, sonuçta elde edilen sayı depolama gereksinimlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f9d3d-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f9d3d-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9d3d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9d3d-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="f9d3d-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9d3d-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f9d3d-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9d3d-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f9d3d-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f9d3d-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f9d3d-121">is</span><span class="sxs-lookup"><span data-stu-id="f9d3d-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="f9d3d-122">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f9d3d-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
