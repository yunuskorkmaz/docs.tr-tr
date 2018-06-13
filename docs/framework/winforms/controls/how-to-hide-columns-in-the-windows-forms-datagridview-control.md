---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 65228490dd90aaf1f1d76b6a37f9cb9e8a739746
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533594"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="71dc2-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Gizleme</span><span class="sxs-lookup"><span data-stu-id="71dc2-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="71dc2-103">Bazı durumlarda yalnızca bazı Windows Forms'ta kullanılabilir olan sütunları görüntülemek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="71dc2-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="71dc2-104">Örneğin, bir çalışan Göster isteyebilirsiniz maaş sütun diğer kullanıcılardan gizleme sırasında yönetim kimlik bilgilerine sahip kullanıcılar için.</span><span class="sxs-lookup"><span data-stu-id="71dc2-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="71dc2-105">Alternatif olarak, yalnızca bazıları görüntülemek istediğiniz sayıda sütun içeren bir veri kaynağına denetimi bağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71dc2-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="71dc2-106">Bu durumda, genellikle görüntülenmesini de ilginizi olmayan yerine, gizleme sütunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="71dc2-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="71dc2-107">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> bir sütunun özellik değeri, sütuna görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="71dc2-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="71dc2-108">Visual Studio'da bu görev için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="71dc2-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="71dc2-109">Ayrıca bkz. [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı Gizle sütunlar](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="71dc2-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="71dc2-110">Bir sütun program aracılığıyla gizleme</span><span class="sxs-lookup"><span data-stu-id="71dc2-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="71dc2-111">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="71dc2-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="71dc2-112">Gizlemek için bir `CustomerID` veri bağlama sırasında otomatik olarak oluşturulan sütun yerleştirin aşağıdaki kod örneğinde bir <xref:System.Windows.Forms.DataGridView.DataBindingComplete> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="71dc2-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71dc2-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="71dc2-113">Compiling the Code</span></span>  
 <span data-ttu-id="71dc2-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="71dc2-114">This example requires:</span></span>  
  
-   <span data-ttu-id="71dc2-115">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="71dc2-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="71dc2-116">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="71dc2-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71dc2-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71dc2-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="71dc2-118">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="71dc2-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="71dc2-119">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="71dc2-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="71dc2-120">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="71dc2-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
