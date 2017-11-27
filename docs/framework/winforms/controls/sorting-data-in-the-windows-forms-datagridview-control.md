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
ms.openlocfilehash: b4027f3ae604f2a3ff4996855fa6dd34d4de8ea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8ea61-102">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="8ea61-102">Sorting Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8ea61-103">Varsayılan olarak, kullanıcılar verileri sıralayabilir bir `DataGridView` bir metin kutusu sütun başlığını tıklatarak denetim.</span><span class="sxs-lookup"><span data-stu-id="8ea61-103">By default, users can sort the data in a `DataGridView` control by clicking the header of a text box column.</span></span> <span data-ttu-id="8ea61-104">Değiştirebileceğiniz `SortMode` Bunu yapmak için anlamlı yaptığında, diğer sütun türlerine göre sıralamak kullanıcıların belirli sütunlardaki özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ea61-104">You can modify the `SortMode` property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="8ea61-105">Verileri programlı olarak herhangi bir sütun tarafından ya da birden çok sütuna göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ea61-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ea61-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8ea61-106">In This Section</span></span>  
 [<span data-ttu-id="8ea61-107">Windows Forms DataGridView denetiminde Sütun sıralama modları</span><span class="sxs-lookup"><span data-stu-id="8ea61-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8ea61-108">Denetimindeki verileri sıralama seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ea61-108">Describes the options for sorting data in the control.</span></span>  
  
 [<span data-ttu-id="8ea61-109">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ea61-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 <span data-ttu-id="8ea61-110">Varsayılan olarak sıralanabilir olmayan sütuna göre sıralamak kullanıcıların sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ea61-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>  
  
 [<span data-ttu-id="8ea61-111">Nasıl yapılır: Windows Forms DataGridView denetiminde sıralamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8ea61-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8ea61-112">Verileri programlamayla sıralama ve kullanarak sıralamayı özelleştirme açıklar <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> olay veya uygulama tarafından <xref:System.Collections.IComparer> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8ea61-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8ea61-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8ea61-113">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="8ea61-114">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="8ea61-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <span data-ttu-id="8ea61-115">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ea61-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="8ea61-116">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ea61-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode>  
 <span data-ttu-id="8ea61-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumnSortMode> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="8ea61-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea61-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ea61-118">See Also</span></span>  
 [<span data-ttu-id="8ea61-119">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="8ea61-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="8ea61-120">Windows Forms DataGridView denetiminde sütun türleri</span><span class="sxs-lookup"><span data-stu-id="8ea61-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
