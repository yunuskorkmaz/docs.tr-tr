---
title: "Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e392b47682d1bf53dc31073920bdf212fb7d997
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="df6b2-102">Nasıl yapılır: Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="df6b2-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="df6b2-103">Bu örnek ana-ayrıntı senaryosunun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="df6b2-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df6b2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="df6b2-104">Example</span></span>  
 <span data-ttu-id="df6b2-105">Bu örnekte, `LeagueList` koleksiyonudur `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="df6b2-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="df6b2-106">Her `League` sahip bir `Name` ve koleksiyonu `Divisions`ve her `Division` bir ad ve bir koleksiyonu vardır `Teams`.</span><span class="sxs-lookup"><span data-stu-id="df6b2-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="df6b2-107">Her `Team` bir takım adı vardır.</span><span class="sxs-lookup"><span data-stu-id="df6b2-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="df6b2-108">Örneğin bir ekran görüntüsü verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df6b2-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="df6b2-109">`Divisions` <xref:System.Windows.Controls.ListBox> Otomatik olarak seçimleri izleyen `Leagues` <xref:System.Windows.Controls.ListBox> ve karşılık gelen verileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df6b2-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="df6b2-110">`Teams` <xref:System.Windows.Controls.ListBox> Diğer iki seçimleri izler <xref:System.Windows.Controls.ListBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="df6b2-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="df6b2-111">![Ana &#45; ayrıntı örneği](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="df6b2-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="df6b2-112">Bu örnekte fark için iki şey vardır:</span><span class="sxs-lookup"><span data-stu-id="df6b2-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="df6b2-113">Üç <xref:System.Windows.Controls.ListBox> denetimleri aynı kaynağa bağlanır.</span><span class="sxs-lookup"><span data-stu-id="df6b2-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="df6b2-114">Ayarladığınız <xref:System.Windows.Data.Binding.Path%2A> hangi düzeyde verileri istediğiniz belirtmek için bağlama özelliğini <xref:System.Windows.Controls.ListBox> görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="df6b2-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="df6b2-115">Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğine `true` üzerinde <xref:System.Windows.Controls.ListBox> denetimlerinin izlediğiniz seçim.</span><span class="sxs-lookup"><span data-stu-id="df6b2-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="df6b2-116">Bu özelliği ayarlamak sağlar Seçili öğe olarak her zaman ayarlanır <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="df6b2-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="df6b2-117">Alternatif olarak, varsa <xref:System.Windows.Controls.ListBox> verilerinden alır bir <xref:System.Windows.Data.CollectionViewSource>, seçimi ve para birimi otomatik olarak eşitler.</span><span class="sxs-lookup"><span data-stu-id="df6b2-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="df6b2-118">Kullanırken teknik biraz farklıdır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.</span><span class="sxs-lookup"><span data-stu-id="df6b2-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="df6b2-119">Bir örnek için bkz: [hiyerarşik XML veriler ile ana-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="df6b2-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6b2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df6b2-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="df6b2-121">Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="df6b2-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="df6b2-122">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="df6b2-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="df6b2-123">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="df6b2-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="df6b2-124">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="df6b2-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
