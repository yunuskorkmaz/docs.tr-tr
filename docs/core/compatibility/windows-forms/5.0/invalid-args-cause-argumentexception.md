---
title: 'Son değişiklik: WinForms yöntemleri şimdi ArgumentException oluşturur'
description: SWindows Forms yöntemlerinin artık geçersiz bağımsız değişkenler için bir ArgumentException oluşturması durumunda .NET 5,0 'deki önemli değişiklik hakkında bilgi edinin.
ms.date: 07/18/2020
ms.openlocfilehash: 46fe3f3b1208a5cd676e1b7546507bed36a850f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761717"
---
# <a name="winforms-methods-now-throw-argumentexception"></a>WinForms yöntemleri artık ArgumentException oluşturur

Bazı Windows Forms Yöntemler artık <xref:System.ArgumentException> , daha önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur. .NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentException> geçersiz bağımsız değişkenler geçirildiğinde bir oluşturur.

<xref:System.ArgumentException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0

## <a name="recommended-action"></a>Önerilen eylem

- Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.
- Gerekirse, <xref:System.ArgumentException> yöntemini çağırırken bir işleyin.

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:

| Yöntem | Parametre adı | Koşul | Sürüm eklendi |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Bağımsız değişken türünde değil <xref:System.Windows.Forms.TabPage> . | Önizleme 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | Bağımsız değişken `null` , <xref:System.String.Empty?displayProperty=nameWithType> veya boşluk. | Preview 5 |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | `InputLanguage`Belirtilen kültür için alınamıyor. | Önizleme 7 |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
