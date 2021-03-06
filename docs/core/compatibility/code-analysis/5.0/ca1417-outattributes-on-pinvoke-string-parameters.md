---
title: 'Son değişiklik: P/Invoke için dize parametresinde CA1417: OutAttribute'
description: Kod Analizi kuralı CA1417 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/29/2020
ms.openlocfilehash: 74aa6dc867bc1eb62e32dd086dd6b43f62e7f01f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257836"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a>Uyarı CA1417: P/Invoke için dize parametresindeki OutAttribute

.Net Code Analyzer Rule [CA1417](/visualstudio/code-quality/ca1417) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Bir parametrenin değere göre geçirildiği ve ile işaretlenen tüm [Platform çağırma (P/Invoke)](../../../../standard/native-interop/pinvoke.md) yöntemi tanımları için bir derleme uyarısı oluşturur <xref:System.String> <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA1417](/visualstudio/code-quality/ca1417)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

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
