---
title: Çalışma zamanı kitaplıklarına genel bakış
description: İçindekiler tablosunun çalışma zamanı kitaplıkları bölümüne nelerin ekleneceğini öğrenin.
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507613"
---
# <a name="runtime-libraries-overview"></a>Çalışma zamanı kitaplıklarına genel bakış

[Çerçeveye bağımlı uygulamalar](../core/introduction.md#deployment-models)tarafından kullanılmak üzere bir makinede yüklü olan [.NET çalışma zamanına](../core/introduction.md#sdk-and-runtimes), expante standart bir sınıf kitaplıkları kümesi vardır:

* Çalışma zamanına dahil olan ve [temel sınıf kitaplıkları (BCL)](glossary.md#bcl)olarak bilinen çekirdek küme.
* Çalışma zamanına dahil olan ve [çalışma zamanı kitaplıkları](glossary.md#runtime) veya [Framework kitaplıkları](glossary.md#framework)olarak bilinen tüm küme.
* NuGet paketlerinde belirtilen çalışma zamanı kitaplıklarının uzantıları.

Bu kitaplıklar birçok genel ve uygulamaya özel türler, algoritmalar ve yardımcı program işlevselliğine yönelik uygulamalar sağlar.

## <a name="base-class-libraries"></a>Temel sınıf kitaplıkları

BCL temel türler ve yardımcı işlevler sağlar ve diğer tüm .NET sınıf kitaplıklarının temelini içerir. Bir örnek <xref:System.String?displayProperty=nameWithType> , dizeler ile çalışmaya yönelik API 'ler sağlayan sınıftır.

## <a name="runtime-libraries"></a>Çalışma zamanı kitaplıkları

Çerçeve kitaplıkları olarak da bilinen çalışma zamanı kitaplıkları, ortak görevler için yardımcı API 'Leri sağlamak üzere BCL üzerinde oluşturur. [Serileştirme kitaplıkları](serialization/index.md)bir örnektir.

## <a name="extensions-to-the-runtime-libraries"></a>Çalışma zamanı kitaplıklarının uzantıları

Çalışma zamanı kitaplıklarının bazıları, çerçeveye bağımlı uygulamalar için yüklenen çalışma zamanına yerleşik olmak yerine NuGet paketlerinde sunulmaktadır. [.Net günlüğü API 'sine](../core/extensions/logging.md)örnek bir örnektir.

## <a name="see-also"></a>Ayrıca bkz.

* [.NET’e giriş](../core/introduction.md)
* [.NET SDK veya çalışma zamanı yüklemesi](../core/install/index.yml)
* [Kullanılacak yüklü .NET SDK 'sını veya çalışma zamanı sürümünü seçin](../core/versions/selection.md)
* [Çerçeveye bağımlı uygulamalar yayımlama](../core/deploying/index.md#publish-framework-dependent)
