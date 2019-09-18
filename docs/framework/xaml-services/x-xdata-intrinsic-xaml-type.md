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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053705"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData İç XAML Türü
Bir XAML üretimi içinde XML veri Adaları yerleştirmesini mümkün bir şekilde sunar. İçindeki `x:XData` XML öğeleri, işlem gören varsayılan xaml ad alanının veya diğer xaml ad alanının bir parçası gibi XAML işlemcileri tarafından değerlendirilmemelidir. `x:XData`Rastgele düzgün biçimlendirilmiş XML içerebilir.  
  
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
|`elementDataRoot`|İliştirilmiş veri Adası 'nin tek kök öğesi. En son tüketiciler için, tek bir köküne sahip olmayan XML geçersiz olarak kabul edilir. Özellikle, WPF için bir XML veri kaynağı veya veri `x:XData` bağlama için xml kaynakları kullanan diğer teknolojiler için tasarlanan tek bir kök gereklidir.|  
|`[elementData]`|İsteğe bağlı. XML verilerini temsil eden XML. Herhangi bir sayıda öğe öğe verisi, iç içe yerleştirilmiş öğeler ise diğer öğelerde bulunabilir; Ancak, XML 'nin genel kuralları geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `x:XData` nesne içindeki XML öğeleri, veri içinde bulunan XMLDOM 'ın tüm olası ad alanlarını ve öneklerini yeniden bildirebilir.  
  
 XML verilerine ve `x:XData` içsel xaml türüne programlı erişim, <xref:System.Windows.Markup.XData> sınıf aracılığıyla .NET Framework XAML hizmetlerinde mümkündür.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Nesne öncelikle bir <xref:System.Windows.Data.XmlDataProvider>alt nesne olarak veya alternatif olarak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliğin alt nesnesi olarak kullanılır (XAML 'de, bu genellikle özellik öğesi söz diziminde ifade edilir). `x:XData`  
  
 Veriler genellikle veri Adası içindeki temel XML ad alanını yeni bir varsayılan XML ad alanı olacak şekilde (boş bir dizeye ayarlanır) yeniden tanımlamalıdır. Bu, basit veri Adaları için en kolay yoldur <xref:System.Windows.Data.Binding.XPath%2A> çünkü verilere başvurmak ve bağlanmak için kullanılan ifadeler ön eklerin dahil edilmesini önleyebilir. Daha karmaşık veri Adaları, veriler için birden çok önek tanımlayabilir ve kökte XML ad alanı için belirli bir önek kullanabilir. Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> ifade başvuruları uygun ad alanı eşlemeli öneki içermelidir. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../wpf/data/data-binding-overview.md).  
  
 Teknik olarak `x:XData` , türünde <xref:System.Xml.Serialization.IXmlSerializable>herhangi bir özelliğin içeriği olarak kullanılabilir. Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tek belirgin uygulama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.XmlDataProvider>
- [Veri Bağlamaya Genel Bakış](../wpf/data/data-binding-overview.md)
- [İşaretleme Uzantısı Bağlama](../wpf/advanced/binding-markup-extension.md)
