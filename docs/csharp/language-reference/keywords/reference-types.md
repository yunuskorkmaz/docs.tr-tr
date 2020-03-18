---
title: Referans türleri - C# Referans
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744522"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="e6e7f-102">Başvuru türleri (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="e6e7f-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="e6e7f-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="e6e7f-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="e6e7f-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="e6e7f-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="e6e7f-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e6e7f-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="e6e7f-106">Değer türleri ile, her değişkenin kendi veri kopyası vardır ve bir değişkendeki işlemlerin diğerini etkilemesi mümkün değildir (in, ref [ref](ref.md) ve [out](out-parameter-modifier.md) out parametre değişkenleri hariç; [bkz.](in-parameter-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="e6e7f-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="e6e7f-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e6e7f-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="e6e7f-108">Sınıfı</span><span class="sxs-lookup"><span data-stu-id="e6e7f-108">class</span></span>](class.md)

- [<span data-ttu-id="e6e7f-109">Arabirim</span><span class="sxs-lookup"><span data-stu-id="e6e7f-109">interface</span></span>](interface.md)

- [<span data-ttu-id="e6e7f-110">temsilci</span><span class="sxs-lookup"><span data-stu-id="e6e7f-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="e6e7f-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="e6e7f-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="e6e7f-112">Dinamik</span><span class="sxs-lookup"><span data-stu-id="e6e7f-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="e6e7f-113">Nesne</span><span class="sxs-lookup"><span data-stu-id="e6e7f-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="e6e7f-114">Dize</span><span class="sxs-lookup"><span data-stu-id="e6e7f-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="e6e7f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6e7f-115">See also</span></span>

- [<span data-ttu-id="e6e7f-116">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e6e7f-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e6e7f-117">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="e6e7f-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e6e7f-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="e6e7f-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e6e7f-119">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="e6e7f-119">Value types</span></span>](../builtin-types/value-types.md)
