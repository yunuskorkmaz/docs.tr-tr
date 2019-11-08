---
title: 'Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733417"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a><span data-ttu-id="70d66-102">Nasıl yapılır: Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma</span><span class="sxs-lookup"><span data-stu-id="70d66-102">How to: Use the Master-Detail Pattern with Hierarchical XML Data</span></span>
<span data-ttu-id="70d66-103">Bu örnek, XML verileriyle master-detail senaryosunun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70d66-103">This example shows how to implement the master-detail scenario with XML data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70d66-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="70d66-104">Example</span></span>  
 <span data-ttu-id="70d66-105">Bu örnek, [hiyerarşik verilerle ana ayrıntı modelini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)bölümünde AÇıKLANAN örnek xml veri sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="70d66-105">This example is the XML data version of the example discussed in [Use the Master-Detail Pattern with Hierarchical Data](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).</span></span> <span data-ttu-id="70d66-106">Bu örnekte, veriler dosya `League.xml`.</span><span class="sxs-lookup"><span data-stu-id="70d66-106">In this example, the data is from the file `League.xml`.</span></span> <span data-ttu-id="70d66-107">Üçüncü <xref:System.Windows.Controls.ListBox> denetiminin <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliğine bağlayarak ikinci <xref:System.Windows.Controls.ListBox> seçim değişikliklerini nasıl izlediğini aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="70d66-107">Note how the third <xref:System.Windows.Controls.ListBox> control tracks selection changes in the second <xref:System.Windows.Controls.ListBox> by binding to its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a><span data-ttu-id="70d66-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70d66-108">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="70d66-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="70d66-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
