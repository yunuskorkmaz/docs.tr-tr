---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme'
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
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193700"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3e9eb-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="3e9eb-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3e9eb-103">Uygulamaya yeni eklenen satırlar için değerleri varsayılan doldururken daha kolay veri girişi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="3e9eb-104">İle <xref:System.Windows.Forms.DataGridView> sınıfı doldurabilirsiniz varsayılan değerlerle <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="3e9eb-105">Kullanıcı yeni kayıtlar için satır girdiğinde bu olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="3e9eb-106">Kodunuzu bu olay işlediğinde, seçtiğiniz değerlere sahip istenen hücreleri doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="3e9eb-107">Aşağıdaki kod örneği kullanarak yeni satırlar için varsayılan değerlerin nasıl belirtileceğini gösterir <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e9eb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e9eb-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e9eb-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3e9eb-109">Compiling the Code</span></span>  
 <span data-ttu-id="3e9eb-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3e9eb-110">This example requires:</span></span>  
  
-   <span data-ttu-id="3e9eb-111">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="3e9eb-112">A `NewCustomerId` benzersiz oluşturmak için işlevi `CustomerID` değerleri.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="3e9eb-113">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9eb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e9eb-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="3e9eb-115">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="3e9eb-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3e9eb-116">Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma</span><span class="sxs-lookup"><span data-stu-id="3e9eb-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
