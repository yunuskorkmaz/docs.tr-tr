---
title: 'Son değişiklik: varsayılan Activityıdformat W3C'
description: Varsayılan Activityıdformat artık W3C olan çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: f15c2d61443117cfbcb2be7de9561fecbff9a1d9
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257511"
---
# <a name="default-activityidformat-is-w3c"></a>Varsayılan ActivityIdFormat W3C

Activity () için varsayılan tanımlayıcı biçimi <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> artık <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

## <a name="change-description"></a>Açıklamayı Değiştir

W3C etkinlik KIMLIĞI biçimi, hiyerarşik KIMLIK biçimine alternatif olarak .NET Core 3,0 ' de tanıtılmıştır. Ancak, uyumluluğu korumak için, W3C biçimi .NET 5,0 ' e kadar varsayılan olarak yapılmamıştır. Varsayılan değer .NET 5 ' te değiştirilmiştir, çünkü [W3C biçimi](https://www.w3.org/TR/trace-context/) , birden çok dil uygulamasında daha fazla şekilde kazanılabilir.

Uygulamanız .NET 5 veya sonraki bir sürümünü hedefliyorsa, bu, varsayılan biçim olan eski davranışla karşılaşacaktır <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> . Bu varsayılan, net45 +, Netstandard 1.1 + ve netcoreapp (1. x, 2. x ve 3. x) platformları için geçerlidir. .NET 5 ve sonraki sürümlerde, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> olarak ayarlanır <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Uygulamanız dağıtılmış izleme için kullanılan tanımlayıcıya belirsiz ise, herhangi bir eylemde bulunmanız gerekmez. ASP.NET Core gibi kitaplıklar <xref:System.Net.Http.HttpClient> , her iki sürümünü kullanabilir veya yayabilir <xref:System.Diagnostics.ActivityIdFormat> .

Mevcut sistemlerle birlikte çalışabilirliğe gerek duyuyorsanız veya geçerli sistemler tanımlayıcı biçimine güvenuygunsa, ' i ' ye ayarlayarak eski davranışı koruyabilirsiniz <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> . Alternatif olarak, bir AppContext anahtarını üç farklı şekilde ayarlayabilirsiniz:

- , Proje dosyasında.

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- Dosyasında *runtimeconfig.js* .

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- Bir ortam değişkeni aracılığıyla.

  `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` `true` Veya 1 olarak ayarlayın.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
