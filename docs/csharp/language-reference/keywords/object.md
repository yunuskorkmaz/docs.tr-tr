---
title: "object (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords: object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0fcced75d3a86fd700e642e48b7e325e554cae53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-c-reference"></a><span data-ttu-id="9e7c6-102">object (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9e7c6-102">object (C# Reference)</span></span>
<span data-ttu-id="9e7c6-103">`object` Türüdür için diğer ad <xref:System.Object> .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="9e7c6-104">C#, tüm türleri, önceden tanımlanmış ve kullanıcı tanımlı başvuru türleri ve değer türleri birleşik türü sistemde, doğrudan veya dolaylı olarak devralınmalıdır <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="9e7c6-105">Türündeki değişkenler için herhangi bir türde değerler atayabilirsiniz `object`.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="9e7c6-106">Ne zaman bir değişkene bir değer türü dönüştürülür nesne için söyledi olmasını *Kutulu*.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="9e7c6-107">Object türünde bir değişken için bir değer türü dönüştürüldüğünde, onu olarak kabul edilir *sarmalanmamış*.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="9e7c6-108">Daha fazla bilgi için bkz: [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="9e7c6-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e7c6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e7c6-109">Example</span></span>  
 <span data-ttu-id="9e7c6-110">Aşağıdaki örnekte gösterildiği nasıl türündeki değişkenler `object` herhangi bir veri türü değerlerini kabul edebilir ve nasıl türündeki değişkenler `object` yöntemlerini kullanabilirsiniz <xref:System.Object> .NET çerçeveden.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9e7c6-111">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9e7c6-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e7c6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e7c6-112">See Also</span></span>  
 [<span data-ttu-id="9e7c6-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e7c6-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9e7c6-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9e7c6-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9e7c6-115">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9e7c6-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9e7c6-116">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="9e7c6-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="9e7c6-117">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="9e7c6-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
