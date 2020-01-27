---
title: DataGridView Denetimlerine Nesne Bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: d5aa5cb64c7fb2b82d69d6c87134ee901b84f5c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746707"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="d6346-102">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="d6346-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="d6346-103">Aşağıdaki kod örneğinde, her nesnenin ayrı bir satır olarak görünmesi için bir nesne koleksiyonunun <xref:System.Windows.Forms.DataGridView> denetimine nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6346-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="d6346-104">Bu örnek ayrıca, Birleşik giriş kutusu açılan listesinin numaralandırma değerlerini içermesi için bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> numaralandırma türüyle bir özelliğin nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6346-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6346-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6346-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d6346-106">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="d6346-106">Compiling the Code</span></span>  
 <span data-ttu-id="d6346-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d6346-107">This example requires:</span></span>  
  
- <span data-ttu-id="d6346-108">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="d6346-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6346-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6346-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="d6346-110">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d6346-110">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d6346-111">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="d6346-111">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
