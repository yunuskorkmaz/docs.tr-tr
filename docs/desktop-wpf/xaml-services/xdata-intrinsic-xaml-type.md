---
title: x:XData İç XAML Türü
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071544"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData İç XAML Türü
XML veri adalarının XAML üretimi içinde yerleştirilmesine olanak sağlar. İçerdeki `x:XData` XML öğeleri XAML işlemciler tarafından varsayılan XAML ad alanının veya başka bir XAML ad alanının bir parçasıymuş gibi ele alınmamalıdır. `x:XData`rasgele iyi biçimlendirilmiş XML içerebilir.

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`elementDataRoot`|Kapalı veri adasının tek kök öğesi. Çoğu nihai tüketici için, tek bir köke sahip olmayan XML geçersiz kabul edilir. Özellikle, WPF veya veri `x:XData` bağlama için XML kaynaklarını kullanan diğer birçok teknoloji için XML veri kaynağı olarak tasarlanmıştırsa, tek bir kök gereklidir.|
|`[elementData]`|İsteğe bağlı. XML verilerini temsil eden XML. Eleman verileri ve iç içe öğeler diğer öğelerde bulunabilir gibi elemanların herhangi bir sayı bulunabilir; ancak, XML genel kuralları geçerlidir.|

## <a name="remarks"></a>Açıklamalar

Bir `x:XData` nesneiçindeki XML öğeleri, veriler içinde xmldom içeren tüm olası ad alanlarını ve öneklerini yeniden bildirebilir.

XML verilerine ve `x:XData` içsel XAML türüne programlı erişim .NET XAML Services'da <xref:System.Windows.Markup.XData> sınıf aracılığıyla mümkündür.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

Nesne `x:XData` öncelikle bir <xref:System.Windows.Data.XmlDataProvider>alt nesne olarak kullanılır , veya alternatif olarak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliğin alt nesnesi olarak (XAML, bu genellikle özellik öğesi sözdizimi ifade edilir).

Veriler genellikle veri adasındaki temel XML ad alanını yeni bir varsayılan XML ad alanı (boş bir dize olarak ayarlanmış) olarak yeniden tanımlamalıdır. Bu basit veri adaları için <xref:System.Windows.Data.Binding.XPath%2A> en kolayıdır, çünkü verilere başvurmak ve bağlamak için kullanılan ifadeler öneklerin eklenmesini önleyebilir. Daha karmaşık veri adaları veriler için birden çok önek tanımlayabilir ve kökteki XML ad alanı için belirli bir önek kullanabilir. Bu durumda, <xref:System.Windows.Data.Binding.XPath%2A> tüm ifade başvuruları uygun ad alanı eşlenen öneki içermelidir. Daha fazla bilgi için bkz: [Veri Bağlama Genel Bakışı.](../data/data-binding-overview.md)

Teknik olarak, `x:XData` türü <xref:System.Xml.Serialization.IXmlSerializable>herhangi bir özelliğin içeriği olarak kullanılabilir. Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tek önemli uygulamadır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.XmlDataProvider>
- [Veri Bağlama Genel Bakış](../data/data-binding-overview.md)
- [Biçimlendirme Uzantısı Bağlama](../../framework/wpf/advanced/binding-markup-extension.md)
