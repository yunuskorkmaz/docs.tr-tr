---
title: Numaralandırmalar (F#)
description: 'F # numaralandırmalar değişmez değerler yerine kodunuzu daha okunabilir ve korunabilir hale getirmek için nasıl kullanılacağını öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4b1a61fb69403f826733893667e55991d39867c6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="enumerations"></a><span data-ttu-id="a5b48-103">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="a5b48-103">Enumerations</span></span>

<span data-ttu-id="a5b48-104">*Numaralandırmalar*, olarak da bilinen *numaralandırmaları*,, burada etiketleri atanır değerleri alt ağını için tam sayı türleridir.</span><span class="sxs-lookup"><span data-stu-id="a5b48-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="a5b48-105">Kodunu daha okunabilir ve sürdürülebilir hale değişmez değerler yerine bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5b48-105">You can use them in place of literals to make code more readable and maintainable.</span></span>


## <a name="syntax"></a><span data-ttu-id="a5b48-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5b48-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="a5b48-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5b48-107">Remarks</span></span>
<span data-ttu-id="a5b48-108">Değerlerin belirtilen dışında numaralandırma basit değerlere sahip ayrılmış bir birleşim benzer görünüyor.</span><span class="sxs-lookup"><span data-stu-id="a5b48-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="a5b48-109">Genellikle 0 veya 1 Başlat tamsayılar veya bit konumlarını temsil eden tamsayılar değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="a5b48-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="a5b48-110">Bit konumlarını temsil etmek için bir numaralandırma amaçlıyorsanız da kullanmalısınız [bayrakları](xref:System.FlagsAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a5b48-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="a5b48-111">Örneğin, bir sonek ile değişmez değerleri gibi kullanabilirsiniz böylece numaralandırması temel alınan türü kullanılan sabit değer belirlenir `1u`, `2u`ve benzeri bir işaretsiz tamsayı (`uint32`) yazın.</span><span class="sxs-lookup"><span data-stu-id="a5b48-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="a5b48-112">Adlandırılmış değerler başvurduğunuzda numaralandırma türünün adı bir niteleyici başka bir deyişle, kullanmalısınız `enum-name.value1`, yalnızca `value1`.</span><span class="sxs-lookup"><span data-stu-id="a5b48-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="a5b48-113">Bu davranış, ayrılmış birleşimler farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a5b48-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="a5b48-114">Numaralandırmalar her zaman sahip olmasıdır [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a5b48-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="a5b48-115">Aşağıdaki kod, bildirimler ve numaralandırma kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5b48-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="a5b48-116">Kolayca numaralandırmalar için temel alınan tür uygun işlecini kullanarak aşağıdaki kodda gösterildiği gibi dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5b48-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="a5b48-117">Numaralandırılmış türler aşağıdaki temel türlerinden biri olabilir: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, ve `char`.</span><span class="sxs-lookup"><span data-stu-id="a5b48-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="a5b48-118">Numaralandırma türleri .NET Framework olarak temsil kaynağından devralındı türleri `System.Enum`, sırayla devralınır `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="a5b48-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="a5b48-119">Bu nedenle, yığın veya satır içeren nesne içinde bulunan değer türleri oldukları ve temel alınan türü herhangi bir değer geçerli bir numaralandırma değeridir.</span><span class="sxs-lookup"><span data-stu-id="a5b48-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="a5b48-120">Desen eşleştirme sabit değerleri değiştiğinde adlandırılmamış değerleri yakalayan bir desen sağlamak zorunda olduğu için bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a5b48-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="a5b48-121">`enum` İşlevi F # Kitaplığı'nda bir numaralandırma değeri, daha önceden tanımlanmış, biri dışında bir değer üretmek için kullanılabilir değerleri adlı.</span><span class="sxs-lookup"><span data-stu-id="a5b48-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="a5b48-122">Kullandığınız `enum` gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="a5b48-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="a5b48-123">Varsayılan `enum` işlevi çalışır türüyle `int32`.</span><span class="sxs-lookup"><span data-stu-id="a5b48-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="a5b48-124">Bu nedenle, temel alınan diğer türlerine sahip Numaralandırma türleri ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a5b48-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="a5b48-125">Bunun yerine, aşağıdaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5b48-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a><span data-ttu-id="a5b48-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5b48-126">See Also</span></span>
[<span data-ttu-id="a5b48-127">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a5b48-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a5b48-128">Tür Değiştirme ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="a5b48-128">Casting and Conversions</span></span>](casting-and-conversions.md)
