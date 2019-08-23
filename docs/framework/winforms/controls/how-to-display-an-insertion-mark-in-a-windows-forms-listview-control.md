---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: f5de00fd41b24fc1a7f1ff4484c3a126e98952a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967828"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="934f8-102">Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="934f8-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="934f8-103"><xref:System.Windows.Forms.ListView> Denetimdeki ekleme işareti kullanıcılara sürüklenen öğelerin ekleneceği noktayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="934f8-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="934f8-104">Bir Kullanıcı bir öğeyi diğer iki öğe arasındaki bir noktaya sürüklendiğinde, ekleme işareti öğenin beklenen yeni konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="934f8-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="934f8-105">Ekleme işareti özelliği yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="934f8-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="934f8-106">Önceki işletim sistemlerinde, ekleme işaretiyle ilgili tüm kodlar etkisizdir ve ekleme işareti görünmez.</span><span class="sxs-lookup"><span data-stu-id="934f8-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="934f8-107">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="934f8-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="934f8-108">Aşağıdaki görüntüde bir ekleme işareti gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="934f8-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="934f8-109">![ListView ekleme işaretini gösteren ekran görüntüsü.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="934f8-109">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="934f8-110">Aşağıdaki kod örneğinde, bu özelliğin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="934f8-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="934f8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="934f8-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="934f8-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="934f8-112">Compiling the Code</span></span>  
 <span data-ttu-id="934f8-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="934f8-113">This example requires:</span></span>  
  
- <span data-ttu-id="934f8-114">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="934f8-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934f8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="934f8-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="934f8-116">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="934f8-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="934f8-117">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="934f8-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="934f8-118">İzlenecek yol: Windows Forms bir sürükle ve bırak Işlemi gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="934f8-118">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
