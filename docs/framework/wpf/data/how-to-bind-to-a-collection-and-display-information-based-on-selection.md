---
title: 'Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme'
description: Bir koleksiyona nasıl bağlanılacağını ve Windows Presentation Foundation (WPF) içindeki seçime göre bilgi görüntülemeyi öğrenmek için bu örneği izleyin.
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619617"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="a36b4-103">Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a36b4-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="a36b4-104">Basit bir ana ayrıntı senaryosunda, gibi bir veri bağladınız <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="a36b4-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="a36b4-105">Kullanıcı seçimine bağlı olarak, seçili öğe hakkında daha fazla bilgi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a36b4-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="a36b4-106">Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a36b4-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a36b4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a36b4-107">Example</span></span>  
 <span data-ttu-id="a36b4-108">Bu örnekte, `People` <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="a36b4-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="a36b4-109">Bu `Person` sınıf üç özellik içerir: `FirstName` , `LastName` , ve `HomeTown` , hepsi türü `string` .</span><span class="sxs-lookup"><span data-stu-id="a36b4-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="a36b4-110">, <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.DataTemplate> Bir öğesinin bilgisinin nasıl sunulduğunu tanımlayan aşağıdakileri kullanır `Person` :</span><span class="sxs-lookup"><span data-stu-id="a36b4-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="a36b4-111">Aşağıda, örneğin ürettiği bir ekran görüntüsü verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a36b4-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="a36b4-112">, <xref:System.Windows.Controls.ContentControl> Seçilen kişinin diğer özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a36b4-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="a36b4-113">![Koleksiyona bağlama](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="a36b4-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="a36b4-114">Bu örnekte dikkat etmeniz gereken iki şey şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a36b4-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="a36b4-115"><xref:System.Windows.Controls.ListBox>Ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır.</span><span class="sxs-lookup"><span data-stu-id="a36b4-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="a36b4-116">Her iki <xref:System.Windows.Data.Binding.Path%2A> Denetim de tüm koleksiyon nesnesine bağladığından her iki bağlamanın özellikleri belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="a36b4-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="a36b4-117"><xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>Bunun çalışması için özelliği olarak ayarlamanız gerekir `true` .</span><span class="sxs-lookup"><span data-stu-id="a36b4-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="a36b4-118">Bu özelliğin ayarlanması, seçilen öğenin her zaman olarak ayarlanmasını sağlar <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="a36b4-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="a36b4-119">Alternatif olarak, <xref:System.Windows.Controls.ListBox> verileri bir öğesinden alırsa, <xref:System.Windows.Data.CollectionViewSource> seçim ve para birimini otomatik olarak eşitler.</span><span class="sxs-lookup"><span data-stu-id="a36b4-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="a36b4-120">`Person`Sınıfının yöntemi aşağıdaki şekilde geçersiz kıldığını unutmayın `ToString` .</span><span class="sxs-lookup"><span data-stu-id="a36b4-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="a36b4-121">Varsayılan olarak, <xref:System.Windows.Controls.ListBox> çağırır `ToString` ve, bağlantılı koleksiyondaki her nesnenin dize gösterimini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a36b4-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="a36b4-122">Bunun nedeni, her birinin `Person` ' de ilk ad olarak görüntülenmesidir <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="a36b4-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="a36b4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a36b4-123">See also</span></span>

- [<span data-ttu-id="a36b4-124">Hiyerarşik verilerle ana ayrıntı modelini kullanın</span><span class="sxs-lookup"><span data-stu-id="a36b4-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="a36b4-125">Hiyerarşik XML verileriyle ana ayrıntı modelini kullanın</span><span class="sxs-lookup"><span data-stu-id="a36b4-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="a36b4-126">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a36b4-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a36b4-127">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a36b4-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="a36b4-128">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a36b4-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
