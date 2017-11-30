---
title: "Nasıl yapılır: Kılavuz Öğesi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="47a28-102">Nasıl yapılır: Kılavuz Öğesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="47a28-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="47a28-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="47a28-103">Example</span></span>  
 <span data-ttu-id="47a28-104">Aşağıdaki örnek oluşturma ve kullanma örneği gösterilmiştir <xref:System.Windows.Controls.Grid> kullanarak ya da [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod.</span><span class="sxs-lookup"><span data-stu-id="47a28-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="47a28-105">Bu örnek üç kullanır <xref:System.Windows.Controls.ColumnDefinition> nesneleri ve üç <xref:System.Windows.Controls.RowDefinition> dokuz sahip bir kılavuz oluşturmak için hücreleri çalışma olduğu gibi nesneleri.</span><span class="sxs-lookup"><span data-stu-id="47a28-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="47a28-106">Her hücre içeren bir <xref:System.Windows.Controls.TextBlock> veri ve en üst sıra temsil eden öğesi içeren bir <xref:System.Windows.Controls.TextBlock> ile <xref:System.Windows.Controls.Grid.ColumnSpan%2A> uygulanan özelliği.</span><span class="sxs-lookup"><span data-stu-id="47a28-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="47a28-107">Her hücrenin sınırlarını göstermek için <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliği etkin hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="47a28-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="47a28-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47a28-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="47a28-109">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="47a28-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
