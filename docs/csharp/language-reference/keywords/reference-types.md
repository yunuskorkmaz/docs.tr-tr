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
ms.openlocfilehash: 16e7cdc624979f9a35e287ea5274bd9398c83132
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715173"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="cfd33-102">Başvuru türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="cfd33-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="cfd33-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="cfd33-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="cfd33-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="cfd33-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="cfd33-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="cfd33-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="cfd33-106">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişkende diğer işlemler (ın, ref ve out parametre değişkenleri hariç) için bir değişken üzerinde işlemler yapılamaz; bkz. [ın](in-parameter-modifier.md), [ref](ref.md) ve [Out](out-parameter-modifier.md) parametre değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="cfd33-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="cfd33-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="cfd33-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="cfd33-108">class</span><span class="sxs-lookup"><span data-stu-id="cfd33-108">class</span></span>](class.md)

- [<span data-ttu-id="cfd33-109">interface</span><span class="sxs-lookup"><span data-stu-id="cfd33-109">interface</span></span>](interface.md)

- [<span data-ttu-id="cfd33-110">delegate</span><span class="sxs-lookup"><span data-stu-id="cfd33-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="cfd33-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="cfd33-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="cfd33-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="cfd33-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="cfd33-113">object</span><span class="sxs-lookup"><span data-stu-id="cfd33-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="cfd33-114">string</span><span class="sxs-lookup"><span data-stu-id="cfd33-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="cfd33-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfd33-115">See also</span></span>

- [<span data-ttu-id="cfd33-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="cfd33-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cfd33-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cfd33-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cfd33-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cfd33-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cfd33-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="cfd33-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="cfd33-120">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="cfd33-120">Value types</span></span>](value-types.md)
