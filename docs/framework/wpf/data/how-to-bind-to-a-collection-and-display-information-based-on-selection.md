---
title: 'Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 61ced27ed80adf8ac5d543584f71794b9ee59676
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188753"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="7de52-102">Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7de52-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="7de52-103">Basit bir ana öğe-ayrıntı senaryosunda elinizdeki verilere bağlı <xref:System.Windows.Controls.ItemsControl> gibi bir <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="7de52-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="7de52-104">Kullanıcı seçimine göre seçili öğe hakkında daha fazla bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7de52-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="7de52-105">Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7de52-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de52-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7de52-106">Example</span></span>  
 <span data-ttu-id="7de52-107">Bu örnekte, `People` olduğu bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `Person` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7de52-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="7de52-108">Bu `Person` sınıfı üç özellik içerir: `FirstName`, `LastName`, ve `HomeTown`, tümü `string`.</span><span class="sxs-lookup"><span data-stu-id="7de52-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="7de52-109"><xref:System.Windows.Controls.ContentControl> Aşağıdaki kullanan <xref:System.Windows.DataTemplate> tanımlayan nasıl bilgilerini bir `Person` sunulur:</span><span class="sxs-lookup"><span data-stu-id="7de52-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="7de52-110">Örneğin ürettiği bir ekran görüntüsü aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7de52-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="7de52-111"><xref:System.Windows.Controls.ContentControl> Seçilen kişinin diğer özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7de52-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="7de52-112">![Koleksiyona bağlama](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="7de52-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="7de52-113">Bu örnekte fark etmeye iki şey vardır:</span><span class="sxs-lookup"><span data-stu-id="7de52-113">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="7de52-114"><xref:System.Windows.Controls.ListBox> Ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır.</span><span class="sxs-lookup"><span data-stu-id="7de52-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="7de52-115"><xref:System.Windows.Data.Binding.Path%2A> Özellikleri belirtilmemiştir çünkü her iki denetim için tüm koleksiyon nesnesi belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="7de52-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2.  <span data-ttu-id="7de52-116">Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` Bunun çalışması.</span><span class="sxs-lookup"><span data-stu-id="7de52-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="7de52-117">Bu özelliğin ayarlanması sağlar Seçili öğe olarak her zaman ayarlandığından <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="7de52-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="7de52-118">Alternatif olarak, <xref:System.Windows.Controls.ListBox> öğesinden veri alır bir <xref:System.Windows.Data.CollectionViewSource>, seçim ve para birimi otomatik olarak eşitler.</span><span class="sxs-lookup"><span data-stu-id="7de52-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="7de52-119">Unutmayın `Person` sınıf geçersiz kılmalarını `ToString` yöntemini aşağıdaki şekilde.</span><span class="sxs-lookup"><span data-stu-id="7de52-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="7de52-120">Varsayılan olarak, <xref:System.Windows.Controls.ListBox> çağrıları `ToString` ve ilişkili koleksiyondaki her bir nesnenin dize gösterimini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7de52-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="7de52-121">İşte bu nedenle her `Person` ilk adı olarak görünür <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="7de52-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="7de52-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7de52-122">See also</span></span>

- [<span data-ttu-id="7de52-123">Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7de52-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="7de52-124">Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7de52-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="7de52-125">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7de52-125">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="7de52-126">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7de52-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="7de52-127">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7de52-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
