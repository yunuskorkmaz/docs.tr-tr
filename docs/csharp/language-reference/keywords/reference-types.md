---
title: Başvuru türleri - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: ae7511c1bbe1b50e0070c41b25642e7b614c485d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241360"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="391ef-102">Başvuru türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="391ef-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="391ef-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="391ef-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="391ef-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="391ef-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="391ef-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="391ef-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="391ef-106">Değer türleri ile her değişkenin kendi veri kopyası vardır ve yapılan işlemlerin diğerini etkilemesi için bir değişken üzerinde değil (hariç durumunda, ref ve out parametresi değişkenleri; bkz [içinde](in-parameter-modifier.md), [ref](ref.md) ve [kullanıma](out-parameter-modifier.md) parametre değiştiricisi).</span><span class="sxs-lookup"><span data-stu-id="391ef-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="391ef-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="391ef-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="391ef-108">class</span><span class="sxs-lookup"><span data-stu-id="391ef-108">class</span></span>](class.md)

- [<span data-ttu-id="391ef-109">interface</span><span class="sxs-lookup"><span data-stu-id="391ef-109">interface</span></span>](interface.md)

- [<span data-ttu-id="391ef-110">delegate</span><span class="sxs-lookup"><span data-stu-id="391ef-110">delegate</span></span>](delegate.md)

 <span data-ttu-id="391ef-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="391ef-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="391ef-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="391ef-112">dynamic</span></span>](dynamic.md)

- [<span data-ttu-id="391ef-113">object</span><span class="sxs-lookup"><span data-stu-id="391ef-113">object</span></span>](object.md)

- [<span data-ttu-id="391ef-114">string</span><span class="sxs-lookup"><span data-stu-id="391ef-114">string</span></span>](string.md)

## <a name="see-also"></a><span data-ttu-id="391ef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="391ef-115">See also</span></span>

- [<span data-ttu-id="391ef-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="391ef-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="391ef-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="391ef-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="391ef-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="391ef-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="391ef-119">Türler</span><span class="sxs-lookup"><span data-stu-id="391ef-119">Types</span></span>](types.md)
- [<span data-ttu-id="391ef-120">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="391ef-120">Value Types</span></span>](value-types.md)