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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459148"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="539be-102">Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="539be-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="539be-103">Basit bir ana ayrıntı senaryosunda, <xref:System.Windows.Controls.ListBox>gibi bir veri bağlantılı <xref:System.Windows.Controls.ItemsControl> vardır.</span><span class="sxs-lookup"><span data-stu-id="539be-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="539be-104">Kullanıcı seçimine bağlı olarak, seçili öğe hakkında daha fazla bilgi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="539be-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="539be-105">Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="539be-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="539be-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="539be-106">Example</span></span>  
 <span data-ttu-id="539be-107">Bu örnekte, `People` `Person` sınıflarının bir <xref:System.Collections.ObjectModel.ObservableCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="539be-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="539be-108">Bu `Person` sınıfı üç özellik içerir: `FirstName`, `LastName`ve `HomeTown`, hepsi tür `string`.</span><span class="sxs-lookup"><span data-stu-id="539be-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="539be-109"><xref:System.Windows.Controls.ContentControl>, `Person` bilgilerinin nasıl sunulduğunu tanımlayan aşağıdaki <xref:System.Windows.DataTemplate> kullanır:</span><span class="sxs-lookup"><span data-stu-id="539be-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="539be-110">Aşağıda, örneğin ürettiği bir ekran görüntüsü verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="539be-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="539be-111"><xref:System.Windows.Controls.ContentControl>, seçilen kişinin diğer özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="539be-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="539be-112">![Koleksiyona bağlama](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="539be-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="539be-113">Bu örnekte dikkat etmeniz gereken iki şey şunlardır:</span><span class="sxs-lookup"><span data-stu-id="539be-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="539be-114"><xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır.</span><span class="sxs-lookup"><span data-stu-id="539be-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="539be-115">Her iki bağlamanın <xref:System.Windows.Data.Binding.Path%2A> özellikleri belirtilmedi çünkü her iki denetim de tüm koleksiyon nesnesine bağlanıyor.</span><span class="sxs-lookup"><span data-stu-id="539be-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="539be-116">Bunun çalışması için <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="539be-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="539be-117">Bu özelliğin ayarlanması, seçilen öğenin her zaman <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>olarak ayarlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="539be-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="539be-118">Alternatif olarak, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Data.CollectionViewSource>verileri alırsa, seçim ve para birimini otomatik olarak eşitler.</span><span class="sxs-lookup"><span data-stu-id="539be-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="539be-119">`Person` sınıfının `ToString` yöntemini aşağıdaki şekilde geçersiz kıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="539be-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="539be-120">Varsayılan olarak, <xref:System.Windows.Controls.ListBox> `ToString` çağırır ve bağlantılı koleksiyondaki her nesnenin dize temsilini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="539be-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="539be-121">Bu nedenle, her bir `Person` <xref:System.Windows.Controls.ListBox>ilk adı olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="539be-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="539be-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="539be-122">See also</span></span>

- [<span data-ttu-id="539be-123">Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="539be-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="539be-124">Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="539be-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="539be-125">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="539be-125">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="539be-126">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="539be-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="539be-127">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="539be-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
