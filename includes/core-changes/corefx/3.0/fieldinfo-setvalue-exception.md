---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449575"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur

.NET Core 3,0 ' den başlayarak, <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>çağırarak statik, <xref:System.Reflection.FieldAttributes.InitOnly> alanında bir değer ayarlamaya çalıştığınızda bir özel durum oluşturulur.

#### <a name="change-description"></a>Açıklamayı Değiştir

3,0 ' dan önceki .NET Core .NET Framework ve sürümlerinde, <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>çağırarak, başlatıldıktan sonra sabit bir statik alanın değerini ([salt okunur C# ](~/docs/csharp/language-reference/keywords/readonly.md)) ayarlayabilirsiniz. Ancak böyle bir alanın bu şekilde ayarlanması, hedef çerçeveye ve iyileştirme ayarlarına bağlı olarak öngörülemeyen davranışlara neden oldu.

.NET Core 3,0 ve sonraki sürümlerinde, statik, <xref:System.Reflection.FieldAttributes.InitOnly> alanında <xref:System.Reflection.FieldInfo.SetValue%2A> çağırdığınızda <xref:System.FieldAccessException?displayProperty=nameWithType> özel durumu oluşturulur.

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly> alan, yalnızca bildirildiği sırada veya kapsayan sınıf için oluşturucuda ayarlanabilir bir alandır. Diğer bir deyişle, başlatıldıktan sonra sabittir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Statik bir oluşturucuda statik, <xref:System.Reflection.FieldAttributes.InitOnly> alanları başlatın. Bu hem dinamik hem de dinamik olmayan türler için geçerlidir.

Alternatif olarak, <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> özniteliğini alandan kaldırabilir ve sonra <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>çağırabilirsiniz.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
