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
ms.openlocfilehash: d78c2fd63192dc499b119e5b038b92555511a695
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544810"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData İç XAML Türü
Bir XAML üretimi içinde XML veri Adaları yerleştirmesini mümkün bir şekilde sunar. İçindeki XML öğeleri, `x:XData` işlem gören varsayılan xaml ad alanının veya DIĞER xaml ad alanının bir parçası gıbı XAML işlemcileri tarafından değerlendirilmemelidir. `x:XData` Rastgele düzgün biçimlendirilmiş XML içerebilir.

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
|`elementDataRoot`|İliştirilmiş veri Adası 'nin tek kök öğesi. En son tüketiciler için, tek bir köküne sahip olmayan XML geçersiz olarak kabul edilir. Özellikle, `x:XData` WPF için BIR XML veri kaynağı veya veri bağlama IÇIN XML kaynakları kullanan diğer teknolojiler için tasarlanan tek bir kök gereklidir.|
|`[elementData]`|İsteğe bağlı. XML verilerini temsil eden XML. Herhangi bir sayıda öğe öğe verisi, iç içe yerleştirilmiş öğeler ise diğer öğelerde bulunabilir; Ancak, XML 'nin genel kuralları geçerlidir.|

## <a name="remarks"></a>Açıklamalar

Bir nesne içindeki XML öğeleri, `x:XData` veri içinde bulunan XMLDOM 'ın tüm olası ad alanlarını ve öneklerini yeniden bildirebilir.

XML verilerine ve `x:XData` IÇSEL xaml türüne programlı erişim, sınıfı aracılığıyla .NET XAML hizmetlerinde mümkündür <xref:System.Windows.Markup.XData> .

## <a name="wpf-usage-notes"></a>WPF kullanım notları

`x:XData`Nesne öncelikle bir alt nesne olarak <xref:System.Windows.Data.XmlDataProvider> veya alternatif olarak özelliğin alt nesnesi olarak KULLANıLıR <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (XAML 'de, bu genellikle özellik öğesi söz diziminde ifade edilir).

Veriler genellikle veri Adası içindeki temel XML ad alanını yeni bir varsayılan XML ad alanı olacak şekilde (boş bir dizeye ayarlanır) yeniden tanımlamalıdır. Bu, basit veri Adaları için en kolay yoldur çünkü <xref:System.Windows.Data.Binding.XPath%2A> verilere başvurmak ve bağlanmak için kullanılan ifadeler ön eklerin dahil edilmesini önleyebilir. Daha karmaşık veri Adaları, veriler için birden çok önek tanımlayabilir ve kökte XML ad alanı için belirli bir önek kullanabilir. Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> ifade başvuruları uygun ad alanı eşlemeli öneki içermelidir. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

Teknik `x:XData` olarak, türünde herhangi bir özelliğin içeriği olarak kullanılabilir <xref:System.Xml.Serialization.IXmlSerializable> . Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tek belirgin uygulama.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.XmlDataProvider>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Biçimlendirme Uzantısı Bağlama](/dotnet/desktop/wpf/advanced/binding-markup-extension)
