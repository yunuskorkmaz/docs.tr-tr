---
title: "Nasıl yapılır: CompositeCollection Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b33e3a61b91c2f9e2362a270216038d61770b815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-compositecollection"></a>Nasıl yapılır: CompositeCollection Uygulama
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok koleksiyonları ve öğeleri kullanarak bir liste olarak görüntülemek üzere gösterilmiştir <xref:System.Windows.Data.CompositeCollection> sınıfı. Bu örnekte, `GreekGods` olan bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `GreekGod` özel nesneleri. Veri şablonları tanımlanan şekilde `GreekGod` nesneleri ve `GreekHero` nesneleri altın ve mavi ön plan rengini sırasıyla görünür.  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
