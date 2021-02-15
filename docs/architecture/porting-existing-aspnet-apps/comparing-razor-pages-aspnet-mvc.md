---
title: Razor Pages ASP.NET MVC ile karşılaştırın
description: Razor Pages, sayfa tabanlı uygulamalar için geleneksel MVC görünümlerinden sorumlulukları düzenlemenin daha iyi bir yolunu sunar. Bu bölümde geleneksel ASP.NET MVC yaklaşımını nasıl karşılaştırılacağını öğrenin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3a113cea52c32b436d357f64d26eb31c722349ee
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488921"
---
# <a name="compare-razor-pages-to-aspnet-mvc"></a>Razor Pages ASP.NET MVC ile karşılaştırın

Razor Pages, ASP.NET Core sayfa veya form tabanlı uygulamalar oluşturmanın tercih edilen yoludur. [Docs](https://docs.microsoft.com/aspnet/core/razor-pages/), "Razor Pages, kodlama sayfasına odaklanmış senaryolar denetleyicileri ve görünümleri kullanmaktan daha kolay ve daha üretken olabilir." ASP.NET MVC uygulamanız görünümlerin yoğun kullanımını yapıyorsa, eylemlerden ve görünümlerden Razor Pages geçiş yapmayı düşünmek isteyebilirsiniz.

Kesin olarak belirlenmiş bir görünüm tabanlı MVC uygulaması, bir veya daha fazla eylem içermesi için bir denetleyici kullanır. Denetleyici, etki alanı veya veri modeliyle etkileşime geçerek ViewModel sınıfının bir örneğini oluşturur. Bu ViewModel sınıfı, bu eylemle ilişkili görünüme geçirilir. Bu yaklaşım, MVC uygulamalarının varsayılan klasör yapısıyla birlikte kullanıldığında, bir uygulamaya yeni bir sayfa eklemek için bir klasörde denetleyicinin değiştirilmesini, başka bir klasördeki iç içe yerleştirilmiş alt klasörde bir görünümü ve başka bir klasörde ViewModel olmasını gerektirir.

Tek bir sınıfta eylem (şimdi bir *işleyici*) ve ViewModel ( *pagemodel* olarak adlandırılır) grubunu bir arada Razor Pages ve bu sınıfı görünüme (Razor sayfası denir) bağlayın. Tüm Razor Pages ASP.NET Core projesinin kökündeki bir *Sayfalar* klasörüne gider. Razor Pages, bu klasör içindeki ad ve konumlarına göre bir yönlendirme kuralı kullanın. İşleyiciler tam olarak eylem yöntemlerine benzer ancak kendi adında (örneğin,) işledikleri HTTP fiiline sahiptir `OnGet` . Bunlar, varsayılan olarak ilişkili oldukları sayfayı döndürecek şekilde kabul ettikleri için de gerekli değildir. Bu, bir uygulamanın belirli bir bölümünü eklemek veya değiştirmek için gereken tüm dosyaları bulmayı ve bunlarla çalışmayı kolaylaştıran, Razor Pages ve işleyicileri daha az ve daha fazla odaklanmış bir hale getirme eğilimi gösterir.

ASP.NET MVC 'den ASP.NET Core bir parçası olarak takımlar, denetleyicileri ve görünümleri ASP.NET Core denetleyicilerine ve görünümlere geçirmek isteyip istemediğinizi düşünmelidir veya Razor Pages. İlki büyük olasılıkla daha az genel çaba gerektirir, ancak ekibin geleneksel görünüm tabanlı dosya kuruluşu üzerinden Razor Pages avantajlarından yararlanmasını sağlar.

## <a name="references"></a>Başvurular

- [ASP.NET Core Razor Pages giriş](https://docs.microsoft.com/aspnet/core/razor-pages/)
- [Razor Pages ile daha basit ASP.NET Core uygulamalar](https://docs.microsoft.com/archive/msdn-magazine/2017/september/asp-net-core-simpler-asp-net-mvc-apps-with-razor-pages)

>[!div class="step-by-step"]
>[Önceki](routing-differences.md) 
> [Sonraki](webapi-differences.md)
