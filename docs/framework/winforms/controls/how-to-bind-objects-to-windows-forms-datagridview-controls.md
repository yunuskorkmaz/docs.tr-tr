---
title: DataGridView Denetimlerine Nesne Bağlama
description: Her nesnenin ayrı bir satır olarak görüntülenmesini sağlamak için bir nesne koleksiyonunu Windows Forms DataGridView denetimine bağlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: add0047937b404dcec1ea12bac8053bb9bdfcf1c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325860"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="e18ef-103">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="e18ef-103">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="e18ef-104">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.DataGridView> her nesnenin ayrı bir satır olarak görünmesi için bir nesne koleksiyonunun bir denetime nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e18ef-104">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="e18ef-105">Bu örnek ayrıca, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> Birleşik giriş kutusu açılan listesinin numaralandırma değerlerini içermesi için bir içinde numaralandırma türü olan bir özelliğin nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e18ef-105">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e18ef-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e18ef-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e18ef-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e18ef-107">Compiling the Code</span></span>  
 <span data-ttu-id="e18ef-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e18ef-108">This example requires:</span></span>  
  
- <span data-ttu-id="e18ef-109">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e18ef-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18ef-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e18ef-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="e18ef-111">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e18ef-111">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e18ef-112">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="e18ef-112">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
