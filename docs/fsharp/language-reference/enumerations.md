---
title: Numaralandırmalar
description: Nasıl kullanacağınızı öğrenin F# kodunuzu daha okunabilir ve sürdürülebilir hale getirmek için değişmez değerler yerine numaralandırmalar.
ms.date: 05/16/2016
ms.openlocfilehash: a8839b73de074f62606b70ffe969a53b3db753bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921582"
---
# <a name="enumerations"></a><span data-ttu-id="30838-103">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="30838-103">Enumerations</span></span>

<span data-ttu-id="30838-104">*Numaralandırmalar*olarak da bilinen *numaralandırmalar*,, etiketleri değerlerin bir alt kümesine atanmış burada integral türleridir.</span><span class="sxs-lookup"><span data-stu-id="30838-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="30838-105">Kod daha okunabilir ve sürdürülebilir hale getirmek için değişmez değerler yerine bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30838-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="30838-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30838-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="30838-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30838-107">Remarks</span></span>

<span data-ttu-id="30838-108">Değerleri belirtilen hariç, bir numaralandırma gibi basit değerler, ayrılmış bir birleşim arar.</span><span class="sxs-lookup"><span data-stu-id="30838-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="30838-109">Genellikle 0 veya 1 başlayan tamsayılar ya da bit konumlarını temsil eden tamsayı değerler.</span><span class="sxs-lookup"><span data-stu-id="30838-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="30838-110">Bit konumlarını temsil eden bir numaralandırma hedeflediyseniz de kullanmalısınız [bayrakları](xref:System.FlagsAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="30838-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="30838-111">Örneğin, bir son eki ile sabit değerleri gibi kullanabilirsiniz, böylece sabit listesinin temel alınan türü kullanılan değişmez değer belirlenir `1u`, `2u`ve benzeri işaretsiz tamsayı (`uint32`) türü.</span><span class="sxs-lookup"><span data-stu-id="30838-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="30838-112">Adlandırılmış değerler için başvurduğunuzda, numaralandırma türü adı bir niteleyici diğer bir deyişle, kullanmalısınız `enum-name.value1`, yalnızca `value1`.</span><span class="sxs-lookup"><span data-stu-id="30838-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="30838-113">Bu davranış, ayrılmış birleşimler farklıdır.</span><span class="sxs-lookup"><span data-stu-id="30838-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="30838-114">Her zaman Numaralandırmaların olmasıdır [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="30838-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="30838-115">Aşağıdaki kod, bildirim ve bir numaralandırma kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30838-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="30838-116">Kolayca numaralandırma için temeldeki tür uygun işleci kullanılarak aşağıdaki kodda gösterildiği gibi dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30838-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="30838-117">Numaralandırılmış türler aşağıdaki temel türlerden biri olabilir: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, ve `char`.</span><span class="sxs-lookup"><span data-stu-id="30838-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="30838-118">Numaralandırma türleri öğesinden devralınan türler olarak .NET Framework'teki gösterilir `System.Enum`, sırayla devralınır `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="30838-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="30838-119">Bu nedenle, yığın veya satır içeren bir nesne içinde bulunan değer türleri olduklarını ve temel türün herhangi bir değer geçerli bir numaralandırma değeridir.</span><span class="sxs-lookup"><span data-stu-id="30838-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="30838-120">Sabit desen değerleri değiştiğinde, isimsiz değerler yakalayan bir desen sağlamak sahip olduğunuz için bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="30838-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="30838-121">`enum` İşlevi F# kitaplığı bir sabit listesi değeri, hatta önceden tanımlanmış, biri dışında bir değer oluşturmak için kullanılabilir değerleri adlı.</span><span class="sxs-lookup"><span data-stu-id="30838-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="30838-122">Kullandığınız `enum` gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="30838-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="30838-123">Varsayılan `enum` işlev türüyle çalışır `int32`.</span><span class="sxs-lookup"><span data-stu-id="30838-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="30838-124">Bu nedenle, temel alınan diğer türleri Numaralandırma türleri ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30838-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="30838-125">Bunun yerine, aşağıdaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="30838-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="30838-126">Ayrıca, her zaman sabit listeleri olarak gönderilir için durumlarda `public`.</span><span class="sxs-lookup"><span data-stu-id="30838-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="30838-127">Bu, böylelikle C# ve .NET platformu geri kalanı ile hizalanır.</span><span class="sxs-lookup"><span data-stu-id="30838-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="30838-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30838-128">See also</span></span>

- [<span data-ttu-id="30838-129">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="30838-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="30838-130">Tür Değiştirme ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="30838-130">Casting and Conversions</span></span>](casting-and-conversions.md)