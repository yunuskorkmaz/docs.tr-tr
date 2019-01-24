---
title: 'Nasıl yapılır: CompositeCollection Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 2021ed83a8f2a6896631fa69d5dd55a74cad8a8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691872"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="fb3ef-102">Nasıl yapılır: CompositeCollection Uygulama</span><span class="sxs-lookup"><span data-stu-id="fb3ef-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="fb3ef-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb3ef-103">Example</span></span>  
 <span data-ttu-id="fb3ef-104">Aşağıdaki örnek, birden çok koleksiyon ve öğeler kullanarak bir liste olarak görüntülenecek gösterilmektedir <xref:System.Windows.Data.CompositeCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fb3ef-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="fb3ef-105">Bu örnekte, `GreekGods` olduğu bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `GreekGod` özel nesneler.</span><span class="sxs-lookup"><span data-stu-id="fb3ef-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="fb3ef-106">Veri şablonları tanımlandığı şekilde `GreekGod` nesneleri ve `GreekHero` nesneleri altın ve mavi ön plan rengi ile sırasıyla görünür.</span><span class="sxs-lookup"><span data-stu-id="fb3ef-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fb3ef-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb3ef-107">See also</span></span>
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="fb3ef-108">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fb3ef-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="fb3ef-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="fb3ef-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
