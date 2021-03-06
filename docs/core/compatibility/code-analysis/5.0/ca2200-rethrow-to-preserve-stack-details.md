---
title: 'Son değişiklik: CA2200: yığın ayrıntılarını korumak için yeniden throw'
description: Kod Analizi kuralı CA2200 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 776a1bcf16c19364017e4652837720080fb7ba72
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257732"
---
# <a name="warning-ca2200-rethrow-to-preserve-stack-details"></a>Uyarı CA2200: yığın ayrıntılarını korumak için yeniden throw

.Net Code Analyzer Rule [CA2200](/visualstudio/code-quality/ca2200) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. Özel durum oluşturan herhangi bir blok için derleme uyarısı üretir `catch` ve özel durum `throw` deyimde açıkça belirtilir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2200](/visualstudio/code-quality/ca2200)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Kural CA2200 bayrakları, özel durumların yeniden oluşturulduğu ve özel durum değişkeninin bildiriminde belirtildiği durumdur `throw` . Bir özel durum oluştuğunda, içerdiği bilgilerin bir kısmı yığın izdir. Yığın izlemesi, özel durumu oluşturan yöntemiyle başlayan ve özel durumu yakalayan yöntemle biten Yöntem çağrısı hiyerarşisinin bir listesidir. Deyimdeki özel durum belirtilerek bir özel durum yeniden oluşturulursa `throw` , yığın izlemesi geçerli yöntemde yeniden başlatılır ve özel durumu oluşturan özgün yöntem ile geçerli yöntem arasındaki yöntem çağrılarının listesi kaybedilir. Özgün yığın izleme bilgilerini özel durumla birlikte tutmak için, `throw` özel durumu belirtmeden ifadesini kullanın.

Aşağıdaki kod parçacığı kural CA2200 için bir uyarı oluşturmaz. Ancak açıklamalı çizgi bir ihlalin *tetikleyecektir* .

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Özel durumu açıkça belirtmeden özel durumları yeniden throw. Daha fazla bilgi için bkz. [CA2200](/visualstudio/code-quality/ca2200).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
