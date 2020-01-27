---
title: DataGridView denetiminde geçerli hücreyi al ve ayarla
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745666"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="cea51-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="cea51-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="cea51-103"><xref:System.Windows.Forms.DataGridView> etkileşim genellikle, şu anda hangi hücrenin etkin olduğunu programlı bir şekilde keşfetmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cea51-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="cea51-104">Geçerli hücreyi de değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cea51-104">You may also need to change the current cell.</span></span> <span data-ttu-id="cea51-105"><xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği ile bu görevleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cea51-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea51-106">Geçerli hücreyi, <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özelliği `false`olarak ayarlanmış bir satır veya sütunda ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="cea51-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="cea51-107"><xref:System.Windows.Forms.DataGridView> denetiminin seçim moduna bağlı olarak, geçerli hücreyi değiştirmek seçimi değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="cea51-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="cea51-108">Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cea51-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="cea51-109">Geçerli hücreyi programlı bir şekilde almak için</span><span class="sxs-lookup"><span data-stu-id="cea51-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="cea51-110"><xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cea51-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="cea51-111">Geçerli hücreyi programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cea51-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="cea51-112"><xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cea51-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="cea51-113">Aşağıdaki kod örneğinde, geçerli hücre satır 0, sütun 1 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cea51-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cea51-114">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="cea51-114">Compiling the Code</span></span>  
 <span data-ttu-id="cea51-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cea51-115">This example requires:</span></span>  
  
- <span data-ttu-id="cea51-116">`getCurrentCellButton` ve `setCurrentCellButton`adlı denetimleri <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="cea51-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="cea51-117">Görselde C#, her düğmenin <xref:System.Windows.Forms.Control.Click> olaylarını örnek kodda ilişkili olay işleyicisine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cea51-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="cea51-118">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="cea51-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="cea51-119"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="cea51-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea51-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cea51-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cea51-121">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="cea51-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="cea51-122">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="cea51-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
