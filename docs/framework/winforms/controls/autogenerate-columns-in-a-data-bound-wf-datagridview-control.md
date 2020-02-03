---
title: Veriye dayalı DataGridView denetiminde sütunları otomatik olarak oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 860e640e095537358d2f8778c810aa577e9d7ff0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746237"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="120df-102">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="120df-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="120df-103">Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView> denetimindeki bir bağlantılı veri kaynağından sütunların nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="120df-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="120df-104"><xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> Özellik değeri `true` (varsayılan) olduğunda, veri kaynağı tablosundaki her sütun için bir <xref:System.Windows.Forms.DataGridViewColumn> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="120df-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="120df-105"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliğini ayarladığınızda <xref:System.Windows.Forms.DataGridView> denetiminde zaten sütun varsa, varolan bağlantılı sütunlar veri kaynağındaki sütunlarla karşılaştırılır ve bir eşleşme olduğunda korunur.</span><span class="sxs-lookup"><span data-stu-id="120df-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="120df-106">İlişkisiz sütunlar her zaman korunur.</span><span class="sxs-lookup"><span data-stu-id="120df-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="120df-107">Veri kaynağında eşleşme olmayan bağlantılı sütunlar kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="120df-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="120df-108">Denetimde eşleşme olmayan veri kaynağındaki sütunlar, <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonun sonuna eklenen yeni <xref:System.Windows.Forms.DataGridViewColumn> nesneleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="120df-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="120df-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="120df-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="120df-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="120df-110">Compiling the Code</span></span>  
 <span data-ttu-id="120df-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="120df-111">This example requires:</span></span>  
  
- <span data-ttu-id="120df-112">`customersDataGridView`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="120df-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
- <span data-ttu-id="120df-113">`Customers`adlı bir tabloya sahip `customersDataSet` adlı <xref:System.Data.DataSet> nesne.</span><span class="sxs-lookup"><span data-stu-id="120df-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
- <span data-ttu-id="120df-114"><xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>ve <xref:System.Xml?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="120df-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120df-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="120df-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="120df-116">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="120df-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="120df-117">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="120df-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
