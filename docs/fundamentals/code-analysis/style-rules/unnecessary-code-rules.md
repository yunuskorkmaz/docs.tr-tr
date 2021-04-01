---
title: Gereksiz kod kuralları
description: Kod Analizi gereksiz kod kuralları hakkında bilgi edinin
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589869"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="b4501-103">Gereksiz kod kuralları</span><span class="sxs-lookup"><span data-stu-id="b4501-103">Unnecessary code rules</span></span>

<span data-ttu-id="b4501-104">Gereksiz kod kuralları, kod tabanının gereksiz ve yeniden düzenlenmiş veya kaldırılabilir olan farklı parçalarını belirler.</span><span class="sxs-lookup"><span data-stu-id="b4501-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="b4501-105">Gereksiz kodun varlığı aşağıdaki sorunlardan birini gösterir:</span><span class="sxs-lookup"><span data-stu-id="b4501-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="b4501-106">Okunabilirlik: gereksiz yere okunabilirlik sağlayan kod.</span><span class="sxs-lookup"><span data-stu-id="b4501-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="b4501-107">Örneğin, [IDE0001](ide0001.md) bayrakları gereksiz tür adı nitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b4501-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="b4501-108">Bakım: yeniden düzenleme sonrasında kullanılmayan ve gereksiz bir şekilde korunmakta olan kod.</span><span class="sxs-lookup"><span data-stu-id="b4501-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="b4501-109">Örneğin, [IDE0051](ide0051.md) bayrakları kullanılmayan özel alanlar, özellikler, olaylar ve Yöntemler.</span><span class="sxs-lookup"><span data-stu-id="b4501-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="b4501-110">Performans: yan etkileri olmayan ve gereksiz performans yükünü sağlayan gereksiz hesaplama.</span><span class="sxs-lookup"><span data-stu-id="b4501-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="b4501-111">Örneğin, [IDE0059](ide0059.md) bayrakları kullanılmamış değer atamaları, bir değeri hesaplama ifadesinin yan etkileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="b4501-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="b4501-112">İşlevsellik: kodda, gerekli kodun gereksiz şekilde işlenmesi halinde Işlevsel sorun.</span><span class="sxs-lookup"><span data-stu-id="b4501-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="b4501-113">Örneğin, [IDE0060](ide0060.md) bayrakları, yöntemin yanlışlıkla bir giriş parametresini yoksaydığı kullanılmamış parametrelere işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b4501-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="b4501-114">Bu bölümdeki kurallar, aşağıdaki gereksiz kod kurallarını ele konusudur:</span><span class="sxs-lookup"><span data-stu-id="b4501-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="b4501-115">Basitleşme adı (IDE0001)</span><span class="sxs-lookup"><span data-stu-id="b4501-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="b4501-116">Üye erişimini basitleştirme (IDE0002)</span><span class="sxs-lookup"><span data-stu-id="b4501-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="b4501-117">Gereksiz tür dönüştürmeyi Kaldır (IDE0004)</span><span class="sxs-lookup"><span data-stu-id="b4501-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="b4501-118">Gereksiz içeri aktarmayı Kaldır (IDE0005)</span><span class="sxs-lookup"><span data-stu-id="b4501-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="b4501-119">Erişilemeyen kodu Kaldır (IDE0035)</span><span class="sxs-lookup"><span data-stu-id="b4501-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="b4501-120">Kullanılmayan özel üyeyi Kaldır (IDE0051)</span><span class="sxs-lookup"><span data-stu-id="b4501-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="b4501-121">Okunmamış özel üyeyi Kaldır (IDE0052)</span><span class="sxs-lookup"><span data-stu-id="b4501-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="b4501-122">Kullanılmayan ifade değerini Kaldır (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="b4501-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="b4501-123">Gereksiz değer atamasını Kaldır (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="b4501-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="b4501-124">Kullanılmayan parametreyi Kaldır (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="b4501-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="b4501-125">Gereksiz gizleme Kaldır (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="b4501-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="b4501-126">[Gereksiz gizleme Işlecini Kaldır (IDE0080)](ide0080.md) -yalnızca C#.</span><span class="sxs-lookup"><span data-stu-id="b4501-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="b4501-127">[' ByVal ' (IDE0081)](ide0081.md) -yalnızca Visual Basic kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b4501-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="b4501-128">Gereksiz eşitlik işlecini Kaldır (IDE0100)</span><span class="sxs-lookup"><span data-stu-id="b4501-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="b4501-129">[Gereksiz atmayı Kaldır (IDE0110)](ide0110.md) -yalnızca C#.</span><span class="sxs-lookup"><span data-stu-id="b4501-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>

<span data-ttu-id="b4501-130">Bu kurallardan bazılarının kural davranışını yapılandırma seçenekleri vardır:</span><span class="sxs-lookup"><span data-stu-id="b4501-130">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="b4501-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="b4501-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="b4501-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="b4501-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="b4501-133">csharp_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="b4501-133">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="b4501-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="b4501-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="b4501-135">dotnet_code_quality_unused_parameters (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="b4501-135">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="b4501-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="b4501-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a><span data-ttu-id="b4501-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4501-137">See also</span></span>

- [<span data-ttu-id="b4501-138">Kod stili dil kuralları</span><span class="sxs-lookup"><span data-stu-id="b4501-138">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="b4501-139">Kod stili kuralları başvurusu</span><span class="sxs-lookup"><span data-stu-id="b4501-139">Code style rules reference</span></span>](index.md)
