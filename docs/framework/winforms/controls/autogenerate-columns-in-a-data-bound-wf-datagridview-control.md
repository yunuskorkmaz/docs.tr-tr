---
title: "Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1d6a790f8a43f4ea2f9d3ad2cdb282186554da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="ae43a-102">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae43a-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ae43a-103">Aşağıdaki kod örneğinde bir bağımlı veri kaynağından sütunları görüntülemek nasıl gösteren bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="ae43a-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ae43a-104">Zaman <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> özellik değeri `true` (varsayılan), bir <xref:System.Windows.Forms.DataGridViewColumn> veri kaynağı tablodaki her sütun için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ae43a-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="ae43a-105">Varsa <xref:System.Windows.Forms.DataGridView> denetim ayarladığınızda sütunu zaten var. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliği, var olan ilişkili sütunların veri kaynağındaki sütunları karşılaştırılan ve bir eşleşme olduğunda korunur.</span><span class="sxs-lookup"><span data-stu-id="ae43a-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="ae43a-106">Bağlanmamış sütunlar her zaman korunur.</span><span class="sxs-lookup"><span data-stu-id="ae43a-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="ae43a-107">Kendisi için bir eşleşme yoktur veri kaynağında ilişkili sütunları kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ae43a-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="ae43a-108">Kendisi için bir eşleşme yoktur denetiminde veri kaynağındaki sütunları oluşturmak yeni <xref:System.Windows.Forms.DataGridViewColumn> sonuna eklenen nesneleri <xref:System.Windows.Forms.DataGridView.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ae43a-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae43a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae43a-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae43a-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ae43a-110">Compiling the Code</span></span>  
 <span data-ttu-id="ae43a-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ae43a-111">This example requires:</span></span>  
  
-   <span data-ttu-id="ae43a-112">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="ae43a-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
-   <span data-ttu-id="ae43a-113">A <xref:System.Data.DataSet> adlı nesne `customersDataSet` adlı bir tablo olan `Customers`.</span><span class="sxs-lookup"><span data-stu-id="ae43a-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
-   <span data-ttu-id="ae43a-114">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, ve <xref:System.Xml?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="ae43a-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae43a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae43a-115">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ae43a-116">Windows Forms DataGridView denetiminde verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ae43a-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="ae43a-117">Nasıl yapılır: Kaldır otomatik oluşturulan sütunları Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="ae43a-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)
