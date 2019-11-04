---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459175"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="11efc-102">Nasıl yapılır: İki Denetimin Özelliklerini Bağlama</span><span class="sxs-lookup"><span data-stu-id="11efc-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="11efc-103">Bu örnek, bir örneği oluşturulan denetimin özelliğinin, <xref:System.Windows.Data.Binding.ElementName%2A> özelliğini kullanarak başka birine nasıl bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11efc-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11efc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="11efc-104">Example</span></span>  
 <span data-ttu-id="11efc-105">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Panel.Background%2A> özelliğinin <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>nasıl bağlanacağını gösterir.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="11efc-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="11efc-106"><xref:System.Windows.Controls.ComboBox>özelliği:</span><span class="sxs-lookup"><span data-stu-id="11efc-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="11efc-107">Bu örnek işlendiğinde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="11efc-107">When this example is rendered it looks like the following:</span></span>  
  
![Yeşil ve yeşil kare değeri olan bir Birleşik giriş kutusunu gösteren ekran görüntüsü.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="11efc-109">Bağlama hedefi özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11efc-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="11efc-110">Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11efc-110">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11efc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11efc-111">See also</span></span>

- [<span data-ttu-id="11efc-112">Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="11efc-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="11efc-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="11efc-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
