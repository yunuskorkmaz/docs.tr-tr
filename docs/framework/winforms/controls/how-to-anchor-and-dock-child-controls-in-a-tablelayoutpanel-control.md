---
title: 'Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: cfa0d374bf08ab1ea1753ed46e3e87ca177343b6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219860"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="2a5ef-102">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="2a5ef-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="2a5ef-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim destekler <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> kendi alt denetimlerindeki özellikler.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="2a5ef-104">Bir alt denetimin TableLayoutPanel hücredeki hizalamak için</span><span class="sxs-lookup"><span data-stu-id="2a5ef-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="2a5ef-105">Oluşturma bir <xref:System.Windows.Forms.TableLayoutPanel> formunuzdaki denetimi.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="2a5ef-106">Değerini <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> ve <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> özelliklerine **1**.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3.  <span data-ttu-id="2a5ef-107">Oluşturma bir <xref:System.Windows.Forms.Button> denetim <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="2a5ef-108"><xref:System.Windows.Forms.Button> Hücresinin sol üst köşesinin kaplar.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4.  <span data-ttu-id="2a5ef-109">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Left`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="2a5ef-110"><xref:System.Windows.Forms.Button> Hücresinin sol kenarlık ile hizalamak denetimi taşır.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a5ef-111">Bu davranış, diğer kapsayıcı denetimlerin davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="2a5ef-112">Diğer kapsayıcı denetimlerinde ne zaman alt denetimin taşımaz <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanır ve bağlantılı denetim ile üst kapsayıcının sınırları arasındaki uzaklığı zaman sabittir <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5.  <span data-ttu-id="2a5ef-113">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="2a5ef-114"><xref:System.Windows.Forms.Button> Hücresinin sol üst köşedeki kaplaması denetimi taşır.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6.  <span data-ttu-id="2a5ef-115">Yineleme 5. adımı bir değerle `Top, Right` taşımak <xref:System.Windows.Forms.Button> hücrenin sağ üst köşedeki denetimi.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="2a5ef-116">Yineleme değerleriyle `Bottom, Left` ve `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="2a5ef-117">Bir alt denetimin TableLayoutPanel hücredeki uzatmak için</span><span class="sxs-lookup"><span data-stu-id="2a5ef-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="2a5ef-118">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="2a5ef-119"><xref:System.Windows.Forms.Button> Denetimi yeniden boyutlandırılır hücre arasında esnetme için.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a5ef-120">Bu davranış, diğer kapsayıcı denetimlerin davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="2a5ef-121">Diğer kapsayıcı denetimlerinde alt denetim değil ne zaman yeniden boyutlandırılmış <xref:System.Windows.Forms.Control.Anchor%2A> özelliği `Left, Right` veya `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2.  <span data-ttu-id="2a5ef-122">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="2a5ef-123"><xref:System.Windows.Forms.Button> Denetimi yeniden boyutlandırılır hücrenin en altına üstten esnetme için.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3.  <span data-ttu-id="2a5ef-124">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="2a5ef-125"><xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4.  <span data-ttu-id="2a5ef-126">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `None`.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="2a5ef-127"><xref:System.Windows.Forms.Button> Denetimi yeniden boyutlandırıldı ve hücreye ortalanmış.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5.  <span data-ttu-id="2a5ef-128">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="2a5ef-129"><xref:System.Windows.Forms.Button> Hücresinin sol kenarlık ile hizalamak denetimi taşır.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="2a5ef-130"><xref:System.Windows.Forms.Button> Denetiminin genişliğini korur, ancak yükseklik hücreyi dikey olarak doldurmak için boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a5ef-131">Diğer kapsayıcı denetimlerinde oluşan aynı davranış budur.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6.  <span data-ttu-id="2a5ef-132">Değiştirin <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="2a5ef-133"><xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5ef-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a5ef-134">Example</span></span>  
 <span data-ttu-id="2a5ef-135">Beş düğmeden beş ayrı bağlantılı aşağıdaki çizimde <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="2a5ef-136">![TableLayoutPanel Bağlama](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="2a5ef-136">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="2a5ef-137">Aşağıdaki çizimde dört ayrı köşelerini bağlantılı dört düğme <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="2a5ef-138">![TableLayoutPanel Bağlama](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="2a5ef-138">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="2a5ef-139">Üç ayrı bağlama tarafından esnetilmiş üç düğme aşağıdaki çizimde <xref:System.Windows.Forms.TableLayoutPanel> hücreleri.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="2a5ef-140">![TableLayoutPanel Bağlama](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="2a5ef-140">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="2a5ef-141">Aşağıdaki kod örneği, tüm bileşimleri gösterir <xref:System.Windows.Forms.Control.Anchor%2A> özellik değerleri için bir <xref:System.Windows.Forms.Button> denetimine bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a5ef-142">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2a5ef-142">Compiling the Code</span></span>  
 <span data-ttu-id="2a5ef-143">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2a5ef-143">This example requires:</span></span>  
  
-   <span data-ttu-id="2a5ef-144">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2a5ef-145">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2a5ef-145">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2a5ef-146">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-146">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5ef-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a5ef-147">See also</span></span>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="2a5ef-148">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="2a5ef-148">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
