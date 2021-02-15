---
title: ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar
description: ASP.NET ve ASP.NET Core arasındaki mimari farklılıkları inceleyin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0e546465a3da6971a118c65114af81c3a387e00e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488926"
---
# <a name="architectural-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki mimari farklar

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Framework ve ASP.NET Core üzerinde ASP.NET MVC arasında birçok mimari fark vardır. Takımlar, ASP.NET MVC uygulamalarını ASP.NET Core 'e taşıma konusunda yer alan işi değerlendirirken, bu farklılıkları büyük bir şekilde kavramak önemlidir. Bu bölümde, ASP.NET Core ASP.NET MVC 'den önemli ölçüde farklı olan her bir yol görünür.

## <a name="breaking-changes"></a>Yeni değişiklikler

.NET Core, .NET Framework platformlar arası yeniden yazma işlemi. [İki çerçeve arasında çok sayıda Son değişiklik](https://docs.microsoft.com/dotnet/core/compatibility/fx-core)vardır. Aşağıdaki bölümler, ASP.NET MVC ve ASP.NET Core uygulamalarının nasıl tasarlandığına ve geliştirildiğiyle ilgili belirli farklılıkları belirler. Ayrıca, hangi çerçeve kitaplıklarının değişiklik yapması gerektiğini belirleyen belgeleri incelemek için de dikkatli olmanız gerekir. Birçok durumda, bir değiştirme NuGet paketi .NET Framework ve .NET Core arasında kalan boşlukları dolduracak şekilde bulunur. Nadir durumlarda, uyumsuzlukları karşılamak için bir üçüncü taraf çözümü bulmanız veya yeni özel kod uygulamanız gerekebilir.

>[!div class="step-by-step"]
>[Önceki](additional-migration-resources.md) 
> [Sonraki](app-startup-differences.md)
