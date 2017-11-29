---
title: "Bitwise İşleçleri (F#)"
description: "F # programlama dili kullanılabilen bit düzeyinde işleçler hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a><span data-ttu-id="d81fe-104">Bitwise İşleçleri</span><span class="sxs-lookup"><span data-stu-id="d81fe-104">Bitwise Operators</span></span>

<span data-ttu-id="d81fe-105">Bu konu, F # dilinde kullanılabilir bit düzeyinde işleçler açıklar.</span><span class="sxs-lookup"><span data-stu-id="d81fe-105">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="d81fe-106">Bit düzeyinde işleçler özeti</span><span class="sxs-lookup"><span data-stu-id="d81fe-106">Summary of Bitwise Operators</span></span>
<span data-ttu-id="d81fe-107">Aşağıdaki tabloda, F # dilinde sarmalanmamış tam sayı türleri için desteklenen bit düzeyinde işleçler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d81fe-107">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="d81fe-108">İşleç</span><span class="sxs-lookup"><span data-stu-id="d81fe-108">Operator</span></span>|<span data-ttu-id="d81fe-109">Notlar</span><span class="sxs-lookup"><span data-stu-id="d81fe-109">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="d81fe-110">Bit düzeyinde AND işleci.</span><span class="sxs-lookup"><span data-stu-id="d81fe-110">Bitwise AND operator.</span></span> <span data-ttu-id="d81fe-111">Her iki kaynak işlenen karşılık gelen bitleri 1 olan yalnızca ve yalnızca, BITS sonuç 1 değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="d81fe-111">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="d81fe-112">Bit düzeyinde OR işleci.</span><span class="sxs-lookup"><span data-stu-id="d81fe-112">Bitwise OR operator.</span></span> <span data-ttu-id="d81fe-113">BITS sonuç varsa 1 değerini ya da kaynak karşılık gelen bitleri işlenenler 1 olan.</span><span class="sxs-lookup"><span data-stu-id="d81fe-113">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="d81fe-114">Bit düzeyinde özel OR işleci.</span><span class="sxs-lookup"><span data-stu-id="d81fe-114">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="d81fe-115">Kaynak işlenen bit eşit olmayan değerleri varsa ve yalnızca varsa BITS sonuç değeri 1 gerekir.</span><span class="sxs-lookup"><span data-stu-id="d81fe-115">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="d81fe-116">Bit düzeyinde değilleme işleci.</span><span class="sxs-lookup"><span data-stu-id="d81fe-116">Bitwise negation operator.</span></span> <span data-ttu-id="d81fe-117">Bu birli işleç ve bir sonuç kaynak işlenen tüm 0 bit 1 BITS dönüştürülür ve tüm 1 BITS 0 BITS dönüştürülür üretir.</span><span class="sxs-lookup"><span data-stu-id="d81fe-117">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="d81fe-118">Bit düzeyinde sola kaydırma işleci.</span><span class="sxs-lookup"><span data-stu-id="d81fe-118">Bitwise left-shift operator.</span></span> <span data-ttu-id="d81fe-119">İkinci işlenen bit sayısına göre sola bit ilk terimiyle gölgeye sonucudur.</span><span class="sxs-lookup"><span data-stu-id="d81fe-119">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="d81fe-120">En önemli konumu gölgeye BITS en az önemli konumun döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="d81fe-120">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="d81fe-121">En az önemli BITS sıfırlarla.</span><span class="sxs-lookup"><span data-stu-id="d81fe-121">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="d81fe-122">İkinci bağımsız değişken türü `int32`.</span><span class="sxs-lookup"><span data-stu-id="d81fe-122">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="d81fe-123">Bitwise sağ kaydırma işleci.</span><span class="sxs-lookup"><span data-stu-id="d81fe-123">Bitwise right-shift operator.</span></span> <span data-ttu-id="d81fe-124">İkinci işlenen bit sayısına göre sağa gölgeye BITS ilk terimiyle sonucudur.</span><span class="sxs-lookup"><span data-stu-id="d81fe-124">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="d81fe-125">En az önemli konumu gölgeye BITS en önemli konumun döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="d81fe-125">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="d81fe-126">İmzasız türler için en önemli BITS sıfırlarla.</span><span class="sxs-lookup"><span data-stu-id="d81fe-126">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="d81fe-127">İmzalı türler için en önemli BITS olanları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d81fe-127">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="d81fe-128">İkinci bağımsız değişken türü `int32`.</span><span class="sxs-lookup"><span data-stu-id="d81fe-128">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="d81fe-129">Bit düzeyinde işleçler ile aşağıdaki türleri kullanılabilir: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, ve `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="d81fe-129">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d81fe-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d81fe-130">See Also</span></span>
[<span data-ttu-id="d81fe-131">Simge ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="d81fe-131">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="d81fe-132">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="d81fe-132">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="d81fe-133">Boole işleçleri</span><span class="sxs-lookup"><span data-stu-id="d81fe-133">Boolean Operators</span></span>](boolean-operators.md)

