---
title: ComboBox ve ListBox
description: Windows Forms ComboBox ve Windows Forms ListBox ' ı kullanma hakkında bilgi edinin ve bir görev için bir veya diğerinin ne zaman uygun olduğunu nasıl söyleyeceğinizi öğrenin.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174425"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="47c2b-103">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="47c2b-103">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="47c2b-104"><xref:System.Windows.Forms.ComboBox>Ve <xref:System.Windows.Forms.ListBox> denetimlerinin benzer davranışları vardır ve bazı durumlarda bu şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="47c2b-104">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="47c2b-105">Ancak, bir veya diğeri bir göreve daha uygun olduğunda zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="47c2b-105">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="47c2b-106">Genellikle, bir açılan kutu, önerilen seçeneklerin bir listesi olduğunda uygundur ve girişi listede olacak şekilde sınırlamak istediğinizde bir liste kutusu uygundur.</span><span class="sxs-lookup"><span data-stu-id="47c2b-106">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="47c2b-107">Bir Birleşik giriş kutusu metin kutusu alanı içeriyorsa, listede bulunmayan seçimler içine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="47c2b-107">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="47c2b-108">Özel durum, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğin olarak ayarlandığı durumdur <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> .</span><span class="sxs-lookup"><span data-stu-id="47c2b-108">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="47c2b-109">Bu durumda, ilk harfini yazarsanız denetim bir öğe seçer.</span><span class="sxs-lookup"><span data-stu-id="47c2b-109">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="47c2b-110">Ayrıca, Birleşik giriş kutuları bir formdaki alanı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="47c2b-110">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="47c2b-111">Kullanıcı aşağı oka tıklaana kadar tam liste görüntülenmediği için, bir açılan kutu bir liste kutusunun uygun olmadığı küçük bir alana kolayca uyum sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="47c2b-111">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="47c2b-112">Bir özel durum, <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliğin olarak ayarlandığı durumdur <xref:System.Windows.Forms.ComboBoxStyle.Simple> : tam liste görüntülenir ve Birleşik giriş kutusu bir liste kutusundan daha fazla yer kaplar.</span><span class="sxs-lookup"><span data-stu-id="47c2b-112">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c2b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47c2b-113">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="47c2b-114">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="47c2b-114">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="47c2b-115">Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama</span><span class="sxs-lookup"><span data-stu-id="47c2b-115">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="47c2b-116">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="47c2b-116">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
