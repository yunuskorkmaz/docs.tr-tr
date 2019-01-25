---
title: 'Nasıl yapılır: Alma ve Windows Forms DataGridView denetiminde geçerli hücreyi ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 2508551cd4bcb056d1e746b2dc962c4500093ea5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495610"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f8606-102">Nasıl yapılır: Alma ve Windows Forms DataGridView denetiminde geçerli hücreyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f8606-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f8606-103">Etkileşim <xref:System.Windows.Forms.DataGridView> genellikle hangi hücre o anda etkin olan program aracılığıyla bulmak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8606-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="f8606-104">Geçerli hücreyi değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f8606-104">You may also need to change the current cell.</span></span> <span data-ttu-id="f8606-105">Bu görevleri gerçekleştirebileceğiniz <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8606-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8606-106">Geçerli hücreyi bir satır veya olan sütunda ayarlanamaz, <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="f8606-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="f8606-107">Yapılandırmanıza bağlı olarak <xref:System.Windows.Forms.DataGridView> denetiminin seçim modunu, geçerli hücreyi değiştirme seçimi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8606-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="f8606-108">Daha fazla bilgi için [Windows Forms DataGridView denetimindeki seçim modları](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f8606-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="f8606-109">Geçerli hücreyi programlı olarak almak için</span><span class="sxs-lookup"><span data-stu-id="f8606-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="f8606-110">Kullanım <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8606-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="f8606-111">Geçerli hücreyi program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="f8606-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="f8606-112">Ayarlama <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f8606-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f8606-113">Aşağıdaki kod örneğinde, 0, sütun 1 satır için geçerli hücreyi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f8606-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8606-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f8606-114">Compiling the Code</span></span>  
 <span data-ttu-id="f8606-115">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8606-115">This example requires:</span></span>  
  
-   <span data-ttu-id="f8606-116"><xref:System.Windows.Forms.Button> adlarında `getCurrentCellButton` ve `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="f8606-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="f8606-117">Görselde C#, iliştirmeniz gerekir <xref:System.Windows.Forms.Control.Click> her düğme için ilişkili olay işleyicisine kod örneği için olayları.</span><span class="sxs-lookup"><span data-stu-id="f8606-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="f8606-118">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f8606-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="f8606-119">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="f8606-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8606-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8606-120">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f8606-121">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f8606-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="f8606-122">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="f8606-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
