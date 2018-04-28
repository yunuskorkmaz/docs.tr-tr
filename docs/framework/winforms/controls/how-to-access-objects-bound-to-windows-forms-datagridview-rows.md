---
title: 'Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd29b04565b29f1cdbc78c070e5cc74baa350f3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="731fd-102">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="731fd-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="731fd-103">Bazen bir iş nesnesi bir koleksiyonda depolanan bilgileri tablosunu görüntülemek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="731fd-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="731fd-104">Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> bu tür bir koleksiyon, her bir genel özelliğinin denetimine özelliği ile gözatılamaz dışı olarak işaretlenmiş sürece kendi sütununda görüntülenen bir <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="731fd-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="731fd-105">Örneğin, bir koleksiyonu `Customer` nesneleri sahip olabilir sütunlar gibi **adı** ve **adresi**.</span><span class="sxs-lookup"><span data-stu-id="731fd-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="731fd-106">Bu nesneler ek bilgi ve erişmek istediğiniz kodu içeriyorsa, satır nesnelerde ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="731fd-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="731fd-107">Aşağıdaki kod örneğinde kullanıcıların birden çok satır seçin ve her karşılık gelen müşteriler için bir fatura göndermek için bir düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="731fd-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="731fd-108">Satır bağlı nesnelere erişmek için</span><span class="sxs-lookup"><span data-stu-id="731fd-108">To access row-bound objects</span></span>  
  
-   <span data-ttu-id="731fd-109">Kullanım <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="731fd-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="731fd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="731fd-110">Example</span></span>  
 <span data-ttu-id="731fd-111">Tam kod örneği basit bir içeren `Customer` uygulama ve bağlamalar <xref:System.Windows.Forms.DataGridView> için bir <xref:System.Collections.ArrayList> birkaç içeren `Customer` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="731fd-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="731fd-112"><xref:System.Windows.Forms.Control.Click> Olay işleyicisi <xref:System.Windows.Forms.Button?displayProperty=nameWithType> erişmesi gereken `Customer` müşteri koleksiyonu dışında erişilebilir olmadığı için satır nesneleri <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="731fd-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="731fd-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="731fd-113">Compiling the Code</span></span>  
 <span data-ttu-id="731fd-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="731fd-114">This example requires:</span></span>  
  
-   <span data-ttu-id="731fd-115">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="731fd-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="731fd-116">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="731fd-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="731fd-117">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="731fd-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="731fd-118">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="731fd-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="731fd-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="731fd-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="731fd-120">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="731fd-120">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="731fd-121">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="731fd-121">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)
