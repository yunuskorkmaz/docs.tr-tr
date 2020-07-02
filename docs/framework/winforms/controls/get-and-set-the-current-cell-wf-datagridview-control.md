---
title: DataGridView denetiminde geçerli hücreyi al ve ayarla
description: Windows Forms DataGridView denetiminde geçerli hücreyi alarak ve ayarlayarak, şu anda hangi hücrenin etkin olduğunu programlı bir şekilde bulmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622217"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7a425-103">Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7a425-103">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7a425-104">İle etkileşim, <xref:System.Windows.Forms.DataGridView> genellikle hangi hücrenin etkin olduğunu programlı bir şekilde keşfetmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7a425-104">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="7a425-105">Geçerli hücreyi de değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7a425-105">You may also need to change the current cell.</span></span> <span data-ttu-id="7a425-106">Bu görevleri özelliği ile gerçekleştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .</span><span class="sxs-lookup"><span data-stu-id="7a425-106">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a425-107">Özelliği olarak ayarlanmış bir satır veya sütundaki geçerli hücreyi ayarlayamazsınız <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="7a425-107">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="7a425-108"><xref:System.Windows.Forms.DataGridView>Denetimin seçim moduna bağlı olarak, geçerli hücreyi değiştirmek seçimi değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="7a425-108">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="7a425-109">Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7a425-109">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="7a425-110">Geçerli hücreyi programlı bir şekilde almak için</span><span class="sxs-lookup"><span data-stu-id="7a425-110">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="7a425-111"><xref:System.Windows.Forms.DataGridView>Denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a425-111">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="7a425-112">Geçerli hücreyi programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7a425-112">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="7a425-113"><xref:System.Windows.Forms.DataGridView.CurrentCell%2A>Denetimin özelliğini ayarlayın <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="7a425-113">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7a425-114">Aşağıdaki kod örneğinde, geçerli hücre satır 0, sütun 1 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7a425-114">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a425-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7a425-115">Compiling the Code</span></span>  
 <span data-ttu-id="7a425-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7a425-116">This example requires:</span></span>  
  
- <span data-ttu-id="7a425-117"><xref:System.Windows.Forms.Button>ve adlı `getCurrentCellButton` denetimler `setCurrentCellButton` .</span><span class="sxs-lookup"><span data-stu-id="7a425-117"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="7a425-118">Visual C# ' ta, <xref:System.Windows.Forms.Control.Click> her düğmenin olayını örnek kodda ilişkili olay işleyicisine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a425-118">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="7a425-119"><xref:System.Windows.Forms.DataGridView>Adlı bir denetim `dataGridView1` .</span><span class="sxs-lookup"><span data-stu-id="7a425-119">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="7a425-120"><xref:System?displayProperty=nameWithType>Ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="7a425-120">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a425-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a425-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7a425-122">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="7a425-122">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="7a425-123">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="7a425-123">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
