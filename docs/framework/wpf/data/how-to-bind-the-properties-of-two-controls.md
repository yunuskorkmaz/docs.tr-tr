---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974811"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="11a4d-102">Nasıl yapılır: İki Denetimin Özelliklerini Bağlama</span><span class="sxs-lookup"><span data-stu-id="11a4d-102">How to: Bind the Properties of Two Controls</span></span>

<span data-ttu-id="11a4d-103">Bu örnek, bir örneği oluşturulan denetimin özelliğinin, <xref:System.Windows.Data.Binding.ElementName%2A> özelliğini kullanarak başka birine nasıl bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11a4d-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="11a4d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="11a4d-104">Example</span></span>

<span data-ttu-id="11a4d-105">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Panel.Background%2A> özelliğinin bir <xref:System.Windows.Controls.ComboBox>[Selectedidıtem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) özelliğine nasıl bağlanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="11a4d-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the [SelectedItem.Content](xref:System.Windows.Controls.ContentControl.Content%2A) property of a <xref:System.Windows.Controls.ComboBox>:</span></span>

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

<span data-ttu-id="11a4d-106">Bu örnek işlendiğinde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="11a4d-106">When this example is rendered it looks like the following:</span></span>

![Yeşil ve yeşil kare değeri olan bir Birleşik giriş kutusunu gösteren ekran görüntüsü.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="11a4d-108">Bağlama hedefi özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11a4d-108">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="11a4d-109">Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11a4d-109">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11a4d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a4d-110">See also</span></span>

- [<span data-ttu-id="11a4d-111">Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="11a4d-111">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="11a4d-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="11a4d-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
