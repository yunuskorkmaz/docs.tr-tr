---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702495"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>WinForms yöntemleri artık ArgumentException oluşturur

Bazı Windows Forms Yöntemler artık <xref:System.ArgumentException> , daha önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur. .NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentException> geçersiz bağımsız değişkenler geçirildiğinde bir oluşturur.

<xref:System.ArgumentException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor. Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.

Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:

| Yöntem | Parametre adı | Koşul | Sürüm eklendi |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Bağımsız değişken türünde değil <xref:System.Windows.Forms.TabPage> . | 5,0 Preview 1 |

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Önerilen eylem

- Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.
- Gerekirse, <xref:System.ArgumentException> yöntemini çağırırken bir işleyin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
