---
title: 'Nasıl yapılır: Bir veri bağlantılı Windows Forms DataGridView denetimine bağlantısız sütun ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: d7f96aa8d11cee9427a9e51f8e79fc55adc79355
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712024"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="28448-102">Nasıl yapılır: Bir veri bağlantılı Windows Forms DataGridView denetimine bağlantısız sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="28448-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="28448-103">Görüntü içinde veri <xref:System.Windows.Forms.DataGridView> denetim normalde bir tür veri kaynağından gelir, ancak bir veri kaynağından gelmeyen veri sütununu görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28448-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="28448-104">Bu tür bir sütun bağlantısız sütun adı verilir.</span><span class="sxs-lookup"><span data-stu-id="28448-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="28448-105">Bağlanmamış sütunlar birçok biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="28448-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="28448-106">Genellikle, bir veri satırı ayrıntılarını erişim sağlamak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="28448-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="28448-107">Aşağıdaki kod örneği, bağlantısız sütun oluşturma işlemini gösterir **ayrıntıları** bir alt tabloda gösterilecek düğmeler ilgili bir ana tablodaki belirli bir satır için ana/ayrıntı senaryo uyguladığınızda.</span><span class="sxs-lookup"><span data-stu-id="28448-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="28448-108">Düğme tıklamalarına yanıt verme için uygulayan bir <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> alt tablo içeren bir form görüntüler olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="28448-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="28448-109">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="28448-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="28448-110">Ayrıca bkz: [nasıl yapılır: Ekle ve Kaldır sütunları Windows Forms DataGridView Tasarımcısı'nı kullanarak denetiminde](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="28448-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28448-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="28448-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28448-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="28448-112">Compiling the Code</span></span>  
 <span data-ttu-id="28448-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="28448-113">This example requires:</span></span>  
  
-   <span data-ttu-id="28448-114">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="28448-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="28448-115">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="28448-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28448-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28448-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="28448-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="28448-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="28448-118">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="28448-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
