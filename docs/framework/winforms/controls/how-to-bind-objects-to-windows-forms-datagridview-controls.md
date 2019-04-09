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
ms.openlocfilehash: 02c4f94eddfcf782d7d2323787d9b6a9b18db2d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180264"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="5ae7c-102">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="5ae7c-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="5ae7c-103">Aşağıdaki kod örneği, bir nesne koleksiyonu bağlamak gösterilmiştir bir <xref:System.Windows.Forms.DataGridView> böylece her nesneyi ayrı bir satır olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ae7c-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="5ae7c-104">Bu örnek ayrıca bir numaralandırma türü ile bir özelliği görüntülemek nasıl gösterir bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> böylece birleşik giriş kutusu açılır listede numaralandırma değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5ae7c-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae7c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ae7c-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ae7c-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5ae7c-106">Compiling the Code</span></span>  
 <span data-ttu-id="5ae7c-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5ae7c-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5ae7c-108">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="5ae7c-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5ae7c-109">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5ae7c-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5ae7c-110">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ae7c-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae7c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ae7c-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="5ae7c-112">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5ae7c-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="5ae7c-113">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="5ae7c-113">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
