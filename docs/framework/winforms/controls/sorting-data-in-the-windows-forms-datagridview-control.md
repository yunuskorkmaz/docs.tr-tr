---
title: Windows Forms DataGridView denetiminde verileri sıralama
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 588678b3ba0d75fea58709c1969a3e276d65439e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688291"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d323f-102">Windows Forms DataGridView denetiminde verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="d323f-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="d323f-103">Varsayılan olarak, kullanıcılar verileri sıralayabilir bir <xref:System.Windows.Forms.DataGridView> denetimi bir metin kutusu sütunun başlığına tıklayarak (veya .NET Framework 4.7.2 ve sonraki sürümlerinde bir metin kutusu hücre odaklandığında F3 tuşuna basarak).</span><span class="sxs-lookup"><span data-stu-id="d323f-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="d323f-104">Değiştirebileceğiniz <xref:System.Windows.Forms.DataGridViewColumn.SortMode> kullanıcıların bunu yapmak için mantıklı zaman diğer sütun türlerine göre sıralamak belirli sütunları özelliği.</span><span class="sxs-lookup"><span data-stu-id="d323f-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="d323f-105">Verileri program aracılığıyla herhangi bir sütun veya birden çok sütuna göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d323f-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d323f-106">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="d323f-106">In this section</span></span>

[<span data-ttu-id="d323f-107">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="d323f-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d323f-108">Denetimindeki verileri sıralama seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d323f-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="d323f-109">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="d323f-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="d323f-110">Varsayılan olarak sıralanabilir yer almayan sütunlara göre sıralama olanağı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d323f-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="d323f-111">Nasıl yapılır: Windows Forms DataGridView denetiminde sıralamayı özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d323f-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d323f-112">Verileri programlamayla sıralama ve sıralama kullanarak özelleştirmek nasıl açıklar <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> olay veya uygulama tarafından <xref:System.Collections.IComparer> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d323f-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="d323f-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d323f-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="d323f-114">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d323f-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="d323f-115">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d323f-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="d323f-116">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d323f-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="d323f-117">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewColumnSortMode> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d323f-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d323f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d323f-118">See also</span></span>

- [<span data-ttu-id="d323f-119">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="d323f-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="d323f-120">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="d323f-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
