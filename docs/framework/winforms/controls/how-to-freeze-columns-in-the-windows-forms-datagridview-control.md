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
ms.openlocfilehash: df8ac7e7db74d4e8df8872b5ec7f8f2ec774b3c8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779964"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b4380-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="b4380-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b4380-103">Kullanıcılar, Windows formlarında gösterilen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetimi, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın.</span><span class="sxs-lookup"><span data-stu-id="b4380-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="b4380-104">Örneğin, müşteri bilgilerinin birçok sütunları içeren bir tablo görüntülerken, müşteri adına dışında görünür bölgesi için diğer sütunları etkinleştirme sırasında her zaman görüntülemek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b4380-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="b4380-105">Bu davranışı elde etmek için denetiminde sütunları dondurma.</span><span class="sxs-lookup"><span data-stu-id="b4380-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="b4380-106">Sütun dondurma, tüm sütunları solunda (veya sağdan sola dil komut sağındakiyle) de dondurulmuş.</span><span class="sxs-lookup"><span data-stu-id="b4380-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="b4380-107">Diğer tüm sütunlar kaydırabilirsiniz sırada dondurulmuş sütun değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="b4380-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4380-108">Sütun yeniden sıralamayı etkinse, dondurulmuş sütun Grup çözülmüş sütunlardan farklı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b4380-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="b4380-109">Kullanıcı iki grupta sütunları konumlandırabilirsiniz, ancak bunlar bir sütun bir grubundan diğerine taşıyamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b4380-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="b4380-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Özelliği sütunun sütun her zaman bir grid içinde görünür olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="b4380-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="b4380-111">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="b4380-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="b4380-112">Ayrıca bkz: [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı içinde Sütunları Dondur](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b4380-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="b4380-113">Bir sütunu programlı olarak dondurmak için</span><span class="sxs-lookup"><span data-stu-id="b4380-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="b4380-114">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="b4380-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4380-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b4380-115">Compiling the Code</span></span>  
 <span data-ttu-id="b4380-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b4380-116">This example requires:</span></span>  
  
-   <span data-ttu-id="b4380-117">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="b4380-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="b4380-118">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="b4380-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4380-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4380-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="b4380-120">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b4380-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="b4380-121">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b4380-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
