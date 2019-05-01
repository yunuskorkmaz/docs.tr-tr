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
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938833"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData İç XAML Türü
XAML üretim içinde XML veri Adaları yerleşimini sağlar. XML öğeleri içinde `x:XData` veya herhangi bir XAML ad acting varsayılan XAML ad alanı bir parçası olmaları durumunda gibi XAML işlemcileri tarafından değerlendirilmesi gerektiğini değil. `x:XData` rastgele iyi biçimlendirilmiş bir XML içerebilir.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`elementDataRoot`|Kapalı bir veri adası tek kök öğesi. En son Tüketiciler için tek bir kök olmayan XML geçersiz olarak kabul edilir. Özellikle, tek bir kök gereklidir `x:XData` bir XML veri kaynağı olarak WPF veya XML kaynakları için veri bağlama kullanan diğer pek çok teknoloji yöneliktir.|  
|`[elementData]`|İsteğe bağlı. XML verileri temsil eder XML. Öğeleri herhangi bir sayıda öğe verileri yer alabilir ve iç içe öğeleri diğer öğeler yer alabilir. Ancak, XML'in genel kurallar uygulanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 XML öğeleri içinde bir `x:XData` nesne tüm olası ad alanlarını ve önekleri içeren XMLDOM verilerdeki, yeniden bildirebilirsiniz.  
  
 XML verilerini için programlı erişim ve `x:XData` iç XAML türü .NET Framework XAML hizmetlerinde içinde olası <xref:System.Windows.Markup.XData> sınıfı.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:XData` Nesne öncelikle bir alt nesnesi olarak kullanılan bir <xref:System.Windows.Data.XmlDataProvider>, ya da alternatif olarak, alt nesnesi olarak <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliği (XAML içinde bu genellikle özellik öğesi sözdizimine ifade edilir).  
  
 Verileri, genellikle yeni bir varsayılan XML ad (boş dize olarak ayarlanmış) olmasını veri adası içinde temel XML ad alanı tanımlamalıdır. Çünkü basit veri Adaları için bu en kolayıdır <xref:System.Windows.Data.Binding.XPath%2A> başvuru ve verilere bağlamak için kullanılan ifadeler önekleri ekleme önlemek. Daha karmaşık veri Adaları verileri birden çok ön eklerini tanımlayın ve kök XML ad alanı için belirli bir önek kullanın. Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> başvuruyor, uygun ad alanı eşlemeli önek içermelidir. Daha fazla bilgi için [Data Binding Overview](../wpf/data/data-binding-overview.md).  
  
 Teknik olarak `x:XData` içeriğini türünde herhangi bir özelliği kullanılabilir <xref:System.Xml.Serialization.IXmlSerializable>. Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> yalnızca tanınmış bir uygulamasıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.XmlDataProvider>
- [Veri Bağlamaya Genel Bakış](../wpf/data/data-binding-overview.md)
- [İşaretleme Uzantısı Bağlama](../wpf/advanced/binding-markup-extension.md)
