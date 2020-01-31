---
title: DataGridView Satırlarına Bağlı Nesnelere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743169"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="1e6b1-102">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="1e6b1-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="1e6b1-103">Bazen iş nesneleri koleksiyonunda depolanan bilgilerin bir tablosunu göstermek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="1e6b1-104">Bu tür bir koleksiyona bir <xref:System.Windows.Forms.DataGridView> denetimi bağladığınızda, özellik bir <xref:System.ComponentModel.BrowsableAttribute>ile gözatılabilir olarak işaretlenmedikçe her genel özellik kendi sütununda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="1e6b1-105">Örneğin, `Customer` nesnelerinin bir koleksiyonu **ad** ve **Adres**gibi sütunlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="1e6b1-106">Bu nesneler, erişmek istediğiniz ek bilgileri ve kodu içeriyorsa, satır nesneleri aracılığıyla buna ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="1e6b1-107">Aşağıdaki kod örneğinde, kullanıcılar birden çok satırı seçip ilgili müşterilerin her birine bir fatura göndermek için bir düğmeye tıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="1e6b1-108">Satır bağlantılı nesnelere erişmek için</span><span class="sxs-lookup"><span data-stu-id="1e6b1-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="1e6b1-109"><xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="1e6b1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e6b1-110">Example</span></span>  
 <span data-ttu-id="1e6b1-111">Tüm kod örneği basit bir `Customer` uygulamasını içerir ve <xref:System.Windows.Forms.DataGridView> birkaç `Customer` nesnesini içeren bir <xref:System.Collections.ArrayList> bağlar.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="1e6b1-112"><xref:System.Windows.Forms.Control.Click> olay <xref:System.Windows.Forms.Button?displayProperty=nameWithType> işleyicisi, müşteri koleksiyonu <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi dışında erişilebilir olmadığı için `Customer` nesnelerine satırlar aracılığıyla erişmelidir.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e6b1-113">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="1e6b1-113">Compiling the Code</span></span>  
 <span data-ttu-id="1e6b1-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1e6b1-114">This example requires:</span></span>  
  
- <span data-ttu-id="1e6b1-115">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e6b1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e6b1-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1e6b1-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1e6b1-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="1e6b1-118">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="1e6b1-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
