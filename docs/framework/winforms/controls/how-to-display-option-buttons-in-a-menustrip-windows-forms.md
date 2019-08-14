---
title: "Nasıl yapılır: Bir MenuStrip 'te seçenek düğmelerini görüntüleme (Windows Forms)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971932"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="59689-102">Nasıl yapılır: Bir MenuStrip 'te seçenek düğmelerini görüntüleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="59689-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="59689-103">Radyo düğmeleri olarak da bilinen seçenek düğmeleri, kullanıcılar tek seferde yalnızca bir tane seçim yapmak dışında onay kutularına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="59689-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="59689-104">Varsayılan olarak, <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesi davranışı sağlamıyorsa, bir <xref:System.Windows.Forms.MenuStrip> denetimdeki menü öğeleri için seçenek düğmesi davranışını uygulamak üzere özelleştirebileceğiniz onay kutusu davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="59689-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="59689-105">Bir menü öğesinin özelliği olduğunda `true`, kullanıcılar bir onay işaretinin görüntülenmesini değiştirmek için öğeye tıklabilirler. <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A></span><span class="sxs-lookup"><span data-stu-id="59689-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="59689-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliği, öğenin geçerli durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59689-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="59689-107">Temel seçenek düğmesi davranışını uygulamak için, bir öğe seçildiğinde, daha önce seçilen öğenin <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini olarak `false`ayarlamış olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59689-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="59689-108">Aşağıdaki yordamlar, <xref:System.Windows.Forms.ToolStripMenuItem> sınıfını devralan bir sınıfta bu ve ek işlevselliğin nasıl uygulanacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="59689-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="59689-109">Sınıfı, seçenek düğmelerinin seçim davranışını <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> görünümünü sağlamak için ve gibi üyeleri geçersiz kılar. `ToolStripRadioButtonMenuItem`</span><span class="sxs-lookup"><span data-stu-id="59689-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="59689-110">Ayrıca, bu sınıf, üst <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> öğe seçilmediği takdirde alt menüdeki seçeneklerin devre dışı bırakılması için özelliği geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="59689-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="59689-111">Seçenek düğmesi seçimi davranışını uygulamak için</span><span class="sxs-lookup"><span data-stu-id="59689-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="59689-112">Öğe seçimini etkinleştirmek için `true` özelliğini'ebaşlatın.<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A></span><span class="sxs-lookup"><span data-stu-id="59689-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="59689-113">Yeni bir <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> öğe seçildiğinde, daha önce seçilen öğenin seçimini temizlemek için yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="59689-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="59689-114">Daha önce seçilmiş olan bir öğeye tıklanmanın seçimi temizlemez olduğundan emin olmak için yönteminigeçersizkılın.<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A></span><span class="sxs-lookup"><span data-stu-id="59689-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="59689-115">Seçenek düğmesi öğelerinin görünüşünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="59689-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="59689-116">Sınıfını kullanarak varsayılan onay işaretini bir seçenek düğmesiyle değiştirmek için yönteminigeçersizkılın.<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> <xref:System.Windows.Forms.RadioButtonRenderer></span><span class="sxs-lookup"><span data-stu-id="59689-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="59689-117"><xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> Farenin durumunu izlemek<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>için,, ve yöntemlerini geçersiz kılın ve yöntemindoğruseçenekdüğmesidurumunuboyaytığınızdaneminolun.<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A></span><span class="sxs-lookup"><span data-stu-id="59689-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="59689-118">Üst öğe seçilmediğinden bir alt menüdeki seçenekleri devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="59689-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="59689-119"><xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> Öğesinin hem`true` değeri hem de değeri`false`olanbir üst öğesi olduğunda öğenin devre dışı bırakılması için özelliği geçersiz kılın. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A></span><span class="sxs-lookup"><span data-stu-id="59689-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="59689-120">Üst öğenin <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayına abone olmak için yönteminigeçersizkılın.<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A></span><span class="sxs-lookup"><span data-stu-id="59689-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="59689-121">Üst öğe <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayının işleyicisinde, ekranı yeni etkin durumuyla güncelleştirmek için öğeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="59689-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="59689-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="59689-122">Example</span></span>

<span data-ttu-id="59689-123">Aşağıdaki kod örneği, tam `ToolStripRadioButtonMenuItem` sınıfı ve seçenek düğmesi davranışını göstermek için bir `Program` <xref:System.Windows.Forms.Form> sınıfı ve sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="59689-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="59689-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="59689-124">Compiling the Code</span></span>

<span data-ttu-id="59689-125">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="59689-125">This example requires:</span></span>

- <span data-ttu-id="59689-126">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="59689-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="59689-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59689-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="59689-128">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="59689-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="59689-129">Nasıl yapılır: Özel bir ToolStripRenderer uygulama</span><span class="sxs-lookup"><span data-stu-id="59689-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
