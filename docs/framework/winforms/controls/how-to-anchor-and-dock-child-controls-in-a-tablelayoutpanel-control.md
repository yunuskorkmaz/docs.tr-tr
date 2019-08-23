---
title: 'Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme'
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
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922816"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="fd63c-102">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="fd63c-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="fd63c-103">Denetim, <xref:System.Windows.Forms.Control.Anchor%2A> alt denetimlerinde ve <xref:System.Windows.Forms.Control.Dock%2A> özelliklerini destekler. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="fd63c-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="fd63c-104">TableLayoutPanel hücresindeki bir alt denetimi hizalamak için</span><span class="sxs-lookup"><span data-stu-id="fd63c-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="fd63c-105">Formunuzda bir <xref:System.Windows.Forms.TableLayoutPanel> denetim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fd63c-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="fd63c-106"><xref:System.Windows.Forms.TableLayoutPanel> Denetimin ve özelliklerinin<xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> değerini 1 olarak ayarlayın. <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="fd63c-107"><xref:System.Windows.Forms.TableLayoutPanel> Denetimde bir <xref:System.Windows.Forms.Button> denetim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fd63c-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="fd63c-108">Hücrenin sol üst köşesini kaplar.<xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="fd63c-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="fd63c-109"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Left`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="fd63c-110">Denetim <xref:System.Windows.Forms.Button> , hücrenin sol kenarlığına göre hizalanacak şekilde gider.</span><span class="sxs-lookup"><span data-stu-id="fd63c-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd63c-111">Bu davranış, diğer kapsayıcı denetimlerinin davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="fd63c-112">Diğer kapsayıcı denetimlerinde, <xref:System.Windows.Forms.Control.Anchor%2A> özellik ayarlandığında alt denetim hareket etmez ve bağlantılı denetim ile üst kapsayıcının sınırı arasındaki mesafe, <xref:System.Windows.Forms.Control.Anchor%2A> özelliğin ayarlandığı zamanda düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="fd63c-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="fd63c-113"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Top, Left`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="fd63c-114">Denetim <xref:System.Windows.Forms.Button> , hücrenin sol üst köşesinin kaplamasına karşı gider.</span><span class="sxs-lookup"><span data-stu-id="fd63c-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="fd63c-115"><xref:System.Windows.Forms.Button> Denetimi hücrenin sağ üst köşesine taşımak `Top, Right` için değeri olan 5. adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="fd63c-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="fd63c-116">`Bottom, Left` Ve`Bottom, Right`değerleri ile tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="fd63c-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="fd63c-117">TableLayoutPanel hücresindeki bir alt denetimi uzatmak için</span><span class="sxs-lookup"><span data-stu-id="fd63c-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="fd63c-118"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Left, Right`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="fd63c-119"><xref:System.Windows.Forms.Button> Denetim hücre üzerinde uzatmak için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd63c-120">Bu davranış, diğer kapsayıcı denetimlerinin davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="fd63c-121">Diğer kapsayıcı denetimlerinde, <xref:System.Windows.Forms.Control.Anchor%2A> özelliği veya `Top, Bottom`olarak `Left, Right` ayarlandığında alt denetim yeniden boyutlandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="fd63c-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="fd63c-122"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Top, Bottom`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="fd63c-123"><xref:System.Windows.Forms.Button> Denetim, hücrenin en üstünden aşağı doğru uzatmak için yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="fd63c-124"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`Top, Bottom, Left, Right`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="fd63c-125"><xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="fd63c-126"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak`None`değiştirin. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="fd63c-127"><xref:System.Windows.Forms.Button> Denetim yeniden boyutlandırıldı ve hücrede ortalandı.</span><span class="sxs-lookup"><span data-stu-id="fd63c-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="fd63c-128"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak<xref:System.Windows.Forms.DockStyle.Left>değiştirin. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="fd63c-129">Denetim <xref:System.Windows.Forms.Button> , hücrenin sol kenarlığına göre hizalanacak şekilde gider.</span><span class="sxs-lookup"><span data-stu-id="fd63c-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="fd63c-130"><xref:System.Windows.Forms.Button> Denetim genişliğini korur, ancak yüksekliği hücreyi dikey olarak dolduracak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd63c-131">Bu, diğer kapsayıcı denetimlerinde gerçekleşen davranıştır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="fd63c-132"><xref:System.Windows.Forms.Button> Denetimin özelliğinin değerini olarak<xref:System.Windows.Forms.DockStyle.Fill>değiştirin. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="fd63c-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="fd63c-133"><xref:System.Windows.Forms.Button> Denetim hücreyi dolduracak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fd63c-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd63c-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd63c-134">Example</span></span>  
 <span data-ttu-id="fd63c-135">Aşağıdaki çizimde beş ayrı <xref:System.Windows.Forms.TableLayoutPanel> hücrede sabitlenmiş beş düğme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd63c-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="fd63c-136">![TableLayoutPanel sabitleme](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="fd63c-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="fd63c-137">Aşağıdaki çizimde dört ayrı <xref:System.Windows.Forms.TableLayoutPanel> hücrenin köşelerinde sabitlenmiş dört düğme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd63c-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="fd63c-138">![TableLayoutPanel sabitleme](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="fd63c-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="fd63c-139">Aşağıdaki çizimde üç ayrı <xref:System.Windows.Forms.TableLayoutPanel> hücrede sabitleme ile uzatılmış üç düğme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd63c-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="fd63c-140">![TableLayoutPanel sabitleme](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="fd63c-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="fd63c-141">Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.TableLayoutPanel> denetimdeki <xref:System.Windows.Forms.Button> denetim için özellik değerlerinin tüm birleşimlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd63c-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd63c-142">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fd63c-142">Compiling the Code</span></span>  
 <span data-ttu-id="fd63c-143">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fd63c-143">This example requires:</span></span>  
  
- <span data-ttu-id="fd63c-144">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="fd63c-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd63c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd63c-145">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="fd63c-146">TableLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="fd63c-146">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
