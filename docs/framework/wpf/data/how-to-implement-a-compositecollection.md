---
title: 'Nasıl yapılır: CompositeCollection Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454031"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="adf10-102">Nasıl yapılır: CompositeCollection Uygulama</span><span class="sxs-lookup"><span data-stu-id="adf10-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="adf10-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="adf10-103">Example</span></span>  
 <span data-ttu-id="adf10-104">Aşağıdaki örnek, <xref:System.Windows.Data.CompositeCollection> sınıfını kullanarak birden çok koleksiyonun ve öğenin tek bir liste olarak nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="adf10-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="adf10-105">Bu örnekte `GreekGods`, `GreekGod` özel nesnelerin bir <xref:System.Collections.ObjectModel.ObservableCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="adf10-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="adf10-106">Veri şablonları, `GreekGod` nesneleri ve `GreekHero` nesneleri sırasıyla altın ve Camgöbeği bir ön plan rengiyle görünecek şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="adf10-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="adf10-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adf10-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="adf10-108">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="adf10-108">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="adf10-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="adf10-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
