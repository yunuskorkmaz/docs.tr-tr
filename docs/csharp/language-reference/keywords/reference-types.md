---
title: Başvuru türleri- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 61b9f8096e1b2093b1ea5589f4336618cd189c34
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422452"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="0cf8a-102">Başvuru türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="0cf8a-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="0cf8a-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="0cf8a-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="0cf8a-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="0cf8a-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="0cf8a-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="0cf8a-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="0cf8a-106">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişkende diğer işlemler (ın, ref ve out parametre değişkenleri hariç) için bir değişken üzerinde işlemler yapılamaz; bkz. [ın](in-parameter-modifier.md), [ref](ref.md) ve [Out](out-parameter-modifier.md) parametre değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0cf8a-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="0cf8a-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="0cf8a-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="0cf8a-108">class</span><span class="sxs-lookup"><span data-stu-id="0cf8a-108">class</span></span>](class.md)

- [<span data-ttu-id="0cf8a-109">interface</span><span class="sxs-lookup"><span data-stu-id="0cf8a-109">interface</span></span>](interface.md)

- [<span data-ttu-id="0cf8a-110">delegate</span><span class="sxs-lookup"><span data-stu-id="0cf8a-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="0cf8a-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="0cf8a-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="0cf8a-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="0cf8a-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="0cf8a-113">object</span><span class="sxs-lookup"><span data-stu-id="0cf8a-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="0cf8a-114">string</span><span class="sxs-lookup"><span data-stu-id="0cf8a-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="0cf8a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf8a-115">See also</span></span>

- [<span data-ttu-id="0cf8a-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="0cf8a-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0cf8a-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0cf8a-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0cf8a-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0cf8a-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0cf8a-119">Türler</span><span class="sxs-lookup"><span data-stu-id="0cf8a-119">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="0cf8a-120">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="0cf8a-120">Value Types</span></span>](value-types.md)
