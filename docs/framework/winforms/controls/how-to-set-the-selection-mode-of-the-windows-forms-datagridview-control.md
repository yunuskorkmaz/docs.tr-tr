---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama"
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
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb0f9d0cff7be2dd1243916e6505aab9cc63dd0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="7abbf-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7abbf-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7abbf-103">Aşağıdaki kod örneğinde nasıl yapılandırılacağını göstermektedir bir <xref:System.Windows.Forms.DataGridView> denetim böylece herhangi bir yeri satır içinde otomatik olarak tıklatmak tüm satırı seçer ve bu nedenle, aynı anda yalnızca bir satır seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="7abbf-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7abbf-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7abbf-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7abbf-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7abbf-105">Compiling the Code</span></span>  
 <span data-ttu-id="7abbf-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7abbf-106">This example requires:</span></span>  
  
-   <span data-ttu-id="7abbf-107">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="7abbf-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="7abbf-108">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="7abbf-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abbf-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7abbf-109">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [<span data-ttu-id="7abbf-110">Seçim ve Pano kullanımı Windows Forms DataGridView denetimi ile</span><span class="sxs-lookup"><span data-stu-id="7abbf-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7abbf-111">Windows Forms DataGridView denetimindeki seçim modları</span><span class="sxs-lookup"><span data-stu-id="7abbf-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
