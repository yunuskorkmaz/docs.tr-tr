---
title: 'Son değişiklik: P/Invoke için dize parametresinde CA1417: OutAttribute'
description: Kod Analizi kuralı CA1417 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/29/2020
ms.openlocfilehash: 3316d07108ec7f9da985494413336cba6d560dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761337"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a>Uyarı CA1417: P/Invoke için dize parametresindeki OutAttribute

.Net Code Analyzer Rule [CA1417](/visualstudio/code-quality/ca1417) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Bir parametrenin değere göre geçirildiği ve ile işaretlenen tüm [Platform çağırma (P/Invoke)](../../../../standard/native-interop/pinvoke.md) yöntemi tanımları için bir derleme uyarısı oluşturur <xref:System.String> <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA1417](/visualstudio/code-quality/ca1417)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Rule CA1417 bayrakları [P/](../../../../standard/native-interop/pinvoke.md) bir <xref:System.String> parametrenin öznitelik ile işaretlendiği <xref:System.Runtime.InteropServices.OutAttribute> ve değer Ile geçirildiği yöntem tanımlarını çağırır. Örnek:

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

.NET çalışma zamanı, bir programdaki her benzersiz sabit değer dizesine tek bir başvuru içeren Intern havuzu adlı bir tablo tutar. İle işaretlenmiş bir dize, <xref:System.Runtime.InteropServices.OutAttribute> bir P/Invoke yöntemine değer ile geçirildiyse, çalışma zamanı kararsız hale gelebilirler. Dize oluşturma hakkında daha fazla bilgi için, bkz <xref:System.String.Intern(System.String)?displayProperty=nameWithType> . açıklamalar.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Değiştirilen dize verilerini çağırana geri almanız gerekiyorsa, dizeyi başvuruya göre geçirin.

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- Değiştirilen dize verilerini çağırana geri sıralayamaz, öğesini kaldırmanız yeterlidir <xref:System.Runtime.InteropServices.OutAttribute> .

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  Daha fazla bilgi için bkz. [CA1417](/visualstudio/code-quality/ca1417).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
