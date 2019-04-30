---
title: Nesne - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: a1917a7925d4ed90ede40248fa394f9c45d09b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661132"
---
# <a name="object-c-reference"></a><span data-ttu-id="55951-102">object (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="55951-102">object (C# Reference)</span></span>

<span data-ttu-id="55951-103">`object` Türü için bir diğer ad, <xref:System.Object> .NET içinde.</span><span class="sxs-lookup"><span data-stu-id="55951-103">The `object` type is an alias for <xref:System.Object> in .NET.</span></span> <span data-ttu-id="55951-104">C#, tüm türlerin, önceden tanımlanmış ve kullanıcı tanımlı başvuru türleri ve değer türleri birleşik tür sisteminde doğrudan veya dolaylı olarak devralınacak <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="55951-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="55951-105">Her türden değer türü değişkenler için atayabilirsiniz `object`.</span><span class="sxs-lookup"><span data-stu-id="55951-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="55951-106">Ne zaman bir değer türü bir değişkene dönüştürülür nesnesi için kabul edilecek *Kutulu*.</span><span class="sxs-lookup"><span data-stu-id="55951-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="55951-107">Türündeki bir değişkene bir değer türüne dönüştürülür, onu olduğu söylenir *kutulanmamış*.</span><span class="sxs-lookup"><span data-stu-id="55951-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="55951-108">Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="55951-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="example"></a><span data-ttu-id="55951-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="55951-109">Example</span></span>

<span data-ttu-id="55951-110">Aşağıdaki örnekte gösterildiği nasıl türündeki değişkenler `object` herhangi bir veri türünün değerlerini kabul edebilir ve nasıl türündeki değişkenler `object` yöntemleri kullanabilirsiniz <xref:System.Object> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55951-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a><span data-ttu-id="55951-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="55951-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="55951-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55951-112">See also</span></span>

- [<span data-ttu-id="55951-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="55951-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="55951-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="55951-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="55951-115">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="55951-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="55951-116">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="55951-116">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="55951-117">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="55951-117">Value Types</span></span>](value-types.md)