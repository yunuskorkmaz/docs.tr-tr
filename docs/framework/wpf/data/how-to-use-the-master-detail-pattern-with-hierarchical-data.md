---
title: 'Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e0bbb24b07fdc1c362e2be43d69d189defbc27a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346190"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="cb9ee-102">Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb9ee-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="cb9ee-103">Bu örnek, ana öğe-ayrıntı senaryonun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb9ee-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb9ee-104">Example</span></span>  
 <span data-ttu-id="cb9ee-105">Bu örnekte, `LeagueList` koleksiyonudur `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="cb9ee-106">Her `League` sahip bir `Name` ve koleksiyonu `Divisions`ve her `Division` bir ad ve bir koleksiyonu `Teams`.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="cb9ee-107">Her `Team` bir takım adı vardır.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="cb9ee-108">Örneğin bir ekran görüntüsü aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="cb9ee-109">`Divisions` <xref:System.Windows.Controls.ListBox> Seçimleri otomatik olarak izler `Leagues` <xref:System.Windows.Controls.ListBox> ve karşılık gelen verileri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="cb9ee-110">`Teams` <xref:System.Windows.Controls.ListBox> İzler ve diğer iki seçimleri <xref:System.Windows.Controls.ListBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Bir ana gösteren ekran görüntüsü&#45;ayrıntı senaryo örneği.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="cb9ee-112">Bu örnekte fark etmeye iki şey vardır:</span><span class="sxs-lookup"><span data-stu-id="cb9ee-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="cb9ee-113">Üç <xref:System.Windows.Controls.ListBox> denetimleri aynı kaynağına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="cb9ee-114">Ayarladığınız <xref:System.Windows.Data.Binding.Path%2A> hangi veri düzeyini istediğinizi belirtmek için bağlama özelliğini <xref:System.Windows.Controls.ListBox> görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="cb9ee-115">Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` üzerinde <xref:System.Windows.Controls.ListBox> denetimlerinin izlediğiniz seçimi.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="cb9ee-116">Bu özelliğin ayarlanması sağlar Seçili öğe olarak her zaman ayarlandığından <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="cb9ee-117">Alternatif olarak, <xref:System.Windows.Controls.ListBox> öğesinden veri alır bir <xref:System.Windows.Data.CollectionViewSource>, seçim ve para birimi otomatik olarak eşitler.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="cb9ee-118">Kullanırken tekniği biraz daha farklı olmasına [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="cb9ee-119">Bir örnek için bkz. [hiyerarşik XML verileri ile ana öğe-ayrıntı desenini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="cb9ee-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9ee-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb9ee-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="cb9ee-121">Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cb9ee-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="cb9ee-122">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb9ee-122">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="cb9ee-123">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb9ee-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="cb9ee-124">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="cb9ee-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
