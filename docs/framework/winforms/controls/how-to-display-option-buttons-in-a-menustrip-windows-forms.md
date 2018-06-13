---
title: 'Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: da2bb7edceaf83aa5178618fd4098631d65a7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538035"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="50daf-102">Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="50daf-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="50daf-103">Seçenek düğmeleri, olarak da bilinen radyo düğmeleri, kullanıcılar yalnızca birer birer seçebilirsiniz onay kutularını benzerdir.</span><span class="sxs-lookup"><span data-stu-id="50daf-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="50daf-104">Ancak varsayılan olarak <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesi davranışı sağlamaz, sınıf menü öğeleri için seçenek düğmesi davranışı uygulamak için özelleştirebileceğiniz onay kutusu davranışı sağlamak bir <xref:System.Windows.Forms.MenuStrip> denetim.</span><span class="sxs-lookup"><span data-stu-id="50daf-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="50daf-105">Zaman <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> menü öğesi özelliği `true`, kullanıcıların bir onay işareti görüntüsünü geçiş yapmak için öğeyi tıklatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50daf-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="50daf-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliği öğesi geçerli durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="50daf-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="50daf-107">Temel seçenek düğmesi davranışı uygulamak için bir öğe seçildiğinde, ayarladığınız sağlamanız gerekir. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliği daha önce seçilen öğeye için `false`.</span><span class="sxs-lookup"><span data-stu-id="50daf-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="50daf-108">Aşağıdaki yordamlar bu uygulamak nasıl açıklar ve ek işlevsellik devralan bir sınıf <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="50daf-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="50daf-109">`ToolStripRadioButtonMenuItem` Sınıfı üyeleri gibi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> seçme davranışı ve seçenek düğmeleri görünümünü sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="50daf-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="50daf-110">Ayrıca, bu sınıfı geçersiz kılan <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> üst öğesi seçmediğiniz sürece bir alt menüsündeki Seçenekler özelliğini devre dışı.</span><span class="sxs-lookup"><span data-stu-id="50daf-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="50daf-111">Seçenek düğmesi seçimi davranışı uygulamak için</span><span class="sxs-lookup"><span data-stu-id="50daf-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="50daf-112">Initialize <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğine `true` öğe seçimi etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="50daf-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="50daf-113">Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> yeni bir öğe seçildiğinde daha önce seçilen öğenin seçimini yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50daf-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="50daf-114">Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> o zaten seçilmiş bir öğeyi tıklatarak emin olmak için yöntem değil seçimi temizleyin.</span><span class="sxs-lookup"><span data-stu-id="50daf-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="50daf-115">Seçenek düğmesi öğelerinin görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="50daf-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="50daf-116">Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemi kullanarak bir seçenek düğmesine sahip varsayılan onay işareti yerine <xref:System.Windows.Forms.RadioButtonRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="50daf-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="50daf-117">Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, ve <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> fare durumunu izlemek ve emin olmak için yöntemler <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemi doğru seçenek düğmesi durumu boyar.</span><span class="sxs-lookup"><span data-stu-id="50daf-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="50daf-118">Üst öğe seçilmediğinde menüdeki seçenekleri devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="50daf-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="50daf-119">Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği böylece her ikisi de sahip bir üst öğesi varsa öğesi devre dışı bir <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> değerini `true` ve <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> değerini `false`.</span><span class="sxs-lookup"><span data-stu-id="50daf-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="50daf-120">Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> abone olmak için yöntem <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> üst öğenin olay.</span><span class="sxs-lookup"><span data-stu-id="50daf-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="50daf-121">Üst öğesi için işleyicisinde <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olay, yeni etkin durumu ile görüntü güncellenecek öğe geçersiz.</span><span class="sxs-lookup"><span data-stu-id="50daf-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="50daf-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="50daf-122">Example</span></span>  
 <span data-ttu-id="50daf-123">Aşağıdaki kod örneğinde eksiksiz `ToolStripRadioButtonMenuItem` sınıfı ve bir <xref:System.Windows.Forms.Form> sınıfı ve `Program` sınıfı seçenek düğmesi davranışı sergiler.</span><span class="sxs-lookup"><span data-stu-id="50daf-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50daf-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="50daf-124">Compiling the Code</span></span>  
 <span data-ttu-id="50daf-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="50daf-125">This example requires:</span></span>  
  
-   <span data-ttu-id="50daf-126">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="50daf-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50daf-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50daf-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="50daf-128">MenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="50daf-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="50daf-129">Nasıl yapılır: Özel ToolStripRenderer Uygulama</span><span class="sxs-lookup"><span data-stu-id="50daf-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
