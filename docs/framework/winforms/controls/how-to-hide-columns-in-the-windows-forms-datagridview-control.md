---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: c1a0283a38a7ef0b8b4a751f7d0e46f5e1d521eb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723003"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="488b8-102">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları gizleme</span><span class="sxs-lookup"><span data-stu-id="488b8-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="488b8-103">Bazen yalnızca bazı Windows Forms'ta mevcut olan sütunları görüntülemek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="488b8-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="488b8-104">Örneğin, bir çalışan göstermek isteyebilirsiniz maaş sütun diğer kullanıcılardan gizleyerek sırasında yönetim kimlik bilgilerine sahip kullanıcılar için.</span><span class="sxs-lookup"><span data-stu-id="488b8-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="488b8-105">Alternatif olarak, denetimi yalnızca bazılarının görüntülemek istediğiniz çok sayıda sütun içeren bir veri kaynağına bağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488b8-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="488b8-106">Bu durumda, genellikle görüntülenmesinde ilgilenmediğiniz yerine, bunları gizlemek sütunları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="488b8-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="488b8-107">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> bir sütunun değerini özellik bu sütunun görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="488b8-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="488b8-108">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="488b8-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="488b8-109">Ayrıca bkz: [nasıl yapılır: Forms DataGridView denetiminde Tasarımcı kullanarak Windows sütunları gizleme](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="488b8-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="488b8-110">Program aracılığıyla bir sütunu gizlemek için</span><span class="sxs-lookup"><span data-stu-id="488b8-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="488b8-111">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="488b8-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="488b8-112">Gizlemek için bir `CustomerID` veri bağlama sırasında otomatik olarak oluşturulan bir sütuna yerleştirin aşağıdaki kod örneğinde bir <xref:System.Windows.Forms.DataGridView.DataBindingComplete> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="488b8-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="488b8-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="488b8-113">Compiling the Code</span></span>  
 <span data-ttu-id="488b8-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="488b8-114">This example requires:</span></span>  
  
-   <span data-ttu-id="488b8-115">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="488b8-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="488b8-116">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="488b8-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488b8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="488b8-117">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="488b8-118">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="488b8-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="488b8-119">Nasıl yapılır: Otomatik oluşturulan sütunları Windows Forms DataGridView denetiminden kaldırma</span><span class="sxs-lookup"><span data-stu-id="488b8-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="488b8-120">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunların sırasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="488b8-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
