---
title: ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 88b6a6023fbfdd8fa315fcd434357626ea69a9ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537774"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="a0174-102">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="a0174-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="a0174-103"><xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ListBox> denetimleri benzer davranışları sahiptir ve bazı durumlarda değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0174-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="a0174-104">Bir ya da başka bir görev için daha uygun olduğunda zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="a0174-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="a0174-105">Genellikle, önerilen seçenek listesini yoktur ve listede nedir için giriş sınırlama getirmek istediğinizde bir liste kutusu uygun olduğunda bir birleşik giriş kutusu uygundur.</span><span class="sxs-lookup"><span data-stu-id="a0174-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="a0174-106">Birleşik giriş kutusu bir metin kutusu alanı içerdiğinden, listede olmayan seçimler yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0174-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="a0174-107">Özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="a0174-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="a0174-108">Bu durumda, ilk harfi yazarsanız denetimi bir öğe seçin.</span><span class="sxs-lookup"><span data-stu-id="a0174-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="a0174-109">Ayrıca, birleşik giriş kutuları, bir form üzerinde alanı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a0174-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="a0174-110">Aşağı oka kullanıcı kadar tam listesi görüntülenmeyen için birleşik giriş kutusu kolayca bir liste kutusu değil nerelerde küçük bir alanda uygun olamaz.</span><span class="sxs-lookup"><span data-stu-id="a0174-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="a0174-111">Bir özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ComboBoxStyle.Simple>: tam listesi görüntülenir ve birleşik giriş kutusu bir liste kutusu olduğundan daha fazla yer alır.</span><span class="sxs-lookup"><span data-stu-id="a0174-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0174-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0174-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="a0174-113">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="a0174-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="a0174-114">Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama</span><span class="sxs-lookup"><span data-stu-id="a0174-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="a0174-115">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="a0174-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
