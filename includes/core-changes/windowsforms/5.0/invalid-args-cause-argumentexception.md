---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158416"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>WinForms yöntemleri artık ArgumentException oluşturur

Bazı Windows Forms Yöntemler artık, daha <xref:System.ArgumentException> önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur. .NET 5,0 ' den başlayarak, bu yöntemler artık geçersiz <xref:System.ArgumentException> bağımsız değişkenler geçirildiğinde bir oluşturur.

.NET çalışma <xref:System.ArgumentException> zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.

Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:

| Yöntem | Parametre adı | Koşul | Sürüm eklendi |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Bağımsız değişken türünde <xref:System.Windows.Forms.TabPage>değil. | 5,0 Preview 1 |

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Önerilen eylem

- Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.
- Gerekirse, yöntemini çağırırken bir <xref:System.ArgumentException> işleyin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
