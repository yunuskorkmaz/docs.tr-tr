---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 9580812be4e15a0b925c5737dc6dfe0e0fdaf407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530113"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="83c7e-102">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="83c7e-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="83c7e-103">Aşağıdaki kod örneği, nesne koleksiyonu bağlamak gösterilmiştir bir <xref:System.Windows.Forms.DataGridView> denetim böylece her nesneyi ayrı bir satır olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="83c7e-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="83c7e-104">Bu örnek ayrıca bir numaralandırma türü ile bir özelliği görüntülemek nasıl gösterilmektedir bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> böylece birleşik giriş kutusu açılan listenin numaralandırma değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="83c7e-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83c7e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="83c7e-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83c7e-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="83c7e-106">Compiling the Code</span></span>  
 <span data-ttu-id="83c7e-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="83c7e-107">This example requires:</span></span>  
  
-   <span data-ttu-id="83c7e-108">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="83c7e-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="83c7e-109">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="83c7e-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="83c7e-110">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83c7e-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="83c7e-111">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="83c7e-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c7e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83c7e-112">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="83c7e-113">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="83c7e-113">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="83c7e-114">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="83c7e-114">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
