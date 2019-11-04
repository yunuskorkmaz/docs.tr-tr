---
title: 'Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459085"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="eeea5-102">Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="eeea5-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="eeea5-103">Bu örnek, ana ayrıntı senaryosunun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eeea5-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eeea5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="eeea5-104">Example</span></span>  
 <span data-ttu-id="eeea5-105">Bu örnekte, `LeagueList` bir `Leagues`koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="eeea5-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="eeea5-106">Her `League` bir `Name` ve bir `Divisions`koleksiyonu vardır ve her bir `Division` bir ad ve bir `Teams`koleksiyonu vardır.</span><span class="sxs-lookup"><span data-stu-id="eeea5-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="eeea5-107">Her `Team` bir takım adına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eeea5-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="eeea5-108">Aşağıda, örneğin bir ekran görüntüsü verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eeea5-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="eeea5-109">`Divisions` <xref:System.Windows.Controls.ListBox>, `Leagues` <xref:System.Windows.Controls.ListBox> seçimleri otomatik olarak izler ve ilgili verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="eeea5-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="eeea5-110">`Teams` <xref:System.Windows.Controls.ListBox> diğer iki <xref:System.Windows.Controls.ListBox> denetimlerindeki seçimleri izler.</span><span class="sxs-lookup"><span data-stu-id="eeea5-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Ana&#45;ayrıntı senaryosu örneği gösteren ekran görüntüsü.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="eeea5-112">Bu örnekte dikkat etmeniz gereken iki şey şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eeea5-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="eeea5-113">Üç <xref:System.Windows.Controls.ListBox> denetimi aynı kaynağa bağlanır.</span><span class="sxs-lookup"><span data-stu-id="eeea5-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="eeea5-114"><xref:System.Windows.Controls.ListBox> görüntülenmesini istediğiniz veri düzeyini belirtmek için bağlamanın <xref:System.Windows.Data.Binding.Path%2A> özelliğini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="eeea5-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="eeea5-115"><xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini, izlemekte olduğunuz seçimin <xref:System.Windows.Controls.ListBox> denetimlerinde `true` olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeea5-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="eeea5-116">Bu özelliğin ayarlanması, seçilen öğenin her zaman <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>olarak ayarlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="eeea5-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="eeea5-117">Alternatif olarak, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Data.CollectionViewSource>verileri alırsa, seçim ve para birimini otomatik olarak eşitler.</span><span class="sxs-lookup"><span data-stu-id="eeea5-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="eeea5-118">[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri kullanırken teknik biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="eeea5-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="eeea5-119">Bir örnek için bkz. [HIYERARŞIK XML verileriyle Master-Detail modelini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="eeea5-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeea5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeea5-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="eeea5-121">Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="eeea5-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="eeea5-122">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eeea5-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="eeea5-123">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eeea5-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="eeea5-124">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="eeea5-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
