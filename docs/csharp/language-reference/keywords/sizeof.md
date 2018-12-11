---
title: sizeof - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 1c5526366651d7e6623724c939b08ac46aa7db56
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242639"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="8f16f-102">sizeof (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8f16f-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="8f16f-103">Yönetilmeyen bir tür için bayt cinsinden boyutunu almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f16f-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="8f16f-104">Yönetilmeyen türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8f16f-104">Unmanaged types include:</span></span>

- <span data-ttu-id="8f16f-105">Aşağıdaki tabloda listelenen basit türler:</span><span class="sxs-lookup"><span data-stu-id="8f16f-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="8f16f-106">İfade</span><span class="sxs-lookup"><span data-stu-id="8f16f-106">Expression</span></span>|<span data-ttu-id="8f16f-107">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="8f16f-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="8f16f-108">1.</span><span class="sxs-lookup"><span data-stu-id="8f16f-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="8f16f-109">1.</span><span class="sxs-lookup"><span data-stu-id="8f16f-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="8f16f-110">2</span><span class="sxs-lookup"><span data-stu-id="8f16f-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="8f16f-111">2</span><span class="sxs-lookup"><span data-stu-id="8f16f-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="8f16f-112">4</span><span class="sxs-lookup"><span data-stu-id="8f16f-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="8f16f-113">4</span><span class="sxs-lookup"><span data-stu-id="8f16f-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="8f16f-114">8</span><span class="sxs-lookup"><span data-stu-id="8f16f-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="8f16f-115">8</span><span class="sxs-lookup"><span data-stu-id="8f16f-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="8f16f-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="8f16f-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="8f16f-117">4</span><span class="sxs-lookup"><span data-stu-id="8f16f-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="8f16f-118">8</span><span class="sxs-lookup"><span data-stu-id="8f16f-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="8f16f-119">16</span><span class="sxs-lookup"><span data-stu-id="8f16f-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="8f16f-120">1.</span><span class="sxs-lookup"><span data-stu-id="8f16f-120">1</span></span>|

- <span data-ttu-id="8f16f-121">Numaralandırma türleri.</span><span class="sxs-lookup"><span data-stu-id="8f16f-121">Enum types.</span></span>

- <span data-ttu-id="8f16f-122">İşaretçi türleri.</span><span class="sxs-lookup"><span data-stu-id="8f16f-122">Pointer types.</span></span>

- <span data-ttu-id="8f16f-123">Tüm örnek alanları veya başvuru türleri veya oluşturulan türler otomatik olarak uygulanan örnek özellikler içermeyen kullanıcı tarafından tanımlanan yapılar.</span><span class="sxs-lookup"><span data-stu-id="8f16f-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="8f16f-124">Aşağıdaki örnek boyutunu almak nasıl gösterir bir `int`:</span><span class="sxs-lookup"><span data-stu-id="8f16f-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="8f16f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f16f-125">Remarks</span></span>

<span data-ttu-id="8f16f-126">C# 2.0 sürümünden itibaren uygulama `sizeof` basit veya sabit listesi türleri artık gerektirir kod içinde derlenecek bir [güvenli](unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="8f16f-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="8f16f-127">`sizeof` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="8f16f-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="8f16f-128">Tarafından döndürülen değerler `sizeof` işleci, tür `int`.</span><span class="sxs-lookup"><span data-stu-id="8f16f-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="8f16f-129">Önceki tablonun gösterdiği için yerine sabit değerler `sizeof` işlenen olarak bazı basit türler sahip ifadeler.</span><span class="sxs-lookup"><span data-stu-id="8f16f-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="8f16f-130">Yapılar, diğer tüm türleri için de dahil olmak üzere `sizeof` işleci yalnızca güvenli olmayan kod blokları içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f16f-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="8f16f-131">Hizmetini kullanıyor olsanız da <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemi, bu yöntem tarafından döndürülen değeri değil her zaman aynı tarafından döndürülen değer olarak `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="8f16f-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="8f16f-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> türü sıralanmış sonra ise boyutunu döndürür `sizeof` herhangi doldurma dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılan boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f16f-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="8f16f-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f16f-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="8f16f-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8f16f-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8f16f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f16f-135">See also</span></span>

- [<span data-ttu-id="8f16f-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8f16f-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8f16f-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8f16f-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8f16f-138">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8f16f-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8f16f-139">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8f16f-139">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="8f16f-140">enum</span><span class="sxs-lookup"><span data-stu-id="8f16f-140">enum</span></span>](enum.md)
- [<span data-ttu-id="8f16f-141">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="8f16f-141">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="8f16f-142">Yapılar</span><span class="sxs-lookup"><span data-stu-id="8f16f-142">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="8f16f-143">Sabitler</span><span class="sxs-lookup"><span data-stu-id="8f16f-143">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)