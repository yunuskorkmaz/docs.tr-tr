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
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "96589869"
---
# <a name="unnecessary-code-rules"></a>Gereksiz kod kuralları

Gereksiz kod kuralları, kod tabanının gereksiz ve yeniden düzenlenmiş veya kaldırılabilir olan farklı parçalarını belirler. Gereksiz kodun varlığı aşağıdaki sorunlardan birini gösterir:

- Okunabilirlik: gereksiz yere okunabilirlik sağlayan kod. Örneğin, [IDE0001](ide0001.md) bayrakları gereksiz tür adı nitelikleri.
- Bakım: yeniden düzenleme sonrasında kullanılmayan ve gereksiz bir şekilde korunmakta olan kod. Örneğin, [IDE0051](ide0051.md) bayrakları kullanılmayan özel alanlar, özellikler, olaylar ve Yöntemler.
- Performans: yan etkileri olmayan ve gereksiz performans yükünü sağlayan gereksiz hesaplama. Örneğin, [IDE0059](ide0059.md) bayrakları kullanılmamış değer atamaları, bir değeri hesaplama ifadesinin yan etkileri yoktur.
- İşlevsellik: kodda, gerekli kodun gereksiz şekilde işlenmesi halinde Işlevsel sorun. Örneğin, [IDE0060](ide0060.md) bayrakları, yöntemin yanlışlıkla bir giriş parametresini yoksaydığı kullanılmamış parametrelere işaret eder.

Bu bölümdeki kurallar, aşağıdaki gereksiz kod kurallarını ele konusudur:

- [Basitleşme adı (IDE0001)](ide0001.md)
- [Üye erişimini basitleştirme (IDE0002)](ide0002.md)
- [Gereksiz tür dönüştürmeyi Kaldır (IDE0004)](ide0004.md)
- [Gereksiz içeri aktarmayı Kaldır (IDE0005)](ide0005.md)
- [Erişilemeyen kodu Kaldır (IDE0035)](ide0035.md)
- [Kullanılmayan özel üyeyi Kaldır (IDE0051)](ide0051.md)
- [Okunmamış özel üyeyi Kaldır (IDE0052)](ide0052.md)
- [Kullanılmayan ifade değerini Kaldır (IDE0058)](ide0058.md)
- [Gereksiz değer atamasını Kaldır (IDE0059)](ide0059.md)
- [Kullanılmayan parametreyi Kaldır (IDE0060)](ide0060.md)
- [Gereksiz gizleme Kaldır (IDE0079)](ide0079.md)
- [Gereksiz gizleme Işlecini Kaldır (IDE0080)](ide0080.md) -yalnızca C#.
- [' ByVal ' (IDE0081)](ide0081.md) -yalnızca Visual Basic kaldırın.
- [Gereksiz eşitlik işlecini Kaldır (IDE0100)](ide0100.md)
- [Gereksiz atmayı Kaldır (IDE0110)](ide0110.md) -yalnızca C#.

Bu kurallardan bazılarının kural davranışını yapılandırma seçenekleri vardır:

- [csharp_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [visual_basic_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [csharp_style_unused_value_assignment_preference (IDE0059)](ide0059.md#csharp_style_unused_value_assignment_preference)
- [visual_basic_style_unused_value_assignment_preference (IDE0059)](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [dotnet_code_quality_unused_parameters (IDE0060)](ide0060.md#dotnet_code_quality_unused_parameters)
- [dotnet_remove_unnecessary_suppression_exclusions (IDE0079)](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod stili dil kuralları](language-rules.md)
- [Kod stili kuralları başvurusu](index.md)
