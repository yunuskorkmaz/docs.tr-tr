---
title: "Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f266af44f954cb8416e1f7672f6642ab7c6995b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="0d6ee-102">Nasıl yapılır: Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminin İçeriğini Sıralama</span><span class="sxs-lookup"><span data-stu-id="0d6ee-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="0d6ee-103">Verilere bağlı olduklarında Windows Forms denetimleri sıralama değil.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="0d6ee-104">Sıralanmış veri görüntülemek için sıralama destekleyen bir veri kaynağı kullanmak ve sıralanmasını veri kaynağına sahip.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="0d6ee-105">Sıralama destekleyen veri kaynakları veri görünümleri, veri yöneticileri görüntülemek ve diziler sıralanır.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="0d6ee-106">Veri bağlama denetimi durumda değilse, sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="0d6ee-107">Sıralamak için</span><span class="sxs-lookup"><span data-stu-id="0d6ee-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="0d6ee-108">Ayarlama `Sorted` özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="0d6ee-109">Bu ayar, var olan tüm liste öğelerini sıralanmış olarak yeniden konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6ee-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d6ee-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="0d6ee-111">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="0d6ee-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="0d6ee-112">Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetiminde Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0d6ee-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="0d6ee-113">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="0d6ee-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="0d6ee-114">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="0d6ee-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
