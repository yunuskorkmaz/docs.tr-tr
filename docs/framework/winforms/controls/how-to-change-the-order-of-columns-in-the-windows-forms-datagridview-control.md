---
title: DataGridView Denetimindeki sütunların sırasını değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746549"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8d30c-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8d30c-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8d30c-103">Bir veri kaynağındaki verileri göstermek için <xref:System.Windows.Forms.DataGridView> kullandığınızda, veri kaynağının şemasındaki sütunların bazen bunları göstermek istediğiniz sırada görünmemelidir.</span><span class="sxs-lookup"><span data-stu-id="8d30c-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="8d30c-104"><xref:System.Windows.Forms.DataGridViewColumn> sınıfının <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> özelliğini kullanarak sütunların görüntülenme sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d30c-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="8d30c-105">Aşağıdaki kod örneği, Northwind örnek veritabanındaki Customers tablosuna bağlanırken otomatik olarak oluşturulan sütunlardan bazılarını konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="8d30c-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="8d30c-106"><xref:System.Windows.Forms.DataGridView> denetimini bir veritabanı tablosuna bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Forms DataGridView denetimine bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8d30c-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="8d30c-107">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="8d30c-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="8d30c-108">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunların sırasını değiştirme](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="8d30c-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d30c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d30c-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d30c-110">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="8d30c-110">Compiling the Code</span></span>  
 <span data-ttu-id="8d30c-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8d30c-111">This example requires:</span></span>  
  
- <span data-ttu-id="8d30c-112">Northwind örnek veritabanındaki `Customers` tablosu gibi, belirtilen sütun adlarıyla bir tabloya bağlanan `customersDataGridView` adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="8d30c-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
- <span data-ttu-id="8d30c-113"><xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>ve <xref:System.Xml?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="8d30c-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d30c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d30c-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8d30c-115">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8d30c-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8d30c-116">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="8d30c-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
