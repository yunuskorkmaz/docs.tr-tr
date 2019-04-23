---
title: 'Nasıl yapılır: CompositeCollection Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 8361c2bfa9c125aeadf0a62ca86af1855e5c3dbc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091172"
---
# <a name="how-to-implement-a-compositecollection"></a>Nasıl yapılır: CompositeCollection Uygulama
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok koleksiyon ve öğeler kullanarak bir liste olarak görüntülenecek gösterilmektedir <xref:System.Windows.Data.CompositeCollection> sınıfı. Bu örnekte, `GreekGods` olduğu bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `GreekGod` özel nesneler. Veri şablonları tanımlandığı şekilde `GreekGod` nesneleri ve `GreekHero` nesneleri altın ve mavi ön plan rengi ile sırasıyla görünür.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
