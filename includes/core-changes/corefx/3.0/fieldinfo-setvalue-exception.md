---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449575"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue statik, yalnızca init-only alanları için özel durum atar

.NET Core 3.0'dan başlayarak, statik bir <xref:System.Reflection.FieldAttributes.InitOnly> alana bir değer ayarlamaya <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>çalıştığınızda bir özel durum atılır.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework ve .NET Core sürümlerinde 3.0'dan önce,[(yalnızca C# olarak okunur)](~/docs/csharp/language-reference/keywords/readonly.md)olarak adlandırıldıktan <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>sonra sabit olan statik alanın değerini ayarlayabilirsiniz. Ancak, böyle bir alanın bu şekilde ayarlanması, hedef çerçeve ve optimizasyon ayarlarına dayalı öngörülemeyen davranışlara yol açtı.

.NET Core 3.0 ve sonraki sürümlerinde, statik, <xref:System.Reflection.FieldInfo.SetValue%2A> <xref:System.Reflection.FieldAttributes.InitOnly> alan <xref:System.FieldAccessException?displayProperty=nameWithType> üzerinde arama yaptığınızda, bir özel durum atılır.

> [!TIP]
> Alan, <xref:System.Reflection.FieldAttributes.InitOnly> yalnızca beyan edildiği anda veya içeren sınıfın oluşturucusunda ayarlanabilen alandır. Başka bir deyişle, baş harfe basıldıktan sonra sabittir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Statik, <xref:System.Reflection.FieldAttributes.InitOnly> statik bir oluşturucu alanları başlatma. Bu, hem dinamik hem de dinamik olmayan türler için geçerlidir.

Alternatif olarak, özniteliği <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> alandan kaldırabilir ve <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>sonra çağırabilirsiniz.

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
