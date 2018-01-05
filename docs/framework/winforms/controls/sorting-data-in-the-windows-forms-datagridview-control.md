---
title: "Windows Forms DataGridView Denetimindeki Verileri Sıralama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2327c6d9696bc5fb54943eb8bbce9d4795a378b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1ad4f-102">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="1ad4f-102">Sorting Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1ad4f-103">Varsayılan olarak, kullanıcılar verileri sıralayabilir bir `DataGridView` bir metin kutusu sütun başlığını tıklatarak denetim.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-103">By default, users can sort the data in a `DataGridView` control by clicking the header of a text box column.</span></span> <span data-ttu-id="1ad4f-104">Değiştirebileceğiniz `SortMode` Bunu yapmak için anlamlı yaptığında, diğer sütun türlerine göre sıralamak kullanıcıların belirli sütunlardaki özelliği.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-104">You can modify the `SortMode` property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="1ad4f-105">Verileri programlı olarak herhangi bir sütun tarafından ya da birden çok sütuna göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ad4f-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1ad4f-106">In This Section</span></span>  
 [<span data-ttu-id="1ad4f-107">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="1ad4f-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ad4f-108">Denetimindeki verileri sıralama seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-108">Describes the options for sorting data in the control.</span></span>  
  
 [<span data-ttu-id="1ad4f-109">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1ad4f-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 <span data-ttu-id="1ad4f-110">Varsayılan olarak sıralanabilir olmayan sütuna göre sıralamak kullanıcıların sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>  
  
 [<span data-ttu-id="1ad4f-111">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1ad4f-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ad4f-112">Verileri programlamayla sıralama ve kullanarak sıralamayı özelleştirme açıklar <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> olay veya uygulama tarafından <xref:System.Collections.IComparer> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ad4f-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1ad4f-113">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="1ad4f-114">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <span data-ttu-id="1ad4f-115">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="1ad4f-116">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode>  
 <span data-ttu-id="1ad4f-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumnSortMode> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad4f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ad4f-118">See Also</span></span>  
 [<span data-ttu-id="1ad4f-119">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="1ad4f-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="1ad4f-120">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="1ad4f-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
