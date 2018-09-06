---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: b9b6e1911d3e372861ebcdc5a175314d69c89175
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855015"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="1505a-102">Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1505a-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="1505a-103">Ekleme işareti <xref:System.Windows.Forms.ListView> denetim noktası sürüklenen öğeler burada eklenecek kullanıcıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="1505a-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="1505a-104">Bir kullanıcı bir öğeyi bir noktaya diğer iki öğe sürüklediğinde ekleme işareti öğenin beklenen yeni konumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1505a-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1505a-105">Yalnızca ekleme işareti özellik kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1505a-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1505a-106">Önceki işletim sistemlerinde ekleme işareti için ilgili herhangi bir kod etkiye sahip değildir ve ekleme işareti görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="1505a-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="1505a-107">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="1505a-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="1505a-108">Aşağıdaki görüntüde ekleme işareti gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1505a-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="1505a-109">![Bir ListView ekleme işareti](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="1505a-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="1505a-110">Aşağıdaki kod örneği, bu özelliğin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1505a-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1505a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="1505a-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1505a-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1505a-112">Compiling the Code</span></span>  
 <span data-ttu-id="1505a-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1505a-113">This example requires:</span></span>  
  
-   <span data-ttu-id="1505a-114">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1505a-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1505a-115">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1505a-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1505a-116">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1505a-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1505a-117">Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1505a-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1505a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1505a-118">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewInsertionMark>  
 [<span data-ttu-id="1505a-119">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="1505a-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="1505a-120">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1505a-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="1505a-121">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="1505a-121">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="1505a-122">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1505a-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
