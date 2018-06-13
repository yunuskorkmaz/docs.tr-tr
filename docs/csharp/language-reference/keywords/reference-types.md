---
title: Başvuru Türleri (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: cca9826c658581be38866410d5f966b1c7c35772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267345"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="e0c7b-102">Başvuru Türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0c7b-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="e0c7b-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="e0c7b-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="e0c7b-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="e0c7b-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="e0c7b-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e0c7b-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="e0c7b-106">Değer türleri ile her değişkenin veri kopyasını vardır ve diğer etkilemek için bir değişken üzerinde işlemler için mümkün değildir (hariç durumunda, ref ve out parametresi değişkenleri; bkz [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) ve [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi değiştiricisi).</span><span class="sxs-lookup"><span data-stu-id="e0c7b-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter modifier).</span></span>  
  
 <span data-ttu-id="e0c7b-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e0c7b-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="e0c7b-108">class</span><span class="sxs-lookup"><span data-stu-id="e0c7b-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="e0c7b-109">interface</span><span class="sxs-lookup"><span data-stu-id="e0c7b-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="e0c7b-110">delegate</span><span class="sxs-lookup"><span data-stu-id="e0c7b-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="e0c7b-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="e0c7b-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="e0c7b-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="e0c7b-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="e0c7b-113">object</span><span class="sxs-lookup"><span data-stu-id="e0c7b-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="e0c7b-114">string</span><span class="sxs-lookup"><span data-stu-id="e0c7b-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0c7b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c7b-115">See Also</span></span>  
 [<span data-ttu-id="e0c7b-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0c7b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e0c7b-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0c7b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e0c7b-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e0c7b-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e0c7b-119">Türler</span><span class="sxs-lookup"><span data-stu-id="e0c7b-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="e0c7b-120">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="e0c7b-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
