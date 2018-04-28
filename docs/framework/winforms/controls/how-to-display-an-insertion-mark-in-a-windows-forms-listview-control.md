---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme'
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
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f50aa16424a50d51fa88bb89d393c9da0f5def7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="8c7dd-102">Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8c7dd-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="8c7dd-103">Ekleme işareti <xref:System.Windows.Forms.ListView> Denetim burada sürüklenen öğeleri eklenecek noktası kullanıcıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="8c7dd-104">Bir kullanıcı iki diğer öğeleri arasında bir noktasına bir öğe sürüklendiğinde ekleme işareti öğenin beklenen yeni konumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c7dd-105">Yalnızca ekleme işareti özellik kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8c7dd-106">Önceki işletim sistemlerinde ekleme işareti ilgili herhangi bir kod hiçbir etkisi olmaz ve ekleme işareti görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="8c7dd-107">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListViewInsertionMark>.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="8c7dd-108">Aşağıdaki resim ekleme işareti gösterir:</span><span class="sxs-lookup"><span data-stu-id="8c7dd-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="8c7dd-109">![ListView ekleme işareti](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="8c7dd-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="8c7dd-110">Aşağıdaki kod örneğinde bu özelliğinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c7dd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c7dd-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c7dd-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8c7dd-112">Compiling the Code</span></span>  
 <span data-ttu-id="8c7dd-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8c7dd-113">This example requires:</span></span>  
  
-   <span data-ttu-id="8c7dd-114">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8c7dd-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8c7dd-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8c7dd-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="8c7dd-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8c7dd-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7dd-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c7dd-118">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewInsertionMark>  
 [<span data-ttu-id="8c7dd-119">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="8c7dd-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="8c7dd-120">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8c7dd-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="8c7dd-121">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="8c7dd-121">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="8c7dd-122">İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8c7dd-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
