---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933695"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c2b40-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c2b40-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c2b40-103">İle etkileşim, <xref:System.Windows.Forms.DataGridView> genellikle hangi hücrenin etkin olduğunu programlı bir şekilde keşfetmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c2b40-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="c2b40-104">Geçerli hücreyi de değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c2b40-104">You may also need to change the current cell.</span></span> <span data-ttu-id="c2b40-105">Bu görevleri <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği ile gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2b40-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2b40-106"><xref:System.Windows.Forms.DataGridViewBand.Visible%2A> Özelliği olarak`false`ayarlanmış bir satır veya sütundaki geçerli hücreyi ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c2b40-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="c2b40-107"><xref:System.Windows.Forms.DataGridView> Denetimin seçim moduna bağlı olarak, geçerli hücreyi değiştirmek seçimi değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c2b40-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="c2b40-108">Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c2b40-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="c2b40-109">Geçerli hücreyi programlı bir şekilde almak için</span><span class="sxs-lookup"><span data-stu-id="c2b40-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="c2b40-110"><xref:System.Windows.Forms.DataGridView> Denetimin<xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c2b40-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="c2b40-111">Geçerli hücreyi programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c2b40-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="c2b40-112"><xref:System.Windows.Forms.DataGridView> Denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c2b40-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c2b40-113">Aşağıdaki kod örneğinde, geçerli hücre satır 0, sütun 1 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c2b40-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2b40-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c2b40-114">Compiling the Code</span></span>  
 <span data-ttu-id="c2b40-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c2b40-115">This example requires:</span></span>  
  
- <span data-ttu-id="c2b40-116"><xref:System.Windows.Forms.Button>`getCurrentCellButton` ve`setCurrentCellButton`adlı denetimler.</span><span class="sxs-lookup"><span data-stu-id="c2b40-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="c2b40-117">Görselde C#, her düğmenin olayını örnek <xref:System.Windows.Forms.Control.Click> kodda ilişkili olay işleyicisine bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2b40-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="c2b40-118"><xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.</span><span class="sxs-lookup"><span data-stu-id="c2b40-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="c2b40-119"><xref:System?displayProperty=nameWithType> Ve<xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c2b40-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b40-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2b40-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c2b40-121">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c2b40-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="c2b40-122">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="c2b40-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
