---
title: 'Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 244047f27b0eb109aba599bd26881046eb538163
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582614"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="24ef3-102">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="24ef3-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="24ef3-103">Bazen iş nesnelerin bir koleksiyonda depolanan bilgilerinin bir tablosunu görüntülemek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="24ef3-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="24ef3-104">Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetimi gibi bir koleksiyona her ortak özelliği, kendi sütunda görüntülenir, özelliği ile gözatılabilir dışı olarak işaretlenmiş sürece bir <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="24ef3-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="24ef3-105">Örneğin, bir koleksiyonunu `Customer` nesneleri haritamın sütunlar gibi **adı** ve **adresi**.</span><span class="sxs-lookup"><span data-stu-id="24ef3-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="24ef3-106">Bu nesne, ek bilgi ve erişmek istediğiniz kodu içeriyorsa, satır nesnelerde ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24ef3-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="24ef3-107">Aşağıdaki kod örneğinde, kullanıcılar birden çok satır seçin ve karşılık gelen müşterilerin her birine bir fatura göndermek için bir düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="24ef3-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="24ef3-108">Satır bağlı nesnelere erişmek için</span><span class="sxs-lookup"><span data-stu-id="24ef3-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="24ef3-109">Kullanım <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="24ef3-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="24ef3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="24ef3-110">Example</span></span>  
 <span data-ttu-id="24ef3-111">Basit bir tam kod örneği içerir `Customer` uygulama ve bağlamalar <xref:System.Windows.Forms.DataGridView> için bir <xref:System.Collections.ArrayList> birkaç içeren `Customer` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="24ef3-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="24ef3-112"><xref:System.Windows.Forms.Control.Click> Olay işleyicisine <xref:System.Windows.Forms.Button?displayProperty=nameWithType> erişmesi gereken `Customer` nesneleri satırları, müşteri koleksiyonunun dışında erişilebilir olmadığından <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="24ef3-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24ef3-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="24ef3-113">Compiling the Code</span></span>  
 <span data-ttu-id="24ef3-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="24ef3-114">This example requires:</span></span>  
  
- <span data-ttu-id="24ef3-115">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="24ef3-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ef3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24ef3-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="24ef3-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="24ef3-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="24ef3-118">Nasıl yapılır: Windows Forms DataGridView denetimlerine nesne bağlama</span><span class="sxs-lookup"><span data-stu-id="24ef3-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
