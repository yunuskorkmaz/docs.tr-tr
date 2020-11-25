---
title: 'Son değişiklik: varsayılan Activityıdformat W3C'
description: Varsayılan Activityıdformat artık W3C olan çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 77ee705ac18065c84ddeab3127e01b6a40c3b84d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761561"
---
# <a name="default-activityidformat-is-w3c"></a>Varsayılan Activityıdformat W3C

Activity () için varsayılan tanımlayıcı biçimi <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> artık <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

## <a name="change-description"></a>Açıklamayı Değiştir

W3C etkinlik KIMLIĞI biçimi, hiyerarşik KIMLIK biçimine alternatif olarak .NET Core 3,0 ' de tanıtılmıştır. Ancak, uyumluluğu korumak için, W3C biçimi .NET 5,0 ' e kadar varsayılan olarak yapılmamıştır. Varsayılan değer .NET 5,0 ' de değiştirilmiştir, çünkü [W3C biçimi](https://www.w3.org/TR/trace-context/) , birden çok dil uygulamasında daha fazla şekilde kazanılabilir.

Uygulamanız .NET 5,0 veya sonraki bir sürümü dışında bir platformu hedefliyorsa, bu, varsayılan biçim olan eski davranışla karşılaşacaktır <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> . Bu varsayılan, net45 +, Netstandard 1.1 + ve netcoreapp (1. x, 2. x ve 3. x) platformları için geçerlidir. .NET 5,0 ve üzeri sürümlerde, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> olarak ayarlanır <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .

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
