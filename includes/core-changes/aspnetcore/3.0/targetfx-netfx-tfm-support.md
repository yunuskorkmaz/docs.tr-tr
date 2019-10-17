---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394485"
---
### <a name="target-framework-net-framework-support-dropped"></a>Hedef Framework: .NET Framework desteği bırakıldı

ASP.NET Core 3,0 ' den başlayarak, .NET Framework desteklenmeyen bir hedef çerçevedir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework 4,8, .NET Framework son ana sürümüdür. Yeni ASP.NET Core uygulamalar .NET Core üzerinde oluşturulmalıdır. .NET Core 3,0 sürümünden itibaren, .NET Core 'un parçası olarak ASP.NET Core 3,0 ' yi düşünebilirsiniz.

.NET Framework ASP.NET Core kullanan müşteriler, [2,1 LTS sürümünü](https://www.microsoft.com/net/download/dotnet-core/2.1)kullanarak tam olarak desteklenen bir biçimde devam edebilir. 2,1 için destek ve bakım, en az 21 Ağustos 2021 tarihine kadar devam eder. Bu tarih, [.net destek ilkesi](https://www.microsoft.com/net/platform/support-policy)başına LTS sürümünün bildiriminden sonraki üç yıldır. **.NET Framework üzerinde** ASP.NET Core 2,1 paketleri için destek, [diğer paket tabanlı ASP.net çerçeveleri için bakım ilkesine](https://dotnet.microsoft.com/platform/support/policy/aspnet)benzer şekilde süresiz olarak genişletilir.

.NET Framework .NET Core 'a taşıma hakkında daha fazla bilgi için bkz. [.NET Core 'A taşıma](~/docs/core/porting/index.md).

`Microsoft.Extensions` paket (günlüğe kaydetme, bağımlılık ekleme ve yapılandırma gibi) ve Entity Framework Core etkilenmemektedir. .NET Standard desteklemeye devam eder.

Bu değişiklik için mosyon hakkında daha fazla bilgi için, [özgün blog gönderisine](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0)bakın.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core uygulamalar .NET Core veya .NET Framework üzerinde çalışabilir.

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core uygulamalar yalnızca .NET Core üzerinde çalıştırılabilir.

#### <a name="recommended-action"></a>Önerilen eylem

Aşağıdaki eylemlerden birini yapın:

- Uygulamanızı ASP.NET Core 2,1 ' de saklayın.
- Uygulamanızı ve bağımlılıklarınızı .NET Core 'a geçirin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
