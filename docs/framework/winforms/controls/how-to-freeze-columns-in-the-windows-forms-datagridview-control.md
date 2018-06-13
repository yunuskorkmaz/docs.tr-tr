---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 6eb6fab4b147365221ba79a682c4eaf744d24b25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532675"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="aa7b8-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="aa7b8-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="aa7b8-103">Kullanıcılar Windows Forms'ta görüntülenen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetim, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="aa7b8-104">Örneğin, müşteri bilgilerinin pek çok sütun içeren bir tablo görüntülerken, müşteri adı görünür bölgesinin dışındaki ilerlemek için diğer sütunları etkinleştirme sırasında her zaman görüntülemek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="aa7b8-105">Bu davranış elde etmek için denetiminde sütunları dondurma.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="aa7b8-106">Bir sütun dondurma, tüm sütunlar solunda (veya sağdan sola dil komut sağındaki) de dondurulmuş.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="aa7b8-107">Diğer tüm sütunları kaydırabilirsiniz sırada dondurulmuş sütun yerinde kalır.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa7b8-108">Sütun yeniden sıralamayı etkinleştirilirse dondurulmuş sütunların çözülmüş sütunlarından ayrı bir grup olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="aa7b8-109">Kullanıcılar ya da Grup sütun konumunu değiştirebilirsiniz, ancak bunlar bir sütun bir gruptan diğerine taşıyamazsınız.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="aa7b8-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Bir sütunun özelliği sütun her zaman ızgara içinde görünür olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="aa7b8-111">Visual Studio'da bu görev için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="aa7b8-112">Ayrıca bkz. [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı Dondur sütunlar](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="aa7b8-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="aa7b8-113">Bir sütunu program aracılığıyla dondurmak için</span><span class="sxs-lookup"><span data-stu-id="aa7b8-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="aa7b8-114">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa7b8-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="aa7b8-115">Compiling the Code</span></span>  
 <span data-ttu-id="aa7b8-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="aa7b8-116">This example requires:</span></span>  
  
-   <span data-ttu-id="aa7b8-117">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="aa7b8-118">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7b8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa7b8-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="aa7b8-120">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="aa7b8-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="aa7b8-121">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="aa7b8-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
