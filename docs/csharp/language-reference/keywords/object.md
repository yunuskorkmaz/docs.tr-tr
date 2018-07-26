---
title: object (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199257"
---
# <a name="object-c-reference"></a><span data-ttu-id="a08a8-102">object (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a08a8-102">object (C# Reference)</span></span>
<span data-ttu-id="a08a8-103">`object` Türü için bir diğer ad, <xref:System.Object> .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="a08a8-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="a08a8-104">C#, tüm türlerin, önceden tanımlanmış ve kullanıcı tanımlı başvuru türleri ve değer türleri birleşik tür sisteminde doğrudan veya dolaylı olarak devralınacak <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a08a8-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="a08a8-105">Her türden değer türü değişkenler için atayabilirsiniz `object`.</span><span class="sxs-lookup"><span data-stu-id="a08a8-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="a08a8-106">Ne zaman bir değer türü bir değişkene dönüştürülür nesnesi için kabul edilecek *Kutulu*.</span><span class="sxs-lookup"><span data-stu-id="a08a8-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="a08a8-107">Türündeki bir değişkene bir değer türüne dönüştürülür, onu olduğu söylenir *kutulanmamış*.</span><span class="sxs-lookup"><span data-stu-id="a08a8-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="a08a8-108">Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="a08a8-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a08a8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a08a8-109">Example</span></span>  
 <span data-ttu-id="a08a8-110">Aşağıdaki örnekte gösterildiği nasıl türündeki değişkenler `object` herhangi bir veri türünün değerlerini kabul edebilir ve nasıl türündeki değişkenler `object` yöntemleri kullanabilirsiniz <xref:System.Object> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a08a8-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a08a8-111">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a08a8-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a08a8-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a08a8-112">See Also</span></span>  
 [<span data-ttu-id="a08a8-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a08a8-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a08a8-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a08a8-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a08a8-115">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a08a8-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a08a8-116">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="a08a8-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="a08a8-117">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="a08a8-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
