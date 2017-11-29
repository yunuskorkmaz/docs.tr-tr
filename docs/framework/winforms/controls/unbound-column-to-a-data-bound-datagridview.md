---
title: "Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme"
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
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cd6a1494a98d912469f7e45c7751a0a9741ff17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="24f51-102">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="24f51-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="24f51-103">Görüntü içinde veri <xref:System.Windows.Forms.DataGridView> denetim normalde bir tür veri kaynağından gelir, ancak veri kaynağı'ndan gelmez veri sütunu görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24f51-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="24f51-104">Bu tür bir sütun bağlantısız sütun adı verilir.</span><span class="sxs-lookup"><span data-stu-id="24f51-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="24f51-105">Bağlanmamış sütunlar birçok biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="24f51-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="24f51-106">Genellikle, bunlar bir veri satırı ayrıntılarını erişim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24f51-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="24f51-107">Aşağıdaki kod örneğinde, bağlantısız sütun oluşturmak gösterilmiştir **ayrıntıları** alt tablosunu görüntülemek için düğmeler ilgili üst tablosundaki belirli bir satır için bir ana öğe/ayrıntı senaryo uyguladığınızda.</span><span class="sxs-lookup"><span data-stu-id="24f51-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="24f51-108">Düğme tıklamalarına yanıt vermesi uygulayan bir <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> alt tablo içeren bir form görüntüler olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="24f51-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="24f51-109">Visual Studio'da bu görev için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="24f51-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="24f51-110">Ayrıca bkz. [nasıl yapılır: ekleme ve kaldırma sütunları Windows Forms DataGridView denetimi kullanarak Tasarımcısı](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="24f51-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f51-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="24f51-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24f51-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="24f51-112">Compiling the Code</span></span>  
 <span data-ttu-id="24f51-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="24f51-113">This example requires:</span></span>  
  
-   <span data-ttu-id="24f51-114">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="24f51-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="24f51-115">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="24f51-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f51-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24f51-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="24f51-117">Windows Forms DataGridView denetiminde verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="24f51-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="24f51-118">Windows Forms DataGridView denetiminde veri görüntüleme modları</span><span class="sxs-lookup"><span data-stu-id="24f51-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
