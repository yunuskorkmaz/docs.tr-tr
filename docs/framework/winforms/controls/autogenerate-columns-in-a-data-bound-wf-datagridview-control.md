---
title: 'Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 4490a24047f5cce1328d68c529783a1d7692ff32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166003"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="08c1e-102">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08c1e-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="08c1e-103">Aşağıdaki kod örneği, bir bağlı veri kaynağından sütunları görüntülemek gösterilmiştir bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="08c1e-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="08c1e-104">Zaman <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özellik değeri `true` (varsayılan), bir <xref:System.Windows.Forms.DataGridViewColumn> veri kaynağı tablosu içindeki her bir sütun için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08c1e-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="08c1e-105">Varsa <xref:System.Windows.Forms.DataGridView> denetimi ayarladığınızda sütunu zaten var. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliği, mevcut bağlı sütun veri kaynağında sütunları karşılaştırılan ve bir eşleşme olduğunda korunur.</span><span class="sxs-lookup"><span data-stu-id="08c1e-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="08c1e-106">Bağlanmamış sütunlar her zaman korunur.</span><span class="sxs-lookup"><span data-stu-id="08c1e-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="08c1e-107">Var olan veri kaynağında eşleşme bağlı sütun kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="08c1e-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="08c1e-108">Vygenerovat sloupce var olduğu eşleşme denetiminde veri kaynağı içindeki yeni <xref:System.Windows.Forms.DataGridViewColumn> sonuna eklenen nesneleri <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="08c1e-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08c1e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="08c1e-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08c1e-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="08c1e-110">Compiling the Code</span></span>  
 <span data-ttu-id="08c1e-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="08c1e-111">This example requires:</span></span>  
  
-   <span data-ttu-id="08c1e-112">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="08c1e-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
-   <span data-ttu-id="08c1e-113">A <xref:System.Data.DataSet> adlı nesne `customersDataSet` adlı bir tablo olan `Customers`.</span><span class="sxs-lookup"><span data-stu-id="08c1e-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
-   <span data-ttu-id="08c1e-114">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, ve <xref:System.Xml?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="08c1e-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c1e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08c1e-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="08c1e-116">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="08c1e-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="08c1e-117">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="08c1e-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
