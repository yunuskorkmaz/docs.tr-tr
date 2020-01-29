---
title: 'Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735517"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="1e7d4-102">Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1e7d4-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="1e7d4-103">Radyo düğmeleri olarak da bilinen seçenek düğmeleri, kullanıcılar tek seferde yalnızca bir tane seçim yapmak dışında onay kutularına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="1e7d4-104">Varsayılan olarak <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesi davranışı sağlamasa da, sınıf, bir <xref:System.Windows.Forms.MenuStrip> denetimindeki menü öğeleri için seçenek düğmesi davranışını uygulamak üzere özelleştirebileceğiniz onay kutusu davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="1e7d4-105">Bir menü öğesinin <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliği `true`olduğunda, kullanıcılar bir onay işaretinin görüntülenmesini değiştirmek için öğeye tıklabilirler.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="1e7d4-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliği öğenin geçerli durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="1e7d4-107">Temel seçenek düğmesi davranışını uygulamak için, bir öğe seçildiğinde, daha önce seçilen öğenin <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini `false`olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="1e7d4-108">Aşağıdaki yordamlarda, <xref:System.Windows.Forms.ToolStripMenuItem> sınıfını devralan bir sınıfta bu ve ek işlevselliğin nasıl uygulanacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="1e7d4-109">`ToolStripRadioButtonMenuItem` sınıfı, seçenek düğmelerinin seçim davranışını ve görünümünü sağlamak için <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> gibi üyeleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="1e7d4-110">Ayrıca, bu sınıf, üst öğe seçilmediği takdirde bir alt menüdeki seçeneklerin devre dışı bırakılması için <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="1e7d4-111">Seçenek düğmesi seçimi davranışını uygulamak için</span><span class="sxs-lookup"><span data-stu-id="1e7d4-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="1e7d4-112">Öğe seçimini etkinleştirmek için <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true` olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="1e7d4-113">Yeni bir öğe seçildiğinde, daha önce seçilen öğenin seçimini temizlemek için <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="1e7d4-114">Daha önce seçilmiş olan bir öğeyi tıklatmak seçimi temizlemez olduğundan emin olmak için <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="1e7d4-115">Seçenek düğmesi öğelerinin görünüşünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1e7d4-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="1e7d4-116"><xref:System.Windows.Forms.RadioButtonRenderer> sınıfını kullanarak varsayılan onay işaretini bir seçenek düğmesiyle değiştirmek için <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="1e7d4-117">Farenin durumunu izlemek için <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>ve <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> yöntemlerini geçersiz kılın ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yönteminin doğru seçenek düğmesi durumunu boyaytığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="1e7d4-118">Üst öğe seçilmediğinden bir alt menüdeki seçenekleri devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="1e7d4-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="1e7d4-119"><xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini, hem <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> `true` hem de `false`<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> değeri olan bir üst öğe olduğunda öğenin devre dışı bırakılması için geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="1e7d4-120">Üst öğenin <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayına abone olmak için <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="1e7d4-121">Üst öğe <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayına yönelik İşleyicide, ekranı yeni etkin durumuyla güncelleştirmek için öğeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="1e7d4-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e7d4-122">Example</span></span>

<span data-ttu-id="1e7d4-123">Aşağıdaki kod örneği, seçenek düğmesi davranışını göstermek için tam `ToolStripRadioButtonMenuItem` sınıfını ve bir <xref:System.Windows.Forms.Form> sınıfı ve `Program` sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="1e7d4-124">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="1e7d4-124">Compiling the Code</span></span>

<span data-ttu-id="1e7d4-125">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1e7d4-125">This example requires:</span></span>

- <span data-ttu-id="1e7d4-126">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e7d4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e7d4-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="1e7d4-128">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="1e7d4-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="1e7d4-129">Nasıl yapılır: Özel ToolStripRenderer Uygulama</span><span class="sxs-lookup"><span data-stu-id="1e7d4-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
