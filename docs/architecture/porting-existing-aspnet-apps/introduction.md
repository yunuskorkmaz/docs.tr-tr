---
title: .NET Core 'a uygulama taşıma konusuna giriş
description: Bu bölümde, var olan ASP.NET uygulamalarını .NET Core 'a geçirmeyi göz önünde bulundurarak takımlar için dikkat edilmesi gerekenler listelenmiştir.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a346d1c693389cc4ca682b41a3b7fc094cfa5482
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488883"
---
# <a name="introduction-to-porting-apps-to-net-core"></a>.NET Core 'a uygulama taşıma konusuna giriş

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Core, .NET Framework 'den ileri doğru bir adımdır. Bu BT, yerleşik platformlar arası destek sayesinde geliştirici memnuniyeti sunan Pano genelinde .NET Framework bir avantaj sunar. ASP.NET Core, [2020 Stack Overflow geliştirici anketine](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks), en çok kullanılan Web çerçevesini de oyladı. Geçişi göz önünde bulundurmanız gereken güçlü nedenler vardır.

.Net [Core 'un, .net 'In geleceği](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)göz önünde bulundurmanız önemlidir. Bu makaleyi tırnak içine almak için:

> Yeni uygulamalar .NET Core üzerinde oluşturulmalıdır. .NET Core, .NET 'teki gelecek yatırımların gerçekleşecektir. Mevcut uygulamalar, desteklenecek .NET Framework devam etmek için güvenlidir. .NET ' teki yeni özelliklerden yararlanmak isteyen mevcut uygulamalar .NET Core 'a geçmeyi düşünmelidir. Gelecekte de planlıyoruz, platforma daha da fazla özellik getirilecektir.

Ancak, uygulamanızı ASP.NET Core için yükseltmek biraz çaba gerektirir. Bu çaba, iş değeri ve hedeflere karşı dengeedilmelidir. .NET Framework uygulamalar, daha önce, öngörülebilir bir şekilde Windows 'da yerleşik olarak bulunan destek sayesinde bu uygulamaların önünde daha fazla zaman yaşamasını sağlıyor. .NET Core 'a geçiş konusunda karar vermeden önce göz önünde bulundurmanız gereken sorulardan bazıları uygun midir? Beklenen avantajlar nelerdir? Dengeler nelerdir? Ne kadar çaba söz konusu? Bu açık sorular yalnızca başlangıcıdır, ancak ekipler müşterilerin ihtiyaçlarını bugün ve yarın uygulamalarla desteklemeyi düşündüen harika bir başlangıç noktası oluşturun.

- .NET Core 'a doğru geçiş yapılsın mı?
- Ne zaman .NET Framework kalmak mantıklı midir?
- Uygulamalar ASP.NET Core 2,1 ' i bir atlama pulu olarak hedeflemelidir mi?
- Takımlar hedeflemek için doğru .NET Core sürümünü nasıl seçer?
- Büyük uygulamaların artımlı geçişi için hangi stratejiler önerilir?
- .NET Core 'a taşıma sırasında hangi dağıtım stratejileri göz önünde bulundurulmalıdır?
- Ek kaynakları nerede bulabilirim?

Bu giriş bölümü, gelecekteki bölümlerde daha belirgin ve teknik noktalara geçmeden önce tüm bu soruların ve daha fazlasını ele alır.

## <a name="references"></a>Başvurular

- [2020 Stack Overflow geliştirici Anketi en iyi Web çerçeveleri](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks)
- [.NET Core, .NET 'in geleceği](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](migration-considerations.md)
