---
title: Numaralandırmalar
description: Kodunuzun daha okunabilir ve F# sürdürülebilir olmasını sağlamak için sabit değerlerin yerine Numaralandırmaların nasıl kullanılacağını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630343"
---
# <a name="enumerations"></a><span data-ttu-id="354c0-103">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="354c0-103">Enumerations</span></span>

<span data-ttu-id="354c0-104">Numaralandırmalar olarak da bilinen *numaralandırmalar*, etiketlerin değerlerinin bir alt kümesine atandığı integral türleridir.</span><span class="sxs-lookup"><span data-stu-id="354c0-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="354c0-105">Kodu daha okunaklı ve bakım yapılabilir hale getirmek için bunları değişmez değerler yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="354c0-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="354c0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="354c0-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="354c0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="354c0-107">Remarks</span></span>

<span data-ttu-id="354c0-108">Bir numaralandırma, değerlerin belirtilemesi dışında basit değerleri olan ayrılmış bir birleşime benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="354c0-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="354c0-109">Değerler genellikle 0 veya 1 ' den başlayan tamsayılar veya bit konumlarını temsil eden tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="354c0-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="354c0-110">Bir numaralandırma, bit konumlarını temsil etmek için tasarlanıyorsa, [Flags](xref:System.FlagsAttribute) özniteliğini de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="354c0-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="354c0-111">Sabit listesinin temel alınan türü, kullanılan değişmez değere göre belirlenir, böylece örneğin, bir işaretsiz tamsayı ( `1u``uint32`) türü için,, ve gibi bir soneke `2u`sahip değişmez değerler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="354c0-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="354c0-112">Adlandırılmış değerlere başvurduğunuzda, sabit listesi türünün adını bir niteleyici olarak kullanmanız gerekir, yani `enum-name.value1`, yalnızca `value1`değil.</span><span class="sxs-lookup"><span data-stu-id="354c0-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="354c0-113">Bu davranış, ayrılmış birleşimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="354c0-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="354c0-114">Bunun nedeni, Numaralandırmaların her zaman [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliğine sahip olmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="354c0-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="354c0-115">Aşağıdaki kod, bir numaralandırmanın bildirimini ve kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="354c0-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="354c0-116">Aşağıdaki kodda gösterildiği gibi, uygun işleci kullanarak numaralandırmaları kolayca temel alınan türe dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="354c0-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="354c0-117">Numaralandırılmış türler aşağıdaki `sbyte`temel türlerden birine sahip olabilir:, `int64` `int32` `uint16` `byte`, `int16`,,, `uint32`,, `uint16`, `uint64`ve. `char`</span><span class="sxs-lookup"><span data-stu-id="354c0-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="354c0-118">Sabit listesi türleri, ' den devralınan türler `System.Enum`olarak .NET Framework temsil edilir ve bundan sonra öğesinden `System.ValueType`devralınır.</span><span class="sxs-lookup"><span data-stu-id="354c0-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="354c0-119">Bu nedenle, yığın üzerinde bulunan veya kapsayan nesnede satır içi olan değer türlerdir ve temel alınan türün herhangi bir değeri numaralandırmanın geçerli bir değeridir.</span><span class="sxs-lookup"><span data-stu-id="354c0-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="354c0-120">Bu, adlandırılmamış değerleri yakalayan bir model sağlamanız gerektiğinden, numaralandırma değerleri üzerinde kalıp eşleştirilirken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="354c0-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="354c0-121">F# Kitaplığındaki işlev, önceden tanımlanmış adlandırılmış değerlerden biri dışında bir değer olan bir sabit listesi değeri oluşturmak için `enum` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="354c0-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="354c0-122">`enum` İşlevini aşağıdaki şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="354c0-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="354c0-123">Varsayılan `enum` işlev, türüyle `int32`çalışır.</span><span class="sxs-lookup"><span data-stu-id="354c0-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="354c0-124">Bu nedenle, diğer temel türlerine sahip sabit listesi türleriyle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="354c0-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="354c0-125">Bunun yerine, aşağıdakileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="354c0-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="354c0-126">Ayrıca, numaralandırmalar için durumlar her zaman olarak `public`yayılır.</span><span class="sxs-lookup"><span data-stu-id="354c0-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="354c0-127">Bu sayede, ve .NET platformunun geri C# kalanı ile hizalanır.</span><span class="sxs-lookup"><span data-stu-id="354c0-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="354c0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="354c0-128">See also</span></span>

- [<span data-ttu-id="354c0-129">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="354c0-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="354c0-130">Tür Değiştirme ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="354c0-130">Casting and Conversions</span></span>](casting-and-conversions.md)
