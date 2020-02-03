---
title: DataGridView Denetimindeki yeni satırlar için varsayılan değerleri belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742938"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9abcb-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="9abcb-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9abcb-103">Uygulama yeni eklenen satırlar için varsayılan değerleri doldurduğunda, veri girişini daha uygun hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9abcb-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="9abcb-104"><xref:System.Windows.Forms.DataGridView> sınıfıyla, varsayılan değerleri <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olayı ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9abcb-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="9abcb-105">Bu olay, Kullanıcı yeni kayıtlar için satırı girdiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="9abcb-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="9abcb-106">Kodunuz bu olayı işlediğinde, istediğiniz hücreleri tercih ettiğiniz değerlerle doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9abcb-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="9abcb-107">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olayını kullanarak yeni satırlar için varsayılan değerlerin nasıl belirtileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9abcb-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9abcb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9abcb-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9abcb-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9abcb-109">Compiling the Code</span></span>  
 <span data-ttu-id="9abcb-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9abcb-110">This example requires:</span></span>  
  
- <span data-ttu-id="9abcb-111">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="9abcb-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="9abcb-112">Benzersiz `CustomerID` değerleri oluşturmak için `NewCustomerId` işlevi.</span><span class="sxs-lookup"><span data-stu-id="9abcb-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="9abcb-113"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="9abcb-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abcb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9abcb-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="9abcb-115">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="9abcb-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9abcb-116">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="9abcb-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
