---
title: sizeof C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: e77076d022051cdf7d5545cc5204b3c74959d0ad
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433878"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="038a9-102">sizeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="038a9-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="038a9-103">[Yönetilmeyen bir türün](../builtin-types/unmanaged-types.md)boyutunu bayt olarak almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="038a9-103">Used to obtain the size in bytes for an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="038a9-104">Yönetilmeyen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="038a9-104">Unmanaged types include:</span></span>

- <span data-ttu-id="038a9-105">Aşağıdaki tabloda listelenen basit türler:</span><span class="sxs-lookup"><span data-stu-id="038a9-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="038a9-106">İfade</span><span class="sxs-lookup"><span data-stu-id="038a9-106">Expression</span></span>|<span data-ttu-id="038a9-107">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="038a9-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="038a9-108">1\.</span><span class="sxs-lookup"><span data-stu-id="038a9-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="038a9-109">1\.</span><span class="sxs-lookup"><span data-stu-id="038a9-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="038a9-110">2</span><span class="sxs-lookup"><span data-stu-id="038a9-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="038a9-111">2</span><span class="sxs-lookup"><span data-stu-id="038a9-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="038a9-112">4</span><span class="sxs-lookup"><span data-stu-id="038a9-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="038a9-113">4</span><span class="sxs-lookup"><span data-stu-id="038a9-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="038a9-114">8</span><span class="sxs-lookup"><span data-stu-id="038a9-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="038a9-115">8</span><span class="sxs-lookup"><span data-stu-id="038a9-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="038a9-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="038a9-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="038a9-117">4</span><span class="sxs-lookup"><span data-stu-id="038a9-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="038a9-118">8</span><span class="sxs-lookup"><span data-stu-id="038a9-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="038a9-119">16</span><span class="sxs-lookup"><span data-stu-id="038a9-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="038a9-120">1\.</span><span class="sxs-lookup"><span data-stu-id="038a9-120">1</span></span>|

- <span data-ttu-id="038a9-121">Sabit listesi türleri.</span><span class="sxs-lookup"><span data-stu-id="038a9-121">Enum types.</span></span>

- <span data-ttu-id="038a9-122">İşaretçi türleri.</span><span class="sxs-lookup"><span data-stu-id="038a9-122">Pointer types.</span></span>

- <span data-ttu-id="038a9-123">Başvuru türleri veya oluşturulmuş türler olan herhangi bir örnek alanı veya otomatik uygulanmış örnek özellikleri içermeyen Kullanıcı tanımlı yapılar.</span><span class="sxs-lookup"><span data-stu-id="038a9-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="038a9-124">Aşağıdaki örnek, öğesinin `int`boyutunun nasıl alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="038a9-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="038a9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="038a9-125">Remarks</span></span>

<span data-ttu-id="038a9-126">Sürüm 2,0 C#' den başlayarak, basit `sizeof` veya Enum türlerine uygulamak artık kodun [güvenli olmayan](unsafe.md) bir bağlamda derlenmesine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="038a9-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="038a9-127">`sizeof` İşleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="038a9-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="038a9-128">`sizeof` İşleci tarafından döndürülen değerler türündedir `int`.</span><span class="sxs-lookup"><span data-stu-id="038a9-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="038a9-129">Önceki tabloda, belirli basit türleri işlenen olarak bulunan ifadeler için `sizeof` değiştirilen sabit değerler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="038a9-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="038a9-130">Yapılar dahil tüm diğer türler için, `sizeof` işleci yalnızca güvenli olmayan kod bloklarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="038a9-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="038a9-131">Yöntemini kullanabilseniz de, bu yöntemin döndürdüğü değer her zaman tarafından `sizeof`döndürülen değerle aynı değildir. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="038a9-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="038a9-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>tür sıralandıktan sonra boyutu döndürür, ancak `sizeof` herhangi bir doldurma dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılan boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="038a9-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="038a9-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="038a9-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="038a9-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="038a9-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="038a9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="038a9-135">See also</span></span>

- [<span data-ttu-id="038a9-136">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="038a9-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="038a9-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="038a9-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="038a9-138">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="038a9-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="038a9-139">enum</span><span class="sxs-lookup"><span data-stu-id="038a9-139">enum</span></span>](enum.md)
- [<span data-ttu-id="038a9-140">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="038a9-140">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="038a9-141">Yapılar</span><span class="sxs-lookup"><span data-stu-id="038a9-141">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="038a9-142">Sabitler</span><span class="sxs-lookup"><span data-stu-id="038a9-142">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)
