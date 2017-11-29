---
title: "Başvuru Türleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="22b08-102">Başvuru Türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="22b08-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="22b08-103">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="22b08-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="22b08-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="22b08-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="22b08-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="22b08-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="22b08-106">Değer türleri ile her değişkenin veri kopyasını vardır ve diğer etkilemek için bir değişken üzerinde işlemler için mümkün değildir (durumunda ref ve out parametresi değişkenleri Bkz dışında [ref](../../../csharp/language-reference/keywords/ref.md) ve [çıkış parametresi Değiştirici](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="22b08-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of ref and out parameter variables, see [ref](../../../csharp/language-reference/keywords/ref.md) and [out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span></span>  
  
 <span data-ttu-id="22b08-107">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="22b08-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="22b08-108">sınıfı</span><span class="sxs-lookup"><span data-stu-id="22b08-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="22b08-109">arabirimi</span><span class="sxs-lookup"><span data-stu-id="22b08-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="22b08-110">temsilci seçme</span><span class="sxs-lookup"><span data-stu-id="22b08-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="22b08-111">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="22b08-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="22b08-112">dinamik</span><span class="sxs-lookup"><span data-stu-id="22b08-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="22b08-113">Nesne</span><span class="sxs-lookup"><span data-stu-id="22b08-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="22b08-114">dize</span><span class="sxs-lookup"><span data-stu-id="22b08-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="22b08-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22b08-115">See Also</span></span>  
 [<span data-ttu-id="22b08-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="22b08-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="22b08-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="22b08-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="22b08-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="22b08-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="22b08-119">Türler</span><span class="sxs-lookup"><span data-stu-id="22b08-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="22b08-120">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="22b08-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
