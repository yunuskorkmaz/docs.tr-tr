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
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459902"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData İç XAML Türü
Bir XAML üretimi içinde XML veri Adaları yerleştirmesini mümkün bir şekilde sunar. `x:XData` içindeki XML öğeleri, işlem gören varsayılan XAML ad alanının veya diğer XAML ad alanının bir parçası gibi XAML işlemcileri tarafından değerlendirilmemelidir. `x:XData`, düzgün biçimlendirilmiş rastgele XML içerebilir.  
  
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
|`elementDataRoot`|İliştirilmiş veri Adası 'nin tek kök öğesi. En son tüketiciler için, tek bir köküne sahip olmayan XML geçersiz olarak kabul edilir. Özellikle, `x:XData` WPF için bir XML veri kaynağı ya da veri bağlama için XML kaynakları kullanan diğer birçok teknoloji olarak tasarlanıyorsa tek bir kök gerekir.|  
|`[elementData]`|İsteğe bağlı. XML verilerini temsil eden XML. Herhangi bir sayıda öğe öğe verisi, iç içe yerleştirilmiş öğeler ise diğer öğelerde bulunabilir; Ancak, XML 'nin genel kuralları geçerlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `x:XData` nesnesi içindeki XML öğeleri, verilerin içinde bulunan XMLDOM 'ın tüm olası ad alanlarını ve öneklerini yeniden bildirebilir.  
  
 .NET Framework XAML hizmetlerinde <xref:System.Windows.Markup.XData> sınıfı aracılığıyla XML verilerine ve `x:XData` iç XAML türüne programlı erişim mümkündür.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:XData` nesnesi öncelikle bir <xref:System.Windows.Data.XmlDataProvider>alt nesne olarak veya alternatif olarak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliğinin alt nesnesi olarak kullanılır (XAML 'de, bu genellikle özellik öğesi söz diziminde ifade edilir).  
  
 Veriler genellikle veri Adası içindeki temel XML ad alanını yeni bir varsayılan XML ad alanı olacak şekilde (boş bir dizeye ayarlanır) yeniden tanımlamalıdır. Bu, basit veri Adaları için en kolay yoldur çünkü verilere başvurmak ve bağlanmak için kullanılan <xref:System.Windows.Data.Binding.XPath%2A> ifadeleri ön eklerin dahil edilmesini önleyebilir. Daha karmaşık veri Adaları, veriler için birden çok önek tanımlayabilir ve kökte XML ad alanı için belirli bir önek kullanabilir. Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> ifade başvuruları uygun ad alanı eşlemeli öneki içermelidir. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../desktop-wpf/data/data-binding-overview.md).  
  
 Teknik olarak, `x:XData` <xref:System.Xml.Serialization.IXmlSerializable>türünde herhangi bir özelliğin içeriği olarak kullanılabilir. Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> tek belirgin uygulama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.XmlDataProvider>
- [Veri Bağlamaya Genel Bakış](../../desktop-wpf/data/data-binding-overview.md)
- [İşaretleme Uzantısı Bağlama](../wpf/advanced/binding-markup-extension.md)
