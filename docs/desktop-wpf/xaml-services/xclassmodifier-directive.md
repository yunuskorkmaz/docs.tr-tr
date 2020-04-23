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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072034"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier Yönergesi
XAML derleme davranışını `x:Class` da sağlandığında değiştirir. Özellikle, erişim düzeyi `class` (varsayılan) `Public` olan bir kısmi oluşturmak `x:Class` yerine, `NotPublic` sağlanan bir erişim düzeyi ile oluşturulur. Bu davranış, oluşturulan derlemelerde sınıfın erişim düzeyini etkiler.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*Genel Not*|Karşı belirtmek <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> için geçecek <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> tam dize, kullandığınız kod arkası programlama diline bağlı olarak değişir. Bkz. Açıklamalar.|

## <a name="dependencies"></a>Bağımlılıklar

[x:Sınıf](xclass-directive.md) da aynı öğe üzerinde sağlanmalıdır ve bu öğe bir sayfadaki kök öğe olmalıdır. Daha fazla bilgi için [ \[MS-XAML\] Bölüm 4.3.1.8'e](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

## <a name="remarks"></a>Açıklamalar

.NET `x:ClassModifier` XAML Hizmetleri'ndeki değer programlama diline göre değişir. Kullanılacak dize, her dilin kendi <xref:System.CodeDom.Compiler.CodeDomProvider> sini nasıl uyguladığına ve anlamları tanımlamak <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>için döndürdüğü tür dönüştürücülerine ve bu dilin büyük/küçük harf duyarlı olup olmadığına bağlıdır.

- C# için, belirtmek <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçmek `internal`için dize.

- Microsoft Visual Basic .NET için, belirtmek <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`için geçmek için dize.

- C++/CLI için XAML derlemeyi destekleyen hiçbir hedef yoktur; bu nedenle, geçmek için değer belirtilmemiştir.

Ayrıca belirtebilirsiniz <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `public` (C#, `Public` Visual Basic'te); ancak, zaten <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> varsayılan davranış <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olduğundan belirtme seyrek yapılır.

C# gibi `private` eşdeğer kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer `x:ClassModifier` değerler, iç içe geçen sınıf başvuruları XAML'de desteklenmediği ve bu nedenle değiştiricinin <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> aynı etkiye sahip olması nedeniyle ilgili değildir.

## <a name="security-notes"></a>Güvenlik Notları

Beyan edildiği `x:ClassModifier` gibi erişim düzeyi hala belirli çerçeveler ve yetenekleri tarafından yorumlanmasına tabidir. WPF, bir paket URI başvurusu aracılığıyla `x:ClassModifier` wpf kaynağından `internal`başvurulmuşsa, türleri yüklemek ve anlık olarak yüklemek için yetenekler içerir. Bu durumda bir sonucu olarak ve diğer çerçeveler tarafından uygulanan gibi potansiyel `x:ClassModifier` diğerleri, sadece tüm olası anlık açma girişimleri engellemek için güvenmeyin.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier Yönergesi](xfieldmodifier-directive.md)
- [Güvenlik (WPF)](../../framework/wpf/security-wpf.md)
- [WPF'den System.Xaml'e Geçirilen Türler](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
