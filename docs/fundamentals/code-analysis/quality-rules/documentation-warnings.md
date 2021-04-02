---
title: Belge kuralları (kod analizi)
description: Kod Analizi kuralı belge kuralları hakkında bilgi edinin
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588906"
---
# <a name="documentation-rules"></a><span data-ttu-id="2be4c-103">Belge kuralları</span><span class="sxs-lookup"><span data-stu-id="2be4c-103">Documentation rules</span></span>

<span data-ttu-id="2be4c-104">Belge kuralları, dışarıdan görülebilen API 'Ler için [XML belge açıklamalarının](../../../csharp/codedoc.md) doğru kullanımıyla birlikte iyi belgelenmiş kitaplıklar yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="2be4c-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2be4c-105">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="2be4c-105">In this section</span></span>

| <span data-ttu-id="2be4c-106">Kural</span><span class="sxs-lookup"><span data-stu-id="2be4c-106">Rule</span></span> | <span data-ttu-id="2be4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="2be4c-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="2be4c-108">CA1200: cref etiketlerini ön ek ile kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="2be4c-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="2be4c-109">XML belgesi etiketindeki [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) özniteliği "kod başvurusu" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2be4c-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="2be4c-110">Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2be4c-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="2be4c-111">`cref`Derleyicinin başvuruları doğrulamasını önlediği için ön ekleri olan etiketleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="2be4c-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="2be4c-112">Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler.</span><span class="sxs-lookup"><span data-stu-id="2be4c-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
