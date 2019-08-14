---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974128"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core 'da hangi tanılama araçları kullanılabilir?

Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.

Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.

## <a name="managed-debuggersmanaged-debuggersmd"></a>[Yönetilen hata ayıklayıcıları](managed-debuggers.md)
Yönetilen hata defterleri, programla etkileşime girebilmeniz için izin verir. Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir. Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.

## <a name="logging-and-tracinglogging-tracingmd"></a>[Günlüğe kaydetme ve izleme](logging-tracing.md)
Günlüğe kaydetme ve izleme ilgili teknikler. Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar. Dosyalar, bir programın yaptığı ayrıntıları kaydeder. Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir. Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.

## <a name="unit-testingtestingindexmd"></a>[Birim testi](../testing/index.md)
Birim testi, yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir. Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.
