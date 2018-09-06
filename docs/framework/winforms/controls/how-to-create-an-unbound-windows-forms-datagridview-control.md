---
title: 'Nasıl yapılır: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 0441f0ce1005c82ae7ea9a0daecb3ec7ff41f59b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745719"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="0f32f-102">Nasıl yapılır: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f32f-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0f32f-103">Aşağıdaki kod örneğinde nasıl doldurulacağını gösterir bir <xref:System.Windows.Forms.DataGridView> program aracılığıyla bir veri kaynağına bağlama olmadan denetimi.</span><span class="sxs-lookup"><span data-stu-id="0f32f-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="0f32f-104">Az miktarda bir tablo biçiminde görüntülemek istediğiniz veri olduğunda bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f32f-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="0f32f-105">Bu kod örneği tam bir açıklaması için bkz. [izlenecek yol: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0f32f-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f32f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f32f-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f32f-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0f32f-107">Compiling the Code</span></span>  
 <span data-ttu-id="0f32f-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0f32f-108">This example requires:</span></span>  
  
-   <span data-ttu-id="0f32f-109">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="0f32f-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0f32f-110">Visual Basic veya Visual C# için komut satırından Bu örnek oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0f32f-110">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0f32f-111">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f32f-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0f32f-112">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0f32f-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f32f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f32f-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="0f32f-114">İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f32f-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0f32f-115">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0f32f-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0f32f-116">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="0f32f-116">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
