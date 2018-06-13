---
title: Bitwise İşleçleri (F#)
description: 'F # programlama dili kullanılabilen bit düzeyinde işleçler hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: bc653ae7ff6dd6bc2c269aaba344f073df1fb708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565333"
---
# <a name="bitwise-operators"></a><span data-ttu-id="3489e-103">Bitwise İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3489e-103">Bitwise Operators</span></span>

<span data-ttu-id="3489e-104">Bu konu, F # dilinde kullanılabilir bit düzeyinde işleçler açıklar.</span><span class="sxs-lookup"><span data-stu-id="3489e-104">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="3489e-105">Bit düzeyinde işleçler özeti</span><span class="sxs-lookup"><span data-stu-id="3489e-105">Summary of Bitwise Operators</span></span>
<span data-ttu-id="3489e-106">Aşağıdaki tabloda, F # dilinde sarmalanmamış tam sayı türleri için desteklenen bit düzeyinde işleçler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3489e-106">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="3489e-107">İşleç</span><span class="sxs-lookup"><span data-stu-id="3489e-107">Operator</span></span>|<span data-ttu-id="3489e-108">Notlar</span><span class="sxs-lookup"><span data-stu-id="3489e-108">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="3489e-109">Bit düzeyinde AND işleci.</span><span class="sxs-lookup"><span data-stu-id="3489e-109">Bitwise AND operator.</span></span> <span data-ttu-id="3489e-110">Her iki kaynak işlenen karşılık gelen bitleri 1 olan yalnızca ve yalnızca, BITS sonuç 1 değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="3489e-110">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="3489e-111">Bit düzeyinde OR işleci.</span><span class="sxs-lookup"><span data-stu-id="3489e-111">Bitwise OR operator.</span></span> <span data-ttu-id="3489e-112">BITS sonuç varsa 1 değerini ya da kaynak karşılık gelen bitleri işlenenler 1 olan.</span><span class="sxs-lookup"><span data-stu-id="3489e-112">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="3489e-113">Bit düzeyinde özel OR işleci.</span><span class="sxs-lookup"><span data-stu-id="3489e-113">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="3489e-114">Kaynak işlenen bit eşit olmayan değerleri varsa ve yalnızca varsa BITS sonuç değeri 1 gerekir.</span><span class="sxs-lookup"><span data-stu-id="3489e-114">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="3489e-115">Bit düzeyinde değilleme işleci.</span><span class="sxs-lookup"><span data-stu-id="3489e-115">Bitwise negation operator.</span></span> <span data-ttu-id="3489e-116">Bu birli işleç ve bir sonuç kaynak işlenen tüm 0 bit 1 BITS dönüştürülür ve tüm 1 BITS 0 BITS dönüştürülür üretir.</span><span class="sxs-lookup"><span data-stu-id="3489e-116">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="3489e-117">Bit düzeyinde sola kaydırma işleci.</span><span class="sxs-lookup"><span data-stu-id="3489e-117">Bitwise left-shift operator.</span></span> <span data-ttu-id="3489e-118">İkinci işlenen bit sayısına göre sola bit ilk terimiyle gölgeye sonucudur.</span><span class="sxs-lookup"><span data-stu-id="3489e-118">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="3489e-119">En önemli konumu gölgeye BITS en az önemli konumun döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="3489e-119">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="3489e-120">En az önemli BITS sıfırlarla.</span><span class="sxs-lookup"><span data-stu-id="3489e-120">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="3489e-121">İkinci bağımsız değişken türü `int32`.</span><span class="sxs-lookup"><span data-stu-id="3489e-121">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="3489e-122">Bitwise sağ kaydırma işleci.</span><span class="sxs-lookup"><span data-stu-id="3489e-122">Bitwise right-shift operator.</span></span> <span data-ttu-id="3489e-123">İkinci işlenen bit sayısına göre sağa gölgeye BITS ilk terimiyle sonucudur.</span><span class="sxs-lookup"><span data-stu-id="3489e-123">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="3489e-124">En az önemli konumu gölgeye BITS en önemli konumun döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="3489e-124">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="3489e-125">İmzasız türler için en önemli BITS sıfırlarla.</span><span class="sxs-lookup"><span data-stu-id="3489e-125">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="3489e-126">İmzalı türler için en önemli BITS olanları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="3489e-126">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="3489e-127">İkinci bağımsız değişken türü `int32`.</span><span class="sxs-lookup"><span data-stu-id="3489e-127">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="3489e-128">Bit düzeyinde işleçler ile aşağıdaki türleri kullanılabilir: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, ve `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="3489e-128">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3489e-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3489e-129">See Also</span></span>
[<span data-ttu-id="3489e-130">Simge ve İşleç Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3489e-130">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="3489e-131">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="3489e-131">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="3489e-132">Boole İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3489e-132">Boolean Operators</span></span>](boolean-operators.md)

