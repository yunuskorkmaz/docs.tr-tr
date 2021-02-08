---
title: Kod analizi kural kategorileri
description: Farklı .NET kod analizi kural kategorilerini öğrenin.
ms.date: 02/05/2021
ms.topic: reference
helpviewer_keywords:
- code analysis, categories
ms.openlocfilehash: 3eaff57a7ea175fbe0895fb7bb8d8d0d8df1365d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804182"
---
# <a name="rule-categories"></a>Kural kategorileri

Her kod analizi kuralı bir kural kategorisine aittir. Örneğin, tasarım kuralları .NET tasarım yönergelerine uygunluğunu destekler ve güvenlik kuralları güvenlik kusurlarını önlemeye yardımcı olur. Kural [kategorisini tümüyle etkinleştirebilir veya devre dışı](configuration-options.md#scope) bırakabilirsiniz. Ayrıca, kategori başına [ek seçenekleri de yapılandırabilirsiniz](code-quality-rule-options.md#category-of-rules) .

Aşağıdaki tabloda farklı kod analizi kuralı kategorileri gösterilmektedir ve her kategorideki kurallara bir bağlantı sağlanır.

| Kategori | Açıklama |
| - | - |
| [Tasarım kuralları](quality-rules/design-warnings.md) | Tasarım kuralları [.NET Framework Tasarım yönergelerine](../../standard/design-guidelines/index.md)uygunluğunu destekler. |
| [Belge kuralları](quality-rules/documentation-warnings.md) | Belge kuralları, dışarıdan görülebilen API 'Ler için XML belge açıklamalarının doğru kullanımıyla birlikte iyi belgelenmiş kitaplıklar yazmayı destekler. |
| [Genelleştirme kuralları](quality-rules/globalization-warnings.md) | Genelleştirme kuralları, dünyaya yönelik kitaplıkları ve uygulamaları destekler. |
| [Taşınabilirlik ve birlikte çalışabilirlik kuralları](quality-rules/interoperability-warnings.md) | Taşınabilirlik kuralları farklı platformlarda taşınabilirliği destekler. Birlikte çalışabilirlik kuralları COM istemcileriyle etkileşimi destekler. |
| [Bakım kuralları](quality-rules/maintainability-warnings.md) | Bakımlama kuralları kitaplığı ve uygulama bakımını destekler. |
| [Adlandırma kuralları](quality-rules/naming-warnings.md) | Adlandırma kuralları, .NET Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekler. |
| [Performans kuralları](quality-rules/performance-warnings.md) | Performans kuralları yüksek performanslı kitaplıkları ve uygulamaları destekler. |
| [Yayımlama kuralları](quality-rules/publish-warnings.md) | Yayımlama kuralları tek dosya uygulamalarını destekler. |
| [Güvenilirlik kuralları](quality-rules/reliability-warnings.md) | Güvenilirlik kuralları, doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekler. |
| [Güvenlik kuralları](quality-rules/security-warnings.md) | Güvenlik kuralları, daha güvenli kitaplıkları ve uygulamaları destekler. Bu kurallar, programınızdaki güvenlik kusurları önlemeye yardımcı olur. |
| [Stil kuralları](style-rules/index.md) | Stil kuralları kod tabanınızda tutarlı kod stilini destekler. Bu kurallar "IDE" önekiyle başlar. |
| [Kullanım kuralları](quality-rules/usage-warnings.md) | Kullanım kuralları, .NET 'in uygun kullanımını destekler. |
