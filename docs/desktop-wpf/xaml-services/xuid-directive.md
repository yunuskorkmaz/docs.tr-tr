---
title: x:Uid Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: b5b480016d2183268422dea861510c6a169ac27b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071341"
---
# <a name="xuid-directive"></a>x:Uid Yönergesi

Biçimlendirme öğeleri için benzersiz bir tanımlayıcı sağlar. Birçok senaryoda, bu benzersiz tanımlayıcı XAML yerelleştirme işlemleri ve araçları tarafından kullanılır.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`identifier`|Bir `x:Uid` tüketici tarafından yorumlandığında bir dosyada benzersiz olması gereken el ile oluşturulmuş veya otomatik olarak oluşturulmuş dize.|

## <a name="remarks"></a>Açıklamalar

[MS-XAML], `x:Uid` bir yönerge olarak tanımlanır. Daha fazla bilgi için [ \[MS-XAML\] Bölüm 5.3.6'ya](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))bakın.

`x:Uid`belirtilen XAML `x:Name` yerelleştirme senaryosu nedeniyle her ikisinden de ayrıktır ve böylece yerelleştirme için kullanılan tanımlayıcıların programlama modelinin `x:Name`etkilerine herhangi bir bağımlılığı yoktur. Ayrıca, `x:Name` XAML isim skop tarafından yönetilir; ancak, `x:Uid` benzersizlik uygulama herhangi bir XAML dil tanımlı kavramı tarafından yönetilmez. Geniş anlamda XAML işlemcilerin (yerelleştirme işleminin bir parçası olmayan işlemcilerin) `x:Uid` değerlerin benzersizliğini zorlaması beklenmez. Bu sorumluluk kavramsal olarak değerlerin yaratıcısı üzerindedir. Tek bir XAML kaynağındaki `x:Uid` değerlerin benzersizliği beklentisi, özel küreselleşme süreçleri veya araçları gibi değerlerin tüketicileri için makuldür. Tipik teklik modeli, `x:Uid` değerlerin XAML'yi temsil eden XML kodlanmış bir dosya içinde benzersiz olmasıdır.

Belirli bir XAML şeması hakkında önemli bilgiye sahip `x:Uid` araçlar, biçimlendirmede metin dizesi değerinin karşılaştığı tüm durumlar yerine yalnızca gerçek yerelleştirilebilir dizeler için uygulamayı seçebilir.

Çerçeveler, tanımlama türüne öznitelik `x:Uid` <xref:System.Windows.Markup.UidPropertyAttribute> uygulayarak nesne modelinde belirli bir özelliğin diğer ad olduğunu belirtebilir. Bir çerçeve belirli bir özelliği belirtirse, hem `x:Uid` de diğer üyeyi aynı nesne üzerinde belirtmek geçerli değildir. Her `x:Uid` ikisi ve diğer ad üye belirtilirse, .NET XAML <xref:System.Xaml.XamlDuplicateMemberException> Services API genellikle bu servis talebi için atar.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

WPF yerelleştirme işleminin `x:Uid` rolü ve XAML'nin BAML formunda daha fazla bilgi için [WPF için Küreselleşme](../../framework/wpf/advanced/globalization-for-wpf.md) veya<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF için Genelleştirme](../../framework/wpf/advanced/globalization-for-wpf.md)
