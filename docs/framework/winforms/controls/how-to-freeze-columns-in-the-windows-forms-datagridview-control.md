---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları dondurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: b4e65f0fd329f624aa186748d298257b15617c17
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584271"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="421c3-102">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları dondurma</span><span class="sxs-lookup"><span data-stu-id="421c3-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="421c3-103">Kullanıcılar, Windows formlarında gösterilen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetimi, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın.</span><span class="sxs-lookup"><span data-stu-id="421c3-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="421c3-104">Örneğin, müşteri bilgilerinin birçok sütunları içeren bir tablo görüntülerken, müşteri adına dışında görünür bölgesi için diğer sütunları etkinleştirme sırasında her zaman görüntülemek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="421c3-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="421c3-105">Bu davranışı elde etmek için denetiminde sütunları dondurma.</span><span class="sxs-lookup"><span data-stu-id="421c3-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="421c3-106">Sütun dondurma, tüm sütunları solunda (veya sağdan sola dil komut sağındakiyle) de dondurulmuş.</span><span class="sxs-lookup"><span data-stu-id="421c3-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="421c3-107">Diğer tüm sütunlar kaydırabilirsiniz sırada dondurulmuş sütun değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="421c3-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="421c3-108">Sütun yeniden sıralamayı etkinse, dondurulmuş sütun Grup çözülmüş sütunlardan farklı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="421c3-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="421c3-109">Kullanıcı iki grupta sütunları konumlandırabilirsiniz, ancak bunlar bir sütun bir grubundan diğerine taşıyamazsınız.</span><span class="sxs-lookup"><span data-stu-id="421c3-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="421c3-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Özelliği sütunun sütun her zaman bir grid içinde görünür olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="421c3-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="421c3-111">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="421c3-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="421c3-112">Ayrıca bkz: [nasıl yapılır: Sütunları dondurma Windows Forms DataGridView denetimi Tasarımcısı'nı kullanarak](freeze-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="421c3-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="421c3-113">Bir sütunu programlı olarak dondurmak için</span><span class="sxs-lookup"><span data-stu-id="421c3-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="421c3-114">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="421c3-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="421c3-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="421c3-115">Compiling the Code</span></span>  
 <span data-ttu-id="421c3-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="421c3-116">This example requires:</span></span>  
  
-   <span data-ttu-id="421c3-117">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="421c3-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="421c3-118">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="421c3-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="421c3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="421c3-119">See also</span></span>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="421c3-120">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="421c3-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="421c3-121">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları yeniden sıralamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="421c3-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
