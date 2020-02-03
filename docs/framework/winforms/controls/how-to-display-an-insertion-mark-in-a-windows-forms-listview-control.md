---
title: ListView denetiminde ekleme Işareti görüntüle
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
ms.openlocfilehash: eeae51223a21baaf4d2412de2ce11d0c6cbcae27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742212"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="200cf-102">Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="200cf-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="200cf-103"><xref:System.Windows.Forms.ListView> denetimindeki ekleme işareti kullanıcılara sürüklenen öğelerin ekleneceği noktayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="200cf-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="200cf-104">Bir Kullanıcı bir öğeyi diğer iki öğe arasındaki bir noktaya sürüklendiğinde, ekleme işareti öğenin beklenen yeni konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="200cf-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
 <span data-ttu-id="200cf-105">Aşağıdaki görüntüde bir ekleme işareti gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="200cf-105">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="200cf-106">![ListView ekleme işaretini gösteren ekran görüntüsü.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="200cf-106">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="200cf-107">Aşağıdaki kod örneğinde, bu özelliğin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="200cf-107">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="200cf-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="200cf-108">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="200cf-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="200cf-109">Compiling the Code</span></span>  
 <span data-ttu-id="200cf-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="200cf-110">This example requires:</span></span>  
  
- <span data-ttu-id="200cf-111">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="200cf-111">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200cf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="200cf-112">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="200cf-113">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="200cf-113">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="200cf-114">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="200cf-114">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="200cf-115">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="200cf-115">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
