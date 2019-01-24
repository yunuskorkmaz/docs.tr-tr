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
ms.openlocfilehash: e877545f93fb57b636fd2e1559f52b4ad70a0b4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722770"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="fe88e-102">Nasıl yapılır: Bir veri bağlantılı Windows Forms DataGridView denetimine bağlantısız sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="fe88e-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fe88e-103">Görüntü içinde veri <xref:System.Windows.Forms.DataGridView> denetim normalde bir tür veri kaynağından gelir, ancak bir veri kaynağından gelmeyen veri sütununu görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe88e-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="fe88e-104">Bu tür bir sütun bağlantısız sütun adı verilir.</span><span class="sxs-lookup"><span data-stu-id="fe88e-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="fe88e-105">Bağlanmamış sütunlar birçok biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe88e-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="fe88e-106">Genellikle, bir veri satırı ayrıntılarını erişim sağlamak için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="fe88e-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="fe88e-107">Aşağıdaki kod örneği, bağlantısız sütun oluşturma işlemini gösterir **ayrıntıları** bir alt tabloda gösterilecek düğmeler ilgili bir ana tablodaki belirli bir satır için ana/ayrıntı senaryo uyguladığınızda.</span><span class="sxs-lookup"><span data-stu-id="fe88e-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="fe88e-108">Düğme tıklamalarına yanıt verme için uygulayan bir <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> alt tablo içeren bir form görüntüler olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="fe88e-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="fe88e-109">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe88e-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="fe88e-110">Ayrıca bkz: [nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma](https://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="fe88e-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe88e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe88e-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe88e-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fe88e-112">Compiling the Code</span></span>  
 <span data-ttu-id="fe88e-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fe88e-113">This example requires:</span></span>  
  
-   <span data-ttu-id="fe88e-114">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="fe88e-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="fe88e-115">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="fe88e-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe88e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe88e-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="fe88e-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fe88e-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fe88e-118">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="fe88e-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
