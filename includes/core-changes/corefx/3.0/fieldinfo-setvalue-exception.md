---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721678"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur

.NET Core 3,0 ' den başlayarak, çağırarak statik, alan üzerinde bir değer ayarlamaya çalıştığınızda bir özel durum oluşturulur <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> .

#### <a name="change-description"></a>Açıklamayı Değiştir

3,0 ' dan önceki .NET Core .NET Framework ve sürümlerinde, öğesini çağırarak, sabit bir statik alanın değerini, başlatıldıktan sonra ([C# dilinde ReadOnly](~/docs/csharp/language-reference/keywords/readonly.md)) ayarlayabilirsiniz <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> . Ancak böyle bir alanın bu şekilde ayarlanması, hedef çerçeveye ve iyileştirme ayarlarına bağlı olarak öngörülemeyen davranışlara neden oldu.

.NET Core 3,0 ve sonraki sürümlerinde, <xref:System.Reflection.FieldInfo.SetValue%2A> bir statik, alanı çağırdığınızda bir <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.FieldAccessException?displayProperty=nameWithType> özel durum oluşturulur.

> [!TIP]
> Bir <xref:System.Reflection.FieldAttributes.InitOnly> alan, yalnızca bildirildiği sırada veya kapsayan sınıf için oluşturucuda ayarlanabilir bir alandır. Diğer bir deyişle, başlatıldıktan sonra sabittir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Reflection.FieldAttributes.InitOnly>Statik bir oluşturucuda statik, alanları başlatın. Bu hem dinamik hem de dinamik olmayan türler için geçerlidir.

Alternatif olarak, <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> alanından özniteliğini kaldırabilir ve ardından öğesini çağırabilirsiniz <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
