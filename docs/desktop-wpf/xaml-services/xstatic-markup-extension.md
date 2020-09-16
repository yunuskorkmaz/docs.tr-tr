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
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551617"
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
|`prefix`|İsteğe bağlı. Eşlenmiş, varsayılan olmayan XAML ad alanına başvuran bir ön ek. `prefix` , bir varsayılan XAML ad alanından gelen statik özelliklere nadiren başvurmanız nedeniyle açıkça kullanımda olarak gösterilir. Bkz. açıklamalar.|
|`typeName`|Gereklidir. İstenen statik üyeyi tanımlayan türün adı.|
|`staticMemberName`|Gereklidir. İstenen statik değer üyesinin adı (bir sabit, statik özellik, bir alan veya bir numaralandırma değeri).|

## <a name="remarks"></a>Açıklamalar

Başvurulan kod varlığı aşağıdakilerden biri olmalıdır:

- Bir sabit
- Statik Özellik
- Bir alan
- Sabit listesi değeri

Statik olmayan bir özellik gibi başka bir kod varlığının belirtilmesi, XAML biçimlendirme derlenmişse ya da XAML yükleme zamanı ayrıştırma özel durumu olduğunda derleme zamanı hatasına neden olur.

`x:Static`GEÇERLI xaml belgesi için varsayılan xaml ad alanında olmayan statik alanlara veya özelliklere başvurular yapabilirsiniz; ancak bu, bir önek eşlemesi gerektirir. Xaml ad alanları, XAML belgesinin kök öğesinde neredeyse her zaman tanımlanır.

Statik özellikler için arama işlemleri, .NET XAML Hizmetleri ve XAML okuyucuları ve XAML yazarları tarafından, varsayılan XAML şeması bağlamıyla çalışırken gerçekleştirilebilir. Bu XAML şema bağlamı, nesne grafiğinin oluşturulması için gerekli statik değerleri sağlamak üzere CLR yansımasını kullanabilir. `typeName`Aslında BIR CLR tür adı değil, BIR xaml tür adı değil, bu, varsayılan xaml şema bağlamı kullanılırken veya var olan tüm clr tabanlı xaml uygulayan çerçeveler kullanılırken aynı ada sahip olsa da.

`x:Static`Doğrudan bir özelliğin değerinin türü olmayan başvurular yaparken dikkatli olun. XAML işleme dizisinde, bir biçimlendirme uzantısından gelen değerler, ek değer dönüşümü çağırmaz. Bu, `x:Static` başvurunuz bir metin dizesi oluştursa ve metin dizesine dayalı öznitelik değerleri için değer dönüştürmesi genellikle söz konusu üye veya dönüş türünün herhangi bir üye değeri için ortaya çıkarsa, bu durum geçerlidir.

Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizeden sonra belirtilen dize belirteci, `x:Static` <xref:System.Windows.Markup.StaticExtension.Member%2A> temel uzantı sınıfının değeri olarak atanır <xref:System.Windows.Markup.StaticExtension> .

Teknik olarak mümkün olan iki farklı XAML kullanımı vardır. Ancak, bu kullanımlar gereksiz bir şekilde ayrıntılıdır, çünkü bu kullanımlar çok daha yaygındır:

01. Nesne öğesi sözdizimi.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. Başlatma dizesi için açık üye özelliği olan öznitelik sözdizimi.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.StaticExtension> .

`x:Static` bir biçimlendirme uzantısıdır. XAML 'deki tüm biçimlendirme uzantıları, bir `{` `}` XAML işlemcisinin bir değer sağlaması gerektiğini tanıdığı kural olan öznitelik sözdiziminde ve karakterlerini kullanır. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-overview.md).

## <a name="wpf-usage-notes"></a>WPF kullanım notları

WPF programlama için kullandığınız varsayılan XAML ad alanı çok sayıda faydalı statik özellik içermez ve yararlı statik özelliklerin çoğu, gerek olmadan kullanımı kolaylaştıran tür dönüştürücüler gibi destek içerir `{x:Static}` . Statik özellikler için aşağıdakilerden biri geçerliyse XAML ad alanı için bir ön eki eşlemeniz gerekir:

- WPF 'de bulunan ancak WPF () için varsayılan XAML ad alanının bir parçası olmayan bir türe başvuruyorsunuz `http://schemas.microsoft.com/winfx/2006/xaml/presentation` . Bu, kullanımı için oldukça yaygın bir senaryodur `x:Static` . Örneğin, `x:Static` <xref:System> sınıfın statik özelliklerine başvurmak için clr ad alanı ve mscorlib DERLEMESI için xaml ad alanı eşlemesi ile bir başvuru kullanabilirsiniz <xref:System.Environment> .

- Özel bir derlemeden bir türe başvuruyorsunuz.

- WPF derlemesinde bulunan bir türe başvuruyorsunuz, ancak bu tür WPF varsayılan XAML ad alanının parçası olacak şekilde eşlenmemiş bir CLR ad alanı içinde. CLR ad alanlarının WPF için varsayılan XAML ad alanı eşlemesi, çeşitli WPF derlemelerindeki tanımlar tarafından gerçekleştirilir (Bu kavram hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)). Eşlenen clr ad alanları, genellikle, gibi XAML için amaçlanan sınıf tanımlarından oluşuyorsa, bu CLR ad alanı var olabilir <xref:System.Windows.Threading> .

WPF için ön ekleri ve XAML ad alanlarını kullanma hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml).

## <a name="see-also"></a>Ayrıca bkz.

- [x:Type İşaretleme Uzantısı](xtype-markup-extension.md)
- [WPF'den System.Xaml'e Geçirilen Türler](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
