---
title: 'Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma'
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
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 245d35989a4e9c5b580ae26458e246c9eb8ec2fe
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="c9ab9-102">Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma</span><span class="sxs-lookup"><span data-stu-id="c9ab9-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="c9ab9-103"><xref:System.Windows.Forms.ToolStripControlHost> rastgele Windows Forms denetimlerini kullanarak barındırma sağlamak üzere tasarlanmış <xref:System.Windows.Forms.ToolStripControlHost> Oluşturucusu veya genişletme <xref:System.Windows.Forms.ToolStripControlHost> kendisi.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="c9ab9-104">Denetimi genişleterek sarmalamak daha kolay <xref:System.Windows.Forms.ToolStripControlHost> ve özellikleri ve sık kullanıma yöntemleri uygulama özellikleri ve yöntemleri denetiminin kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="c9ab9-105">Denetim olaylarını da getirebilir <xref:System.Windows.Forms.ToolStripControlHost> düzeyi.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="c9ab9-106">Bir denetimde bir ToolStripControlHost göre türetme barındırmak için</span><span class="sxs-lookup"><span data-stu-id="c9ab9-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1.  <span data-ttu-id="c9ab9-107">Genişletme <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="c9ab9-108">İstenen denetiminde temel sınıf oluşturucu geçirme çağıran varsayılan bir oluşturucu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-108">Implement a default constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2.  <span data-ttu-id="c9ab9-109">Sarmalanan denetimi aynı türden bir özelliği bildirme ve geri dönüp `Control` özelliğin erişimci denetiminde doğru türü.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3.  <span data-ttu-id="c9ab9-110">Sunmaya diğer sık özellikleri ve yöntemleri Sarmalanan denetimi özellikleri ve yöntemleri genişletilmiş sınıfında ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4.  <span data-ttu-id="c9ab9-111">İsteğe bağlı olarak, geçersiz kılma <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, ve <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> yöntemleri ve istediğiniz kullanıma sunmak için denetim olayları ekler.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5.  <span data-ttu-id="c9ab9-112">Kullanıma sunmak istediğiniz olayları için gerekli kaydırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="c9ab9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9ab9-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c9ab9-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c9ab9-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c9ab9-115">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c9ab9-115">This example requires:</span></span>  
  
-   <span data-ttu-id="c9ab9-116">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c9ab9-117">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab9-117">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c9ab9-118">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-118">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c9ab9-119">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c9ab9-119">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ab9-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9ab9-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripControlHost>  
 [<span data-ttu-id="c9ab9-121">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c9ab9-121">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="c9ab9-122">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="c9ab9-122">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="c9ab9-123">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="c9ab9-123">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
