---
title: "x:XData İç XAML Türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: "17"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec46d0363e5b10d3bd3bd3f9c8f4d3694abc1c8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData İç XAML Türü
XAML üretim içinde XML veri Adaları yerleşimini sağlar. XML öğeleri içinde `x:XData` hareket varsayılan XAML ad uzayı parçası veya diğer bir XAML ad olmaları durumunda gibi XAML işlemcileri tarafından değerlendirilmelidir değil. `x:XData`rastgele doğru biçimlendirilmiş XML içerebilir.  
  
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
|`elementDataRoot`|Kapalı veri adası tek bir kök öğesi. En son Tüketiciler için tek bir kök olmayan XML geçersiz olarak kabul edilir. Özellikle, tek bir kök gerekli ise `x:XData` bir XML veri kaynağı olarak WPF veya XML kaynakları için veri bağlamayı kullanan diğer pek çok teknoloji yöneliktir.|  
|`[elementData]`|İsteğe bağlı. XML verilerini temsil eden XML. Öğeleri herhangi bir sayıda öğe verileri bulunabilir ve iç içe geçmiş öğe diğer öğeleri bulunabilir; Ancak, XML genel kurallar uygulanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 XML öğeleri içinde bir `x:XData` nesne tüm olası ad alanlarını ve öneklerini içeren XMLDOM verileri içinde yeniden bildirebilirsiniz.  
  
 XML verileri programlı olarak erişim ve `x:XData` iç XAML türü olan .NET Framework XAML Hizmetleri aracılığıyla, olası <xref:System.Windows.Markup.XData> sınıfı.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:XData` Nesnesi bir alt nesne olarak birincil olarak kullanılan bir <xref:System.Windows.Data.XmlDataProvider>, veya alternatif olarak, alt nesne <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> özelliği (XAML içinde bu genellikle özellik öğesi sözdiziminde ifade edilir).  
  
 Genellikle veri temel XML ad alanı (boş bir dize olarak ayarlayın) yeni bir varsayılan XML ad alanı olmasını veri adası içinde yeniden tanımlamanız. Basit veri çünkü Adaları için bu en kolayıdır <xref:System.Windows.Data.Binding.XPath%2A> başvuru ve veri bağlamak için kullanılan ifadeleri önekleri ekleme özen gösterin. Daha karmaşık veri Adaları verileri birden çok ön eklerini tanımlayın ve XML ad alanı kökünde için belirli bir ön ekini kullanın. Bu durumda, tüm <xref:System.Windows.Data.Binding.XPath%2A> ifade başvuruları uygun ad alanı eşlenen önek içermelidir. Daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Teknik olarak `x:XData` türü herhangi bir özelliği içeriği olarak kullanılan <xref:System.Xml.Serialization.IXmlSerializable>. Ancak, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> yalnızca belirgin uygulamasıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Veri Bağlamaya Genel Bakış](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [İşaretleme Uzantısı Bağlama](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
