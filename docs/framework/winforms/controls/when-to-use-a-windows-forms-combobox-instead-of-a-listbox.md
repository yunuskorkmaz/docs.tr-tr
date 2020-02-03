---
title: ComboBox ve ListBox
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
ms.openlocfilehash: 7087760a393bb58d83d899c1741c745fb28585bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739932"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="12acc-102">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="12acc-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="12acc-103"><xref:System.Windows.Forms.ComboBox> ve <xref:System.Windows.Forms.ListBox> denetimleri benzer davranışlara sahiptir ve bazı durumlarda bu şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="12acc-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="12acc-104">Ancak, bir veya diğeri bir göreve daha uygun olduğunda zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="12acc-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="12acc-105">Genellikle, bir açılan kutu, önerilen seçeneklerin bir listesi olduğunda uygundur ve girişi listede olacak şekilde sınırlamak istediğinizde bir liste kutusu uygundur.</span><span class="sxs-lookup"><span data-stu-id="12acc-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="12acc-106">Bir Birleşik giriş kutusu metin kutusu alanı içeriyorsa, listede bulunmayan seçimler içine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="12acc-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="12acc-107">Bu, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğinin <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>olarak ayarlandığı durumdur.</span><span class="sxs-lookup"><span data-stu-id="12acc-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="12acc-108">Bu durumda, ilk harfini yazarsanız denetim bir öğe seçer.</span><span class="sxs-lookup"><span data-stu-id="12acc-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="12acc-109">Ayrıca, Birleşik giriş kutuları bir formdaki alanı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="12acc-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="12acc-110">Kullanıcı aşağı oka tıklaana kadar tam liste görüntülenmediği için, bir açılan kutu bir liste kutusunun uygun olmadığı küçük bir alana kolayca uyum sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="12acc-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="12acc-111">Bir özel durum, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğinin <xref:System.Windows.Forms.ComboBoxStyle.Simple>olarak ayarlandığı durumdur: tam liste görüntülenir ve Birleşik giriş kutusu bir liste kutusundan daha fazla yer kaplar.</span><span class="sxs-lookup"><span data-stu-id="12acc-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12acc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12acc-112">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="12acc-113">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="12acc-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="12acc-114">Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama</span><span class="sxs-lookup"><span data-stu-id="12acc-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="12acc-115">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="12acc-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
