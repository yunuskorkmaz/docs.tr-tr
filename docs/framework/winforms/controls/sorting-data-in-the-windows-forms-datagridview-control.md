---
title: Windows Forms DataGridView denetiminde verileri sıralama
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1cbfb4a19e9bb0db5cbb595a91a254a3a8e3f309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536019"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7ffd7-102">Windows Forms DataGridView denetiminde verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="7ffd7-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="7ffd7-103">Varsayılan olarak, kullanıcılar verileri sıralayabilir bir <xref:System.Windows.Forms.DataGridView> denetim bir metin kutusu sütun başlığını tıklatarak (veya bir metin kutusu hücre .NET Framework 4.7.2 ve sonraki sürümler odaklanan açarken F3 tuşuna basarak).</span><span class="sxs-lookup"><span data-stu-id="7ffd7-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="7ffd7-104">Değiştirebileceğiniz <xref:System.Windows.Forms.DataGridViewColumn.SortMode> Bunu yapmak için anlamlı yaptığında, diğer sütun türlerine göre sıralamak kullanıcıların belirli sütunlardaki özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="7ffd7-105">Verileri programlı olarak herhangi bir sütun tarafından ya da birden çok sütuna göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7ffd7-106">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="7ffd7-106">In this section</span></span>

[<span data-ttu-id="7ffd7-107">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="7ffd7-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="7ffd7-108">Denetimindeki verileri sıralama seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="7ffd7-109">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7ffd7-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="7ffd7-110">Varsayılan olarak sıralanabilir olmayan sütuna göre sıralamak kullanıcıların sağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="7ffd7-111">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7ffd7-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="7ffd7-112">Verileri programlamayla sıralama ve kullanarak sıralamayı özelleştirme açıklar <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> olay veya uygulama tarafından <xref:System.Collections.IComparer> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="7ffd7-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7ffd7-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="7ffd7-114">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="7ffd7-115">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="7ffd7-116">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="7ffd7-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumnSortMode> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ffd7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ffd7-118">See also</span></span>

[<span data-ttu-id="7ffd7-119">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="7ffd7-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
[<span data-ttu-id="7ffd7-120">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="7ffd7-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  