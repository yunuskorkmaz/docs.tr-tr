---
title: 'Nasıl yapılır: CompositeCollection Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: f8af8d806b8c889be11533392ee3c831399e9ab7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556123"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="039c3-102">Nasıl yapılır: CompositeCollection Uygulama</span><span class="sxs-lookup"><span data-stu-id="039c3-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="039c3-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="039c3-103">Example</span></span>  
 <span data-ttu-id="039c3-104">Aşağıdaki örnek, birden çok koleksiyonları ve öğeleri kullanarak bir liste olarak görüntülemek üzere gösterilmiştir <xref:System.Windows.Data.CompositeCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="039c3-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="039c3-105">Bu örnekte, `GreekGods` olan bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `GreekGod` özel nesneleri.</span><span class="sxs-lookup"><span data-stu-id="039c3-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="039c3-106">Veri şablonları tanımlanan şekilde `GreekGod` nesneleri ve `GreekHero` nesneleri altın ve mavi ön plan rengini sırasıyla görünür.</span><span class="sxs-lookup"><span data-stu-id="039c3-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="039c3-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="039c3-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="039c3-108">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="039c3-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="039c3-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="039c3-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
