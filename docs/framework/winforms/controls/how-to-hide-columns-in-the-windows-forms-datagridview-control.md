---
title: DataGridView Denetimindeki sütunları gizleme
description: DataGridViewColumn. Visible özelliğini false olarak ayarlayarak Windows Forms DataGridView Denetimindeki sütunları programlama yoluyla gizlemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 27e9f331151acd68d76233bc7dbb09c2d870afde
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618057"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fe4a6-103">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Gizleme</span><span class="sxs-lookup"><span data-stu-id="fe4a6-103">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fe4a6-104">Bazen Windows Forms denetiminde kullanılabilir olan sütunlardan yalnızca bazılarını göstermek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="fe4a6-104">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fe4a6-105">Örneğin, yönetim kimlik bilgilerine sahip kullanıcılara bir çalışan maaş sütununu diğer kullanıcılardan gizleyerek göstermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-105">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="fe4a6-106">Alternatif olarak, denetimi çok sayıda sütun içeren bir veri kaynağına ve yalnızca bir kısmını göstermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-106">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="fe4a6-107">Bu durumda, genellikle, görüntülemeden İlgilendiğiniz sütunları gizlemeniz yerine kaldıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-107">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="fe4a6-108"><xref:System.Windows.Forms.DataGridView>Denetimde, <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> sütunun özellik değeri sütunun görüntülenip görüntülenmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-108">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="fe4a6-109">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="fe4a6-110">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunları gizleme](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="fe4a6-110">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="fe4a6-111">Bir sütunu programlı bir şekilde gizlemek için</span><span class="sxs-lookup"><span data-stu-id="fe4a6-111">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="fe4a6-112"><xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>Özelliğini olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="fe4a6-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="fe4a6-113">`CustomerID`Veri bağlama sırasında otomatik olarak oluşturulan bir sütunu gizlemek için aşağıdaki kod örneğini bir <xref:System.Windows.Forms.DataGridView.DataBindingComplete> olay işleyicisine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-113">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe4a6-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fe4a6-114">Compiling the Code</span></span>  
 <span data-ttu-id="fe4a6-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fe4a6-115">This example requires:</span></span>  
  
- <span data-ttu-id="fe4a6-116">Adında <xref:System.Windows.Forms.DataGridView> `dataGridView1` bir sütun içeren adlı bir denetim `CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="fe4a6-116">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="fe4a6-117"><xref:System?displayProperty=nameWithType>Ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-117">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4a6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4a6-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fe4a6-119">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="fe4a6-119">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="fe4a6-120">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="fe4a6-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="fe4a6-121">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fe4a6-121">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
