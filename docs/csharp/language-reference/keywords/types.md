---
title: Türler (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
ms.openlocfilehash: c5c29f5d9a1a4e25e2d5f8816a0df31fa9a91fb1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463318"
---
# <a name="types-c-reference"></a><span data-ttu-id="42a97-102">Türler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="42a97-102">Types (C# Reference)</span></span>
<span data-ttu-id="42a97-103">C# sistem yazarak aşağıdaki kategorileri içerir:</span><span class="sxs-lookup"><span data-stu-id="42a97-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="42a97-104">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="42a97-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="42a97-105">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="42a97-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="42a97-106">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="42a97-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="42a97-107">Değer türleri olan değişkenler verileri depolamak ve başvuru türleri olan depolama başvurularının gerçek veriler.</span><span class="sxs-lookup"><span data-stu-id="42a97-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="42a97-108">Başvuru türleri, nesneleri olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="42a97-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="42a97-109">İşaretçi türleri yalnızca kullanılabilir [güvenli](../../../csharp/language-reference/keywords/unsafe.md) modu.</span><span class="sxs-lookup"><span data-stu-id="42a97-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="42a97-110">Bir değer türü bir başvuru türüne dönüştürün ve bir değer türü kullanarak yeniden mümkündür [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="42a97-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="42a97-111">Paketlenmiş değer türü hariç olmak üzere, bir başvuru türü bir değer türüne dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="42a97-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="42a97-112">Bu bölüm ayrıca tanıtır [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="42a97-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="42a97-113">Değer türleri de ek bir değer olmayan durum depolayabilecekleri anlamına gelir boş değer atanabilir,.</span><span class="sxs-lookup"><span data-stu-id="42a97-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="42a97-114">Daha fazla bilgi için [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="42a97-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a97-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42a97-115">See Also</span></span>

- [<span data-ttu-id="42a97-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="42a97-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="42a97-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="42a97-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="42a97-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="42a97-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="42a97-119">Türler için Başvuru Tabloları</span><span class="sxs-lookup"><span data-stu-id="42a97-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [<span data-ttu-id="42a97-120">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="42a97-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="42a97-121">Türler</span><span class="sxs-lookup"><span data-stu-id="42a97-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
