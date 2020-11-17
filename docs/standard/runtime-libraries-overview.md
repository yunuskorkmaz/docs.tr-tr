---
title: Çalışma zamanı kitaplıklarına genel bakış
description: İçindekiler tablosunun çalışma zamanı kitaplıkları bölümüne nelerin ekleneceğini öğrenin.
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687896"
---
# <a name="runtime-libraries-overview"></a>Çalışma zamanı kitaplıklarına genel bakış

[Framework 'e bağımlı uygulamalar](../core/introduction.md#deployment-models)tarafından kullanılmak üzere bir makineye yüklenen [.NET çalışma zamanı](../core/introduction.md#sdk-and-runtimes), [çalışma zamanı kitaplıkları](glossary.md#runtime), [çerçeve kitaplıkları](glossary.md#framework-libraries)veya [temel sınıf kitaplığı (BCL)](glossary.md#bcl)olarak bilinen, expante standart bir sınıf kitaplıkları kümesine sahiptir. Ayrıca, NuGet paketlerinde belirtilen çalışma zamanı kitaplıklarının uzantıları vardır.

Bu kitaplıklar birçok genel ve uygulamaya özel türler, algoritmalar ve yardımcı program işlevselliğine yönelik uygulamalar sağlar.

## <a name="runtime-libraries"></a>Çalışma zamanı kitaplıkları

Bu kitaplıklar temel türler ve yardımcı işlevler sağlar ve diğer tüm .NET sınıf kitaplıklarının tabtemeldir. Bir örnek <xref:System.String?displayProperty=nameWithType> , dizeler ile çalışmaya yönelik API 'ler sağlayan sınıftır. [Serileştirme kitaplıkları](serialization/index.md)başka bir örnektir.

## <a name="extensions-to-the-runtime-libraries"></a>Çalışma zamanı kitaplıklarının uzantıları

Bazı kitaplıklar, çalışma zamanının [paylaşılan çerçevesine](glossary.md#shared-framework)dahil olmak yerine NuGet paketlerinde sunulmaktadır. Örnek:

* [Günlüğe kaydetme](../core/extensions/logging.md)
* [Bağımlılık ekleme](../core/extensions/dependency-injection.md)
* [Yapılandırma](../core/extensions/configuration.md)

## <a name="see-also"></a>Ayrıca bkz.

* [.NET’e giriş](../core/introduction.md)
* [.NET SDK veya çalışma zamanı yüklemesi](../core/install/index.yml)
* [Kullanılacak yüklü .NET SDK 'sını veya çalışma zamanı sürümünü seçin](../core/versions/selection.md)
* [Çerçeveye bağımlı uygulamalar yayımlama](../core/deploying/index.md#publish-framework-dependent)
