---
title: x:Uid Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 32cfd9ab0cf6037c731b619e81a7504ac92d5fb9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837187"
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
|`identifier`|Bir `x:Uid` tüketicisi tarafından yorumlanan bir dosyada benzersiz olması gereken el ile oluşturulmuş veya otomatik oluşturulan dize.|  
  
## <a name="remarks"></a>Açıklamalar  
 [MS-XAML] içinde `x:Uid` bir yönerge olarak tanımlanır. Daha fazla bilgi için bkz. [\[MS-XAML\] Bölüm 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 `x:Uid`, belirtilen XAML yerelleştirme senaryosu nedeniyle her ikisi de `x:Name` ayrı değildir ve bu nedenle yerelleştirme için kullanılan tanımlayıcıların, `x:Name`programlama modeli etkilerine bağımlılığı yoktur. Ayrıca, `x:Name` XAML namescope 'un tabidir; Ancak, `x:Uid` hiçbir XAML dili tarafından tanımlanan benzersizlik zorlaması kavramı tarafından yönetilmez. Büyük bir Sense (yerelleştirme sürecinin parçası olmayan işlemciler) için XAML işlemcileri, `x:Uid` değerlerinin benzersizliğini zorlayacağı için beklenmez. Bu sorumluluk, değerleri oluşturan kavramsal olarak belirlenir. Tek XAML kaynağı içindeki `x:Uid` değerlerinin benzersizliği, adanmış genelleştirme süreçler veya araçlar gibi değer tüketicileri için uygun değildir. Tipik benzersizlik modeli, `x:Uid` değerlerinin XAML 'yi temsil eden XML kodlu bir dosya içinde benzersiz olduğu değerlerdir.  
  
 Belirli bir XAML şeması hakkında önemli bilgiler içeren araçlar, İşaretlemede bir metin dizesi değerine rastlandı tüm durumlar yerine yalnızca doğru yerelleştirilebilir dizeler için `x:Uid` uygulamayı seçebilir.  
  
 Çerçeveler, nesne modelindeki belirli bir özelliği, öznitelik <xref:System.Windows.Markup.UidPropertyAttribute> tanımlayan türe uygulayarak `x:Uid` için bir diğer ad olarak belirtebilir. Bir çerçeve belirli bir özelliği belirtiyorsa, aynı nesne üzerinde hem `x:Uid` hem de diğer ad üyesini belirtmek geçerli değildir. Hem `x:Uid` hem de diğer ad üyesi belirtilirse, .NET Framework XAML Hizmetleri API 'SI genellikle bu durum için <xref:System.Xaml.XamlDuplicateMemberException> oluşturur.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF yerelleştirme işlemindeki `x:Uid` rolü ve XAML 'nin BAML formundaki hakkında daha fazla bilgi için bkz. about [Genelleştirme for WPF](../wpf/advanced/globalization-for-wpf.md) veya <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF için Genelleştirme](../wpf/advanced/globalization-for-wpf.md)
