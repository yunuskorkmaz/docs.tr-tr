---
title: "Türler (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c7285e237b04c1290391c4bba3e62886dceb83c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-reference"></a><span data-ttu-id="1f9a9-102">Türler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1f9a9-102">Types (C# Reference)</span></span>
<span data-ttu-id="1f9a9-103">C# sistem yazarak aşağıdaki kategorileri içerir:</span><span class="sxs-lookup"><span data-stu-id="1f9a9-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="1f9a9-104">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="1f9a9-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="1f9a9-105">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="1f9a9-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="1f9a9-106">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="1f9a9-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="1f9a9-107">Değer türleri olan değişkenler verileri depolamak ve başvuru türleri olan gerçek veri başvurularını saklayın.</span><span class="sxs-lookup"><span data-stu-id="1f9a9-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="1f9a9-108">Başvuru türleri nesneler olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1f9a9-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="1f9a9-109">İşaretçi türleri yalnızca kullanılabilir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) modu.</span><span class="sxs-lookup"><span data-stu-id="1f9a9-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="1f9a9-110">Bu değer türüne bir başvuru türüne dönüştürmek ve bir değer türü kullanarak yeniden mümkündür [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="1f9a9-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="1f9a9-111">Paketlenmiş değer türü dışında bir değer türüne bir başvuru türü dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="1f9a9-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="1f9a9-112">Bu bölüm ayrıca tanıtır [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="1f9a9-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="1f9a9-113">Değer türleri de ek bir değeri olmayan durum depolayabilecekleri başka bir deyişle, boş değer atanabilir,.</span><span class="sxs-lookup"><span data-stu-id="1f9a9-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="1f9a9-114">Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f9a9-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9a9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f9a9-115">See Also</span></span>  
 [<span data-ttu-id="1f9a9-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1f9a9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1f9a9-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1f9a9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1f9a9-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1f9a9-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1f9a9-119">Türler için başvuru tabloları</span><span class="sxs-lookup"><span data-stu-id="1f9a9-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="1f9a9-120">Atama ve tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="1f9a9-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="1f9a9-121">Türler</span><span class="sxs-lookup"><span data-stu-id="1f9a9-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
