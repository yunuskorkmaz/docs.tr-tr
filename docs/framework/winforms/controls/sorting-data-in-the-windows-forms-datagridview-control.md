---
title: DataGridView Denetimindeki verileri sıralama
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742949"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="451d9-102">Windows Forms DataGridView Denetimindeki verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="451d9-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="451d9-103">Varsayılan olarak, kullanıcılar bir <xref:System.Windows.Forms.DataGridView> denetimindeki verileri metin kutusu sütununun başlığına tıklayarak sıralayabilir (veya bir metin kutusu hücresi .NET Framework 4.7.2 ve sonraki sürümlere odaklandığında F3 tuşuna basarak).</span><span class="sxs-lookup"><span data-stu-id="451d9-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="451d9-104">Belirli sütunların <xref:System.Windows.Forms.DataGridViewColumn.SortMode> özelliğini, kullanıcıların bunu yapabilmeleri durumunda diğer sütun türlerine göre sıralamalarına izin verecek şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="451d9-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="451d9-105">Ayrıca, verileri herhangi bir sütuna veya birden çok sütuna göre programlı bir şekilde sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="451d9-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="451d9-106">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="451d9-106">In this section</span></span>

[<span data-ttu-id="451d9-107">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="451d9-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="451d9-108">Denetimdeki verileri sıralama seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="451d9-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="451d9-109">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="451d9-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="451d9-110">Kullanıcıların varsayılan olarak sıralanabilir olmayan sütunlara göre sıralama için nasıl etkinleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="451d9-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="451d9-111">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="451d9-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="451d9-112">Verilerin programlı olarak nasıl sıralanacağını ve <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> olayı kullanılarak veya <xref:System.Collections.IComparer> arabirimini uygulayarak sıralamayı nasıl özelleştireceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="451d9-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="451d9-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="451d9-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="451d9-114"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="451d9-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="451d9-115"><xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="451d9-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="451d9-116"><xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="451d9-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="451d9-117"><xref:System.Windows.Forms.DataGridViewColumnSortMode> numaralandırması için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="451d9-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="451d9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="451d9-118">See also</span></span>

- [<span data-ttu-id="451d9-119">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="451d9-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="451d9-120">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="451d9-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
