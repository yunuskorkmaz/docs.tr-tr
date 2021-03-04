---
title: ASP.NET MVC ve ASP.NET Core Razor kullanımını karşılaştırın
description: ASP.NET MVC ve ASP.NET Core arasında Razor farklı midir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a9f7fa2e6b8c0c6bf61c743cf8c956b1ad09713c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105868"
---
# <a name="compare-razor-usage-in-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core Razor kullanımını karşılaştırın

Razor 'nin temel sözdizimi, ASP.NET MVC ve ASP.NET Core arasında önemli ölçüde değişmemiştir. Ancak, geçiş sırasında göz önünde bulundurmanız gereken [Etiket Yardımcıları](/aspnet/core/mvc/views/tag-helpers/intro) ve Razor Pages giriş gibi bazı farklılıklar vardır. Uygulamanız özel Razor işlevlerinin ağır kullanımını yapıyorsa, ASP.NET Core 'e geçiş yaparken hangi değişikliklerin gerekli olabileceğini görmek için [ASP.NET Core Razor söz dizimi başvurusuna](/aspnet/core/razor-pages) bakın.

## <a name="tag-helpers"></a>Etiket Yardımcıları

Etiket Yardımcıları, Razor dosyalarında HTML öğelerinin oluşturulmasına ve işlenmesine sunucu tarafı kodun katılmasını etkinleştir. Bunlar HTML yardımcılarına göre birçok avantaj sunar ve mümkün olan yerlerde HTML yardımcılarının yerine kullanılmalıdır. Bunlar standart HTML gibi göründiklerinden ve HTML düzenlemek için tasarlanan çoğu araç tarafından yoksayıldığından, HTML kullanımı kolay bir geliştirme deneyimi sağlar. _Visual Studio_'Da, etiket YARDıMCıLARı ile HTML ve Razor biçimlendirmesi oluşturmaya yönelik zengin IntelliSense desteği vardır. Etiket Yardımcıları, Razor dosyalarındaki bildirime dayalı biçimlendirmeden basit veya karmaşık davranış sağlayabilir.

## <a name="razor-pages"></a>Razor Pages

Razor Pages, sayfa ve form tabanlı uygulamalara yönelik denetleyiciler, Eylemler ve görünümlere bir alternatif sunar. [Razor Pages, bu bölümde daha önce ASP.NET MVC ile karşılaştırıldı](./comparing-razor-pages-aspnet-mvc.md).

## <a name="references"></a>Başvurular

- [ASP.NET MVC 'den ASP.NET Core MVC: denetleyiciler ve görünümler 'e geçiş](/aspnet/core/migration/mvc#migrate-controllers-and-views)
- [ASP.NET Core etiket yardımcıları](/aspnet/core/mvc/views/tag-helpers/intro)
- [ASP.NET Core Razor Pages giriş](/aspnet/core/razor-pages)
- [ASP.NET Core için Razor söz dizimi başvurusu](/aspnet/core/razor-pages)

>[!div class="step-by-step"]
>[Önceki](controller-differences.md) 
> [Sonraki](signalr-differences.md)
