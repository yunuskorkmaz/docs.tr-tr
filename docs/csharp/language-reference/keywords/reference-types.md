---
title: Başvuru türleri- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744522"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="beb2b-102">Başvuru türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="beb2b-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="beb2b-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="beb2b-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="beb2b-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="beb2b-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="beb2b-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="beb2b-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="beb2b-106">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişkende diğer işlemler (ın, ref ve out parametre değişkenleri hariç) için bir değişken üzerinde işlemler yapılamaz; bkz. [ın](in-parameter-modifier.md), [ref](ref.md) ve [Out](out-parameter-modifier.md) parametre değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="beb2b-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="beb2b-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="beb2b-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="beb2b-108">class</span><span class="sxs-lookup"><span data-stu-id="beb2b-108">class</span></span>](class.md)

- [<span data-ttu-id="beb2b-109">interface</span><span class="sxs-lookup"><span data-stu-id="beb2b-109">interface</span></span>](interface.md)

- [<span data-ttu-id="beb2b-110">delegate</span><span class="sxs-lookup"><span data-stu-id="beb2b-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="beb2b-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="beb2b-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="beb2b-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="beb2b-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="beb2b-113">object</span><span class="sxs-lookup"><span data-stu-id="beb2b-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="beb2b-114">string</span><span class="sxs-lookup"><span data-stu-id="beb2b-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="beb2b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beb2b-115">See also</span></span>

- [<span data-ttu-id="beb2b-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="beb2b-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="beb2b-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="beb2b-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="beb2b-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="beb2b-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="beb2b-119">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="beb2b-119">Value types</span></span>](../builtin-types/value-types.md)
