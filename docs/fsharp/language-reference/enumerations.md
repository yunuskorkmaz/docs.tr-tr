---
title: Listelemeler
description: 'Kodunuzun daha okunabilir ve sürdürülebilir olmasını sağlamak için sabit değer yerine F # numaralandırmaları nasıl kullanacağınızı öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812113"
---
# <a name="enumerations"></a><span data-ttu-id="7aa61-103">Listelemeler</span><span class="sxs-lookup"><span data-stu-id="7aa61-103">Enumerations</span></span>

<span data-ttu-id="7aa61-104">*Numaralandırmalar*olarak da bilinen *numaralandırmalar*, etiketlerin değerlerinin bir alt kümesine atandığı integral türleridir.</span><span class="sxs-lookup"><span data-stu-id="7aa61-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="7aa61-105">Kodu daha okunaklı ve bakım yapılabilir hale getirmek için bunları değişmez değerler yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aa61-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="7aa61-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7aa61-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="7aa61-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7aa61-107">Remarks</span></span>

<span data-ttu-id="7aa61-108">Bir numaralandırma, değerlerin belirtilemesi dışında basit değerleri olan ayrılmış bir birleşime benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="7aa61-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="7aa61-109">Değerler genellikle 0 veya 1 ' den başlayan tamsayılar veya bit konumlarını temsil eden tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="7aa61-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="7aa61-110">Bir numaralandırma, bit konumlarını temsil etmek için tasarlanıyorsa, [Flags](xref:System.FlagsAttribute) özniteliğini de kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="7aa61-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="7aa61-111">Sabit listesinin temel alınan türü, kullanılan değişmez değere göre belirlenir, böylece örneğin, bir `1u` `2u` işaretsiz tamsayı () türü için,, ve gibi bir soneke sahip değişmez değerler kullanabilirsiniz `uint32` .</span><span class="sxs-lookup"><span data-stu-id="7aa61-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="7aa61-112">Adlandırılmış değerlere başvurduğunuzda, sabit listesi türünün adını bir niteleyici olarak kullanmanız gerekir, yani, `enum-name.value1` yalnızca değil `value1` .</span><span class="sxs-lookup"><span data-stu-id="7aa61-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="7aa61-113">Bu davranış, ayrılmış birleşimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7aa61-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="7aa61-114">Bunun nedeni, Numaralandırmaların her zaman [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) özniteliğine sahip olmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="7aa61-114">This is because enumerations always have the [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) attribute.</span></span>

<span data-ttu-id="7aa61-115">Aşağıdaki kod, bir numaralandırmanın bildirimini ve kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7aa61-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="7aa61-116">Aşağıdaki kodda gösterildiği gibi, uygun işleci kullanarak numaralandırmaları kolayca temel alınan türe dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aa61-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="7aa61-117">Numaralandırılmış türler aşağıdaki temel türlerden birine sahip olabilir: `sbyte` ,,, `byte` `int16` `uint16` , `int32` , `uint32` , `int64` , `uint16` , `uint64` ve `char` .</span><span class="sxs-lookup"><span data-stu-id="7aa61-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="7aa61-118">Sabit listesi türleri, ' den devralınan türler olarak .NET Framework temsil edilir `System.Enum` ve bundan sonra öğesinden devralınır `System.ValueType` .</span><span class="sxs-lookup"><span data-stu-id="7aa61-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="7aa61-119">Bu nedenle, yığın üzerinde bulunan veya kapsayan nesnede satır içi olan değer türlerdir ve temel alınan türün herhangi bir değeri numaralandırmanın geçerli bir değeridir.</span><span class="sxs-lookup"><span data-stu-id="7aa61-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="7aa61-120">Bu, adlandırılmamış değerleri yakalayan bir model sağlamanız gerektiğinden, numaralandırma değerleri üzerinde kalıp eşleştirilirken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7aa61-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="7aa61-121">`enum`F # kitaplığındaki işlev, önceden tanımlanmış adlandırılmış değerlerden biri dışında bir değer olan bir sabit listesi değeri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7aa61-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="7aa61-122">`enum`İşlevini aşağıdaki şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="7aa61-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="7aa61-123">Varsayılan `enum` işlev, türüyle çalışır `int32` .</span><span class="sxs-lookup"><span data-stu-id="7aa61-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="7aa61-124">Bu nedenle, diğer temel türlerine sahip sabit listesi türleriyle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7aa61-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="7aa61-125">Bunun yerine, aşağıdakileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aa61-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="7aa61-126">Ayrıca, numaralandırmalar için durumlar her zaman olarak yayılır `public` .</span><span class="sxs-lookup"><span data-stu-id="7aa61-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="7aa61-127">Bu, C# ve .NET platformunun geri kalanı ile hizalanır.</span><span class="sxs-lookup"><span data-stu-id="7aa61-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aa61-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aa61-128">See also</span></span>

- [<span data-ttu-id="7aa61-129">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="7aa61-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7aa61-130">Atama ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="7aa61-130">Casting and Conversions</span></span>](casting-and-conversions.md)
