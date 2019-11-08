---
title: x:Static İşaretleme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: bf94f1d61ee3080c9d3582e55e0695b269801c80
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733366"
---
# <a name="xstatic-markup-extension"></a>x:Static İşaretleme Uzantısı
Ortak dil belirtimi (CLS) ile uyumlu bir şekilde tanımlanan herhangi bir statik değere sahip kod varlığına başvurur. Başvurulan static özelliği, XAML içindeki bir özelliğin değerini sağlamak için kullanılabilir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
| | |  
|-|-|  
|`prefix`|İsteğe bağlı. Eşlenmiş, varsayılan olmayan XAML ad alanına başvuran bir ön ek. bir varsayılan XAML ad alanından gelen statik özelliklere nadiren başvurmanız gerektiğinden `prefix` kullanımda açık olarak gösterilir. Bkz. açıklamalar.|  
|`typeName`|Gerekli. İstenen statik üyeyi tanımlayan türün adı.|  
|`staticMemberName`|Gerekli. İstenen statik değer üyesinin adı (bir sabit, statik özellik, bir alan veya bir numaralandırma değeri).|  
  
## <a name="remarks"></a>Açıklamalar  

Başvurulan kod varlığı aşağıdakilerden biri olmalıdır:  
  
- Bir sabit  
- Statik Özellik  
- Bir alan  
- Sabit listesi değeri

Statik olmayan bir özellik gibi başka bir kod varlığının belirtilmesi, XAML biçimlendirme derlenmişse ya da XAML yükleme zamanı ayrıştırma özel durumu olduğunda derleme zamanı hatasına neden olur.  

Geçerli XAML belgesi için varsayılan XAML ad alanında olmayan statik alanlara veya özelliklere `x:Static` başvuruları yapabilirsiniz; Ancak, bu bir önek eşlemesi gerektirir. Xaml ad alanları, XAML belgesinin kök öğesinde neredeyse her zaman tanımlanır.  

Statik özelliklerin arama işlemleri, .NET Framework XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları tarafından, varsayılan XAML şeması içeriğiyle çalışırken gerçekleştirilebilir. Bu XAML şema bağlamı, nesne grafiğinin oluşturulması için gerekli statik değerleri sağlamak üzere CLR yansımasını kullanabilir. Belirttiğiniz `typeName`, CLR tür adı değil, aslında bir XAML tür adıdır, ancak varsayılan XAML şema bağlamı kullanılırken veya mevcut tüm CLR tabanlı XAML uygulayan çerçeveler kullanılırken bunlar temelde aynı addır.  

Doğrudan bir özelliğin değerinin türü olmayan `x:Static` başvuruları yaparken dikkatli olun. XAML işleme dizisinde, bir biçimlendirme uzantısından gelen değerler, ek değer dönüşümü çağırmaz. Bu, `x:Static` başvurunuz bir metin dizesi oluştursa ve metin dizesine dayalı öznitelik değerleri için değer dönüştürmesi genellikle söz konusu üye için ya da dönüş türünün herhangi bir üye değeri için ortaya çıkarsa, bu durum geçerlidir.  

Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `x:Static` tanımlayıcı dizeden sonra belirtilen dize belirteci, temel <xref:System.Windows.Markup.StaticExtension> uzantı sınıfının <xref:System.Windows.Markup.StaticExtension.Member%2A> değeri olarak atanır.  

Teknik olarak mümkün olan iki farklı XAML kullanımı vardır. Ancak, bu kullanımlar gereksiz bir şekilde ayrıntılıdır, çünkü bu kullanımlar çok daha yaygındır:  

1. Nesne öğesi sözdizimi.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. Başlatma dizesi için açık üye özelliği olan öznitelik sözdizimi.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

.NET Framework XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Markup.StaticExtension> sınıfı tarafından tanımlanır.  

`x:Static`, biçimlendirme uzantısıdır. XAML 'deki tüm biçimlendirme uzantıları, bir XAML işlemcisinin bir değer sağlaması gerektiğini tanıdığı kural olan öznitelik sözdiziminde `{` ve `}` karakterlerini kullanır. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 WPF programlama için kullandığınız varsayılan XAML ad alanı çok sayıda faydalı statik özellik içermez ve yararlı statik özelliklerin çoğu, `{x:Static}` gerekmeden kullanımı kolaylaştıran tür dönüştürücüler gibi destek içerir. Statik özellikler için aşağıdakilerden biri geçerliyse XAML ad alanı için bir ön eki eşlemeniz gerekir:  
  
- WPF 'de bulunan ancak WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`) için varsayılan XAML ad alanının bir parçası olmayan bir türe başvuruyorsunuz. Bu, `x:Static`kullanmaya yönelik oldukça yaygın bir senaryodur. Örneğin, <xref:System.Environment> sınıfının statik özelliklerine başvurmak için <xref:System> CLR ad alanı ve mscorlib bütünleştirilmiş kodu ile XAML ad alanı eşlemesi olan bir `x:Static` başvurusunu kullanabilirsiniz.  
  
- Özel bir derlemeden bir türe başvuruyorsunuz.  
  
- WPF derlemesinde bulunan bir türe başvuruyorsunuz, ancak bu tür WPF varsayılan XAML ad alanının parçası olacak şekilde eşlenmemiş bir CLR ad alanı içinde. CLR ad alanlarının WPF için varsayılan XAML ad alanı eşlemesi, çeşitli WPF derlemelerindeki tanımlar tarafından gerçekleştirilir (Bu kavram hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Bu CLR ad alanı, genellikle <xref:System.Windows.Threading>gibi XAML için tasarlanmamış sınıf tanımlarından oluşuyorsa, eşlenmiş olmayan CLR ad alanları bulunabilir.  
  
 WPF için ön ekleri ve XAML ad alanlarını kullanma hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Type İşaretleme Uzantısı](x-type-markup-extension.md)
- [WPF'den System.Xaml'e Geçirilen Türler](types-migrated-from-wpf-to-system-xaml.md)
