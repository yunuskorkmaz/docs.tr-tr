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
ms.openlocfilehash: 8a2429049acf1a22edde8d132ece17da4e91f1db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111429"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="1ab71-102">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="1ab71-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="1ab71-103"><xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ListBox> denetimleri benzer davranışlara sahiptir ve bazı durumlarda değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1ab71-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="1ab71-104">Bir veya başka bir görev için daha uygun olduğunda zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="1ab71-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="1ab71-105">Genel olarak, önerilen seçenek listesini olduğunda ve listede nedir için giriş sınırlandırmak istediğinizde bir liste kutusunda uygun bir birleşik giriş kutusu uygundur.</span><span class="sxs-lookup"><span data-stu-id="1ab71-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="1ab71-106">Listede olmayan seçimler yazılabilir için bir açılan kutunun metin kutusu alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="1ab71-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="1ab71-107">Özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="1ab71-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="1ab71-108">Bu durumda, ilk harfinden yazarsanız denetimi bir öğe seçin.</span><span class="sxs-lookup"><span data-stu-id="1ab71-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="1ab71-109">Ayrıca, birleşik giriş kutuları, form üzerinde alanı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1ab71-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="1ab71-110">Kullanıcı aşağı oka tıklayana kadar tam listesi görüntülenmez için birleşik giriş kutusu liste kutusu değil nerelerde küçük bir alana kolayca uygun olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ab71-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="1ab71-111">Bir özel durum olduğunda <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> özelliği <xref:System.Windows.Forms.ComboBoxStyle.Simple>: tam listesi görüntülenir ve birleşik giriş kutusu liste kutusunun olduğu kadar temkinli daha fazla yer alır.</span><span class="sxs-lookup"><span data-stu-id="1ab71-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab71-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ab71-112">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="1ab71-113">Nasıl yapılır: Ekleme ve kaldırma öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi</span><span class="sxs-lookup"><span data-stu-id="1ab71-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="1ab71-114">Nasıl yapılır: Sıralama içeriği bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi</span><span class="sxs-lookup"><span data-stu-id="1ab71-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="1ab71-115">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="1ab71-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
