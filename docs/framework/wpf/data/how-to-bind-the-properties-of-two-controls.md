---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: f3355969d0f12f0f3ed9b49bdb7efa6913c5e4c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372106"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="c17fc-102">Nasıl yapılır: İki Denetimin Özelliklerini Bağlama</span><span class="sxs-lookup"><span data-stu-id="c17fc-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="c17fc-103">Bu örnekte, başka bir örneği oluşturulan bir denetimin özellik bağlama gösterilmektedir <xref:System.Windows.Data.Binding.ElementName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c17fc-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c17fc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c17fc-104">Example</span></span>  
 <span data-ttu-id="c17fc-105">Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Canvas> için <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="c17fc-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="c17fc-106">özelliği bir <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="c17fc-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="c17fc-107">Bu örnek oluşturulduğunda aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="c17fc-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="c17fc-108">![Yeşil bir arka plana sahip bir tuval](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="c17fc-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="c17fc-109">**Not** bağlama hedefi özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c17fc-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="c17fc-110">Daha fazla bilgi için [Data Binding Overview](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c17fc-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17fc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c17fc-111">See also</span></span>
- [<span data-ttu-id="c17fc-112">Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="c17fc-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="c17fc-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c17fc-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
