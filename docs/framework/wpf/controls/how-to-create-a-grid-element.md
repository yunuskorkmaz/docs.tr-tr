---
title: 'Nasıl yapılır: Kılavuz Öğesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: b93bb859c4a0df50da2fa00587a28fda3776fd09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185790"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="ab683-102">Nasıl yapılır: Kılavuz Öğesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab683-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="ab683-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab683-103">Example</span></span>  
 <span data-ttu-id="ab683-104">Aşağıdaki örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.Controls.Grid> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod.</span><span class="sxs-lookup"><span data-stu-id="ab683-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="ab683-105">Bu örnek, üç kullanır <xref:System.Windows.Controls.ColumnDefinition> nesneleri ve üç <xref:System.Windows.Controls.RowDefinition> dokuz sahip bir kılavuz oluşturmak için hücreleri gibi çalışma nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ab683-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="ab683-106">Her hücre içeren bir <xref:System.Windows.Controls.TextBlock> verileri ve üst satırı temsil eden öğe içeren bir <xref:System.Windows.Controls.TextBlock> ile <xref:System.Windows.Controls.Grid.ColumnSpan%2A> özellik uygulandı.</span><span class="sxs-lookup"><span data-stu-id="ab683-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="ab683-107">Her bir hücresinde sınırları gösterilecek <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliği etkin hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="ab683-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  <span data-ttu-id="ab683-108">Her iki yöntemle de aynı, bir aşağıdaki gibi benzer bir kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab683-108">Either approach will generate a user interface that looks much the same, like the one below.</span></span>

  ![üç sütuna bozuk bir kılavuz içeren bir WPF kullanıcı arabirimi ekran gösterilmektedir.](./media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a><span data-ttu-id="ab683-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab683-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="ab683-113">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab683-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
