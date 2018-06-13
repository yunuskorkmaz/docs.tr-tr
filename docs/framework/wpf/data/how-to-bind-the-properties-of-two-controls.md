---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 02e71bfcc41fc3d256ea95381ed27d36b289b8f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555587"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="4e193-102">Nasıl yapılır: İki Denetimin Özelliklerini Bağlama</span><span class="sxs-lookup"><span data-stu-id="4e193-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="4e193-103">Bu örnek bir örneklenen denetim özelliği, başka bir bağlama gösterilmektedir <xref:System.Windows.Data.Binding.ElementName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4e193-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e193-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e193-104">Example</span></span>  
 <span data-ttu-id="4e193-105">Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Canvas> için <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="4e193-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="4e193-106">özelliği bir <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="4e193-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="4e193-107">Bu örnek işlendiğinde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="4e193-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="4e193-108">![Yeşil arka plana sahip bir tuval](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="4e193-108">![A canvas with a green background](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="4e193-109">**Not** bağlama hedef özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e193-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="4e193-110">Daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e193-110">For more information, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e193-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e193-111">See Also</span></span>  
 [<span data-ttu-id="4e193-112">Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="4e193-112">Specify the Binding Source</span></span>](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [<span data-ttu-id="4e193-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="4e193-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
