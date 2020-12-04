---
title: İfade düzeyinde tercihler
description: İfade düzeyi tercihleri için kod analizi dil kuralları hakkında bilgi edinin
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 9933111b1ed76166e5ae86e9bc1a2332c3c77c81
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "96589825"
---
# <a name="expression-level-preferences"></a><span data-ttu-id="b8611-103">İfade düzeyinde tercihler</span><span class="sxs-lookup"><span data-stu-id="b8611-103">Expression-level preferences</span></span>

## <a name="net-expression-level-preferences"></a><span data-ttu-id="b8611-104">.NET ifade düzeyi tercihleri</span><span class="sxs-lookup"><span data-stu-id="b8611-104">.NET expression-level preferences</span></span>

<span data-ttu-id="b8611-105">Bu bölümdeki stil kuralları, C# ve Visual Basic ortak olan aşağıdaki ifade düzeyi tercihleri ilgilendirdir:</span><span class="sxs-lookup"><span data-stu-id="b8611-105">The style rules in this section concern the following expression-level preferences that are common to C# and Visual Basic:</span></span>

- [<span data-ttu-id="b8611-106">Switch ifadesine eksik durum ekleme (IDE0010)</span><span class="sxs-lookup"><span data-stu-id="b8611-106">Add missing cases to switch statement (IDE0010)</span></span>](ide0010.md)
- [<span data-ttu-id="b8611-107">Nesne başlatıcılarının kullanımı (IDE0017)</span><span class="sxs-lookup"><span data-stu-id="b8611-107">Use object initializers (IDE0017)</span></span>](ide0017.md)
- [<span data-ttu-id="b8611-108">Koleksiyon Başlatıcıları kullanma (IDE0028)</span><span class="sxs-lookup"><span data-stu-id="b8611-108">Use collection initializers (IDE0028)</span></span>](ide0028.md)
- [<span data-ttu-id="b8611-109">Auto özelliğini kullan (IDE0032)</span><span class="sxs-lookup"><span data-stu-id="b8611-109">Use auto property (IDE0032)</span></span>](ide0032.md)
- [<span data-ttu-id="b8611-110">Açık olarak sağlanmış demet adı kullanın (IDE0033)</span><span class="sxs-lookup"><span data-stu-id="b8611-110">Use explicitly provided tuple name (IDE0033)</span></span>](ide0033.md)
- [<span data-ttu-id="b8611-111">Gösterilen üye adı kullan (IDE0037)</span><span class="sxs-lookup"><span data-stu-id="b8611-111">Use inferred member name (IDE0037)</span></span>](ide0037.md)
- [<span data-ttu-id="b8611-112">Atama için koşullu ifade kullan (IDE0045)</span><span class="sxs-lookup"><span data-stu-id="b8611-112">Use conditional expression for assignment (IDE0045)</span></span>](ide0045.md)
- [<span data-ttu-id="b8611-113">Return (IDE0046) için koşullu ifade kullan</span><span class="sxs-lookup"><span data-stu-id="b8611-113">Use conditional expression for return (IDE0046)</span></span>](ide0046.md)
- [<span data-ttu-id="b8611-114">Anonim türü kayıt türüne Dönüştür (IDE0050)</span><span class="sxs-lookup"><span data-stu-id="b8611-114">Convert anonymous type to tuple (IDE0050)</span></span>](ide0050.md)
- [<span data-ttu-id="b8611-115">Bileşik atama kullan (IDE0054 ve IDE0074)</span><span class="sxs-lookup"><span data-stu-id="b8611-115">Use compound assignment (IDE0054 and IDE0074)</span></span>](ide0054-ide0074.md)
- [<span data-ttu-id="b8611-116">' System. HashCode. Birleştir ' kullanın (IDE0070)</span><span class="sxs-lookup"><span data-stu-id="b8611-116">Use 'System.HashCode.Combine' (IDE0070)</span></span>](ide0070.md)
- [<span data-ttu-id="b8611-117">İlişkilendirmeyi basitleştirme (IDE0071)</span><span class="sxs-lookup"><span data-stu-id="b8611-117">Simplify interpolation (IDE0071)</span></span>](ide0071.md)
- [<span data-ttu-id="b8611-118">Koşullu ifadeyi basitleştirme (IDE0075)</span><span class="sxs-lookup"><span data-stu-id="b8611-118">Simplify conditional expression (IDE0075)</span></span>](ide0075.md)
- [<span data-ttu-id="b8611-119">' Typeof ' öğesini ' NameOf ' öğesine Dönüştür (IDE0082)</span><span class="sxs-lookup"><span data-stu-id="b8611-119">Convert 'typeof' to 'nameof' (IDE0082)</span></span>](ide0082.md)

## <a name="c-expression-level-preferences"></a><span data-ttu-id="b8611-120">C# ifade düzeyi tercihleri</span><span class="sxs-lookup"><span data-stu-id="b8611-120">C# expression-level preferences</span></span>

<span data-ttu-id="b8611-121">Bu bölümdeki stil kuralları C# ' ye özgü aşağıdaki ifade düzeyi tercihleri ile ilgilendirin:</span><span class="sxs-lookup"><span data-stu-id="b8611-121">The style rules in this section concern the following expression-level preferences that are specific to C#:</span></span>

- [<span data-ttu-id="b8611-122">Satır içi değişken bildirimi (IDE0018)</span><span class="sxs-lookup"><span data-stu-id="b8611-122">Inline variable declaration (IDE0018)</span></span>](ide0018.md)
- [<span data-ttu-id="b8611-123">' Default ' ifadesini Basitleştir (IDE0034)</span><span class="sxs-lookup"><span data-stu-id="b8611-123">Simplify 'default' expression (IDE0034)</span></span>](ide0034.md)
- [<span data-ttu-id="b8611-124">Lambda yerine yerel işlev kullan (IDE0039)</span><span class="sxs-lookup"><span data-stu-id="b8611-124">Use local function instead of lambda (IDE0039)</span></span>](ide0039.md)
- [<span data-ttu-id="b8611-125">Değişken bildirimini kaldırma (IDE0042)</span><span class="sxs-lookup"><span data-stu-id="b8611-125">Deconstruct variable declaration (IDE0042)</span></span>](ide0042.md)
- [<span data-ttu-id="b8611-126">Dizin işleci kullan (IDE0056)</span><span class="sxs-lookup"><span data-stu-id="b8611-126">Use index operator (IDE0056)</span></span>](ide0056.md)
- [<span data-ttu-id="b8611-127">Range işleci kullan (IDE0057)</span><span class="sxs-lookup"><span data-stu-id="b8611-127">Use range operator (IDE0057)</span></span>](ide0057.md)
- [<span data-ttu-id="b8611-128">Anahtar ifadesine eksik durum ekleme (IDE0072)</span><span class="sxs-lookup"><span data-stu-id="b8611-128">Add missing cases to switch expression (IDE0072)</span></span>](ide0072.md)
- [<span data-ttu-id="b8611-129">' New ' ifadesini Basitleştir (IDE0090)</span><span class="sxs-lookup"><span data-stu-id="b8611-129">Simplify 'new' expression (IDE0090)</span></span>](ide0090.md)

## <a name="see-also"></a><span data-ttu-id="b8611-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8611-130">See also</span></span>

- [<span data-ttu-id="b8611-131">Kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="b8611-131">Code style rules reference</span></span>](index.md)
- [<span data-ttu-id="b8611-132">Kod stili dil kuralları</span><span class="sxs-lookup"><span data-stu-id="b8611-132">Code style language rules</span></span>](language-rules.md)
