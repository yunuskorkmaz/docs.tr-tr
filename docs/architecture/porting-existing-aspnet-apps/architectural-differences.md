---
title: ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar
description: ASP.NET ve ASP.NET Core arasındaki mimari farklılıkları inceleyin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 96477f2393482380eee9891e9b2dbbb6445e15bd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106153"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Framework ve ASP.NET Core üzerinde ASP.NET MVC arasında birçok mimari fark vardır. Takımlar, ASP.NET MVC uygulamalarını ASP.NET Core 'e taşıma konusunda yer alan işi değerlendirirken, bu farklılıkları büyük bir şekilde kavramak önemlidir. Bu bölümde, ASP.NET Core ASP.NET MVC 'den önemli ölçüde farklı olan her bir yol görünür.

## <a name="breaking-changes"></a>Yeni değişiklikler

.NET Core, .NET Framework platformlar arası yeniden yazma işlemi. [İki çerçeve arasında çok sayıda Son değişiklik](../../core/compatibility/fx-core.md)vardır. Aşağıdaki bölümler, ASP.NET MVC ve ASP.NET Core uygulamalarının nasıl tasarlandığına ve geliştirildiğiyle ilgili belirli farklılıkları belirler. Ayrıca, hangi çerçeve kitaplıklarının değişiklik yapması gerektiğini belirleyen belgeleri incelemek için de dikkatli olmanız gerekir. Birçok durumda, bir değiştirme NuGet paketi .NET Framework ve .NET Core arasında kalan boşlukları dolduracak şekilde bulunur. Nadir durumlarda, uyumsuzlukları karşılamak için bir üçüncü taraf çözümü bulmanız veya yeni özel kod uygulamanız gerekebilir.

>[!div class="step-by-step"]
>[Önceki](additional-migration-resources.md) 
> [Sonraki](app-startup-differences.md)
