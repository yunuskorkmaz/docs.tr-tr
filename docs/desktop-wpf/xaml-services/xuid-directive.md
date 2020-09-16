---
title: x:Uid Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 3de02702e6fd2be63bc2d099dad11f896b281ad1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543504"
---
# <a name="xuid-directive"></a>x:Uid Yönergesi

Biçimlendirme öğeleri için benzersiz bir tanımlayıcı sağlar. Birçok senaryoda, bu benzersiz tanımlayıcı XAML yerelleştirme işlemi ve araçları tarafından kullanılır.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`identifier`|Bir tüketici tarafından yorumlanırken bir dosyada benzersiz olması gereken el ile oluşturulmuş veya otomatik oluşturulan dize `x:Uid` .|

## <a name="remarks"></a>Açıklamalar

[MS-XAML] içinde `x:Uid` bir yönerge olarak tanımlanmıştır. Daha fazla bilgi için bkz. [ \[ MS-xaml \] Section 5.3.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid` , `x:Name` BELIRTILEN xaml yerelleştirme senaryosu nedeniyle her ikisi de ayrı değildir ve bu nedenle Yerelleştirmede kullanılan tanımlayıcıların, programlama modeli etkilerine ilişkin hiçbir bağımlılığı yoktur `x:Name` . Ayrıca `x:Name` xaml namescope tarafından yönetilir; ancak, `x:Uid` hiçbir xaml dili tarafından tanımlanan benzersizlik zorlaması kavramı tarafından yönetilmez. XAML işlemcileri, büyük bir anlamda (yerelleştirme işleminin parçası olmayan işlemciler) değerlerin benzersizlik zorlaması beklenmez `x:Uid` . Bu sorumluluk, değerleri oluşturan kavramsal olarak belirlenir. `x:Uid`Tek BIR xaml kaynağı içindeki değerlerin benzersizliği, adanmış genelleştirme süreçler veya araçlar gibi değer tüketicileri için uygun değildir. Tipik benzersizlik modeli, `x:Uid` DEĞERLERIN xaml 'yi temsil eden XML kodlu bir dosya içinde benzersiz olduğu değerlerdir.

Belirli bir XAML şeması hakkında önemli bilgiler içeren Araçlar `x:Uid` , İşaretlemede bir metin dizesi değerine rastlandı tüm durumlar yerine yalnızca doğru yerelleştirilebilir dizeler için geçerli olabilir.

Çerçeveler, nesne modelindeki belirli bir özelliği, `x:Uid` özniteliği tanımlayan türe uygulayarak bir diğer ad olacak şekilde belirtebilir <xref:System.Windows.Markup.UidPropertyAttribute> . Bir çerçeve belirli bir özelliği belirtiyorsa, `x:Uid` aynı nesne üzerinde hem hem de diğer ad üyesini belirtmek geçerli değildir. Hem hem de `x:Uid` diğer ad üyesi belirtilirse, .net xaml Hizmetleri API 'si genellikle <xref:System.Xaml.XamlDuplicateMemberException> Bu durum için oluşturulur.

## <a name="wpf-usage-notes"></a>WPF kullanım notları

`x:Uid`WPF yerelleştirme işleminde ve xaml 'nın BAML formundaki rolü hakkında daha fazla bilgi için bkz. [WPF için Genelleştirme](/dotnet/desktop/wpf/advanced/globalization-for-wpf) veya<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF için Genelleştirme](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
