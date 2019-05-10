---
title: 'Nasıl yapılır: İki Denetimin Özelliklerini Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754053"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="11870-102">Nasıl yapılır: İki Denetimin Özelliklerini Bağlama</span><span class="sxs-lookup"><span data-stu-id="11870-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="11870-103">Bu örnekte, başka bir örneği oluşturulan bir denetimin özellik bağlama gösterilmektedir <xref:System.Windows.Data.Binding.ElementName%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="11870-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11870-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="11870-104">Example</span></span>  
 <span data-ttu-id="11870-105">Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Canvas> için <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="11870-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="11870-106">özelliği bir <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="11870-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="11870-107">Bu örnek oluşturulduğunda aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="11870-107">When this example is rendered it looks like the following:</span></span>  
  
![Bir birleşik giriş kutusu seçiliyken yeşil değeri ve yeşil bir kare gösteren ekran görüntüsü.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="11870-109">Bağlamanın hedef özelliği (Bu örnekte, <xref:System.Windows.Controls.Panel.Background%2A> özelliği) bir bağımlılık özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11870-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="11870-110">Daha fazla bilgi için [Data Binding Overview](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11870-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11870-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11870-111">See also</span></span>

- [<span data-ttu-id="11870-112">Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="11870-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="11870-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="11870-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
