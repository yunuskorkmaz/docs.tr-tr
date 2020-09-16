---
title: x:ClassModifier Yönergesi
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544823"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier Yönergesi
Ayrıca sağlandığında XAML derleme davranışını değiştirir `x:Class` . Özellikle, erişim düzeyine sahip bir kısmi oluşturmak yerine `class` `Public` (varsayılan), belirtilen bir `x:Class` `NotPublic` erişim düzeyiyle oluşturulur. Bu davranış, oluşturulan derlemelerdeki sınıfın erişim düzeyini etkiler.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*NotPublic*|Belirtmek için geçirilecek tam dize <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullandığınız arka plan kod programlama diline bağlı olarak farklılık gösterir. Bkz. açıklamalar.|

## <a name="dependencies"></a>Bağımlılıklar

[X:Class](xclass-directive.md) aynı öğe üzerinde de sağlanmalıdır ve bu öğenin bir sayfada kök öğe olması gerekir. Daha fazla bilgi için bkz. [ \[ MS-xaml \] section 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Açıklamalar

`x:ClassModifier`.Net xaml Hizmetleri kullanımındaki değeri programlama diline göre farklılık gösterir. Kullanılacak dize, her dilin <xref:System.CodeDom.Compiler.CodeDomProvider> ve için anlamlarını ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.

- C# için, atamak için geçirilecek dize <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olur `internal` .

- Microsoft Visual Basic .NET için, atamak için geçirilecek dize <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olur `Friend` .

- C++/CLı için XAML derlemeyi destekleyen bir hedef yoktur; Bu nedenle, geçirilecek değer belirtilmemiş.

Ayrıca, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ( `public` C# ' de Visual Basic) öğesini de belirtebilirsiniz `Public` ; ancak, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> varsayılan davranış zaten olduğu için, belirtme daha seyrek yapılır <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> .

C# ' de olduğu gibi eşdeğer Kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer değerler, `private` `x:ClassModifier` iç içe geçmiş sınıf başvuruları xaml 'de desteklenmediğinden, bu nedenle <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> değiştirici aynı etkiye sahiptir.

## <a name="security-notes"></a>Güvenlik notları

İçinde bildirildiği gibi erişim düzeyi `x:ClassModifier` , hala belirli çerçeveler ve bunların özelliklerine göre yoruma tabidir. WPF, bir `x:ClassModifier` `internal` paket URI başvurusu aracılığıyla bir WPF kaynağından başvuruluyorsa, türü yükleme ve örnek oluşturma özelliklerini içerir. Bu durumun bir sonucu ve diğer çerçeveler tarafından uygulandığı gibi diğerleri, `x:ClassModifier` olası tüm örnek oluşturma girişimlerini engellemek için özel olarak açık değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:FieldModifier Yönergesi](xfieldmodifier-directive.md)
- [Güvenlik (WPF)](/dotnet/desktop/wpf/security-wpf)
- [WPF'den System.Xaml'e Geçirilen Türler](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
