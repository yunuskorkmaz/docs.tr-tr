---
title: 'Nasıl yapılır: CompositeCollection Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 8361c2bfa9c125aeadf0a62ca86af1855e5c3dbc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931683"
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
