---
title: .NET Core yüklemeleri yönetme
description: Birden çok .NET Core SDK ve çalışma zamanı sürümleri ile yan yana yükleme stratejileri çalışma makinenizde yönetin.
author: leecow
ms.author: wiwagn
ms.date: 08/22/2018
ms.openlocfilehash: 06c3f43e7917efb8fd31898044d8f5d920c2cada
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485482"
---
# <a name="manage-net-core-installations"></a>.NET Core yüklemeleri yönetme

.NET core, hem oluşturma hem de .NET Core uygulamaları çalıştırmak için sürüm bağımlılık esneklik etkinleştirilmesi, yan yana birden çok sürümünü mevcut çalışma zamanını ve SDK sağlar. Bu yükleme ve otomatik sürüm sarma davranışları okunur eksisi ancak önemli avantajları sunar. .NET Core çalışma zamanı ve .NET Core SDK'sı güncelleştirme yüklü olarak, önceki sürümler disk üzerinde kalır. Birden çok yüklü sürümlerini zamanla disk kullanımını artırın. 50'den fazla .NET Core SDK'sı güncelleştirme yayımladık. SDK ve çalışma zamanı kaldırılamadı, sisteminizde yüklü'nın birçok sürümü olabilir.

## <a name="safe-to-remove"></a>Kaldırmak için güvenli mi?

[.NET Core sürüm seçimi](selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğunu güncelleştirmeleri arasında önceki sürümlerini güvenli kaldırılmasını sağlar. .NET core çalışma zamanı güncelleştirmeleri, bir ana sürüm 1.x ve 2.x'i gibi ' bant' içinde uyumludur. Ayrıca, .NET Core SDK'sının daha yeni sürümleri, genellikle, çalışma zamanı, hedef önceki sürümleri uyumlu bir şekilde uygulamalar oluşturmanızı yapılandırabilmeyi sürdürmeniz.

Genel olarak, yalnızca en son SDK'sı ve uygulamanız için gereken çalışma zamanları en son düzeltme eki sürümü gerekir. Örnekleri burada project.json tabanlı uygulamaları sürdürmek tutulan daha eski SDK veya çalışma zamanı sürümleri içerir.  Uygulamanızı önceki bir SDK'ları veya çalışma zamanları belirli nedenlerle olmadığı sürece, eski sürümleri güvenli bir şekilde kaldırabilirsiniz.

.NET Core kaldırma yöntemleri platformdan platforma değişir ve .NET Core sürümleri arasında biraz değişti. Artık gerekli .NET Core sürümleri kaldırma hakkında daha fazla bilgi için bkz ['SDK ve .NET Core çalışma zamanı'nı kaldırmak nasıl'](remove-runtime-sdk-versions.md) içinde [.NET Core belgeleri](../index.md).
