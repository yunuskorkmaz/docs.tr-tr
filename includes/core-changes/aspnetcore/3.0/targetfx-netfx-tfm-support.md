---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549604"
---
### <a name="target-framework-net-framework-support-dropped"></a>Hedef çerçeve: .NET Framework desteği düştü

ASP.NET Core 3.0 ile başlayan .NET Framework desteklenmeyen bir hedef çerçevesidir.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework 4.8 ,.NET Framework'ün son ana sürümüdür. Yeni ASP.NET Core uygulamaları .NET Core üzerine kurulmalıdır. .NET Core 3.0 sürümünden başlayarak, ASP.NET Core 3.0'ı .NET Core'un bir parçası olarak düşünebilirsiniz.

.NET Framework ile ASP.NET Core kullanan müşteriler [2.1 LTS sürümü](https://dotnet.microsoft.com/download/dotnet-core/2.1)kullanarak tam destekli bir şekilde devam edebilirsiniz. 2.1 için destek ve hizmet en az 21 Ağustos 2021 tarihine kadar devam etmektedir. Bu tarih, [.NET Destek İlkesi](https://dotnet.microsoft.com/platform/support-policy)uyarınca LTS sürümünin beyanı tarihinden üç yıl sonradır. **.NET Framework'deki** ASP.NET Core 2.1 paketlerinin desteği, [diğer paket tabanlı ASP.NET çerçeveleri için servis politikasına](https://dotnet.microsoft.com/platform/support/policy/aspnet)benzer şekilde süresiz olarak uzayacaktır.

.NET Framework'den .NET Core'a taşıma hakkında daha fazla bilgi [için](~/docs/core/porting/index.md)bkz.

`Microsoft.Extensions`paketleri (günlük, bağımlılık enjeksiyonu ve yapılandırma gibi) ve Entity Framework Core etkilenmez. .NET Standard'ı desteklemeye devam edeceklerdir.

Bu değişikliğin motivasyonu hakkında daha fazla bilgi için [orijinal blog gönderisi](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core uygulamaları .NET Core veya .NET Framework üzerinde çalıştırılabilir.

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core uygulamaları yalnızca .NET Core'da çalıştırılabilir.

#### <a name="recommended-action"></a>Önerilen eylem

Aşağıdaki eylemlerden birini uygulayın:

- Uygulamanızı Core 2.1ASP.NET de tutun.
- Uygulamanızı ve bağımlılıklarınızı .NET Core'a geçirin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
