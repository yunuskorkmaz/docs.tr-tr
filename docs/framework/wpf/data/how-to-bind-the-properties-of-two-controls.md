---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 0dd7b817b632758cfca8b5c45d88e333510485f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222074"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="56ecc-102">Nasıl yapılır: İki Denetimin Özelliklerini Bağlama</span><span class="sxs-lookup"><span data-stu-id="56ecc-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="56ecc-103">Bu örnekte, başka bir örneği oluşturulan bir denetimin özellik bağlama gösterilmektedir <xref:System.Windows.Data.Binding.ElementName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="56ecc-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ecc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="56ecc-104">Example</span></span>  
 <span data-ttu-id="56ecc-105">Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Canvas> için <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="56ecc-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.</span></span><xref:System.Windows.Controls.ContentControl.Content%2A> <span data-ttu-id="56ecc-106">özelliği bir <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="56ecc-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="56ecc-107">Bu örnek oluşturulduğunda aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="56ecc-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="56ecc-108">![Yeşil bir arka plana sahip bir tuval](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="56ecc-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="56ecc-109">**Not** bağlama hedefi özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56ecc-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="56ecc-110">Daha fazla bilgi için [Data Binding Overview](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="56ecc-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ecc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56ecc-111">See also</span></span>

- [<span data-ttu-id="56ecc-112">Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="56ecc-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="56ecc-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="56ecc-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
