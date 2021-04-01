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
# <a name="documentation-rules"></a>Belge kuralları

Belge kuralları, dışarıdan görülebilen API 'Ler için [XML belge açıklamalarının](../../../csharp/codedoc.md) doğru kullanımıyla birlikte iyi belgelenmiş kitaplıklar yazmayı destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Description |
| - | - |
| [CA1200: cref etiketlerini ön ek ile kullanmaktan kaçının](ca1200.md) | XML belgesi etiketindeki [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. `cref`Derleyicinin başvuruları doğrulamasını önlediği için ön ekleri olan etiketleri kullanmaktan kaçının. Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler. |
