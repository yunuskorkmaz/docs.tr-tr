---
title: 'Nasıl yapılır: Tıklamalar ve Çift Tıklamaları Birbirinden Ayırma'
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
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f6f92c225e7b3c745c5cf439c9094d72fa0cde0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a><span data-ttu-id="3db9d-102">Nasıl yapılır: Tıklamalar ve Çift Tıklamaları Birbirinden Ayırma</span><span class="sxs-lookup"><span data-stu-id="3db9d-102">How to: Distinguish Between Clicks and Double-Clicks</span></span>
<span data-ttu-id="3db9d-103">Genellikle, bir tek *tıklatın* bir kullanıcı arabirimi (UI) eylemi başlatır ve *çift tıklatın* eylemi genişletir.</span><span class="sxs-lookup"><span data-stu-id="3db9d-103">Typically, a single *click* initiates a user interface (UI) action and a *double-click* extends the action.</span></span> <span data-ttu-id="3db9d-104">Örneğin, tek bir tıklatmayla genellikle bir öğe seçer ve seçilen öğeyi çift tıklatma düzenler.</span><span class="sxs-lookup"><span data-stu-id="3db9d-104">For example, one click usually selects an item, and a double-click edits the selected item.</span></span> <span data-ttu-id="3db9d-105">Ancak, Windows Forms tıklama olayları bir eylem bağlı olduğundan kolayca burada bir tıklatma ve çift tıklatma gerçekleştirmek uyumsuz Eylemler, bir senaryoda çalışmak değil <xref:System.Windows.Forms.Control.Click> veya <xref:System.Windows.Forms.Control.MouseClick> olay, eyleminden önce bağlıgerçekleştirilir<xref:System.Windows.Forms.Control.DoubleClick>veya <xref:System.Windows.Forms.Control.MouseDoubleClick> olay.</span><span class="sxs-lookup"><span data-stu-id="3db9d-105">However, the Windows Forms click events do not easily accommodate a scenario where a click and a double-click perform incompatible actions, because an action tied to the <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> event is performed before the action tied to the <xref:System.Windows.Forms.Control.DoubleClick> or <xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span> <span data-ttu-id="3db9d-106">Bu konuda bu sorunun iki çözümü gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3db9d-106">This topic demonstrates two solutions to this problem.</span></span> <span data-ttu-id="3db9d-107">Bir çözüm, çift tıklatma olayını işlemek ve eylemleri click olayını işlemede geri almaktır.</span><span class="sxs-lookup"><span data-stu-id="3db9d-107">One solution is to handle the double-click event and roll back the actions in the handling of the click event.</span></span> <span data-ttu-id="3db9d-108">Nadir durumlarda, davranış işleyerek çift tıklayın ve tıklatın benzetimini gerekebilir <xref:System.Windows.Forms.Control.MouseDown> olay ve kullanarak <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> ve <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> özelliklerini <xref:System.Windows.Forms.SystemInformation> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3db9d-108">In rare situations you may need to simulate click and double-click behavior by handling the <xref:System.Windows.Forms.Control.MouseDown> event and by using the <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> and <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> properties of the <xref:System.Windows.Forms.SystemInformation> class.</span></span> <span data-ttu-id="3db9d-109">Tıklama ve ikinci bir tıklatma değeri önce oluşursa arasındaki süreyi ölçmek <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> ulaşıldığında ve tıklatın tarafından tanımlanan bir dikdörtgen içinde <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, çift tıklatma eylemi gerçekleştirir; Aksi halde, tıklatma eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="3db9d-109">You measure the time between clicks and if a second click occurs before the value of <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> is reached and the click is within a rectangle defined by <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, perform the double-click action; otherwise, perform the click action.</span></span>  
  
### <a name="to-roll-back-a-click-action"></a><span data-ttu-id="3db9d-110">Bir tıklatma eylemi geri almak için</span><span class="sxs-lookup"><span data-stu-id="3db9d-110">To roll back a click action</span></span>  
  
-   <span data-ttu-id="3db9d-111">Çalıştığınız denetim standart sahip olduğundan emin olun davranışı çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3db9d-111">Ensure that the control you are working with has standard double-click behavior.</span></span> <span data-ttu-id="3db9d-112">Değilse, denetimle etkinleştirmek <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3db9d-112">If not, enable the control with the <xref:System.Windows.Forms.Control.SetStyle%2A> method.</span></span> <span data-ttu-id="3db9d-113">Çift tıklatma olayını işlemek ve çift tıklatma eylemi yanı sıra tıklatma eylemi geri alma.</span><span class="sxs-lookup"><span data-stu-id="3db9d-113">Handle the double-click event and roll back the click action as well as the double-click action.</span></span> <span data-ttu-id="3db9d-114">Aşağıdaki kod örneği gösterilmiştir çift tıklatma eylemi çift olay kod işleme geri almak nasıl yanı sıra etkin ile özel bir düğme oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3db9d-114">The following code example demonstrates a how to create a custom button with double-click enabled, as well as how to roll back the click action in the double-click event handling code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a><span data-ttu-id="3db9d-115">MouseDown olayı tıklama ayırt etmek için</span><span class="sxs-lookup"><span data-stu-id="3db9d-115">To distinguish between clicks in the MouseDown event</span></span>  
  
-   <span data-ttu-id="3db9d-116">İşleme <xref:System.Windows.Forms.Control.MouseDown> olay ve saat ve konum span uygun kullanarak tıklamaları belirlemek <xref:System.Windows.Forms.SystemInformation> özellikleri ve bir <xref:System.Windows.Forms.Timer> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="3db9d-116">Handle the <xref:System.Windows.Forms.Control.MouseDown> event and determine the location and time span between clicks using the appropriate <xref:System.Windows.Forms.SystemInformation> properties and a <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="3db9d-117">Olup tıklatın ya da çift gerçekleşir bağlı olarak uygun eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="3db9d-117">Perform the appropriate action depending on whether a click or double-click takes place.</span></span> <span data-ttu-id="3db9d-118">Aşağıdaki kod örneği, bu nasıl yapılabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="3db9d-118">The following code example demonstrates how this can be done.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3db9d-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3db9d-119">Compiling the Code</span></span>  
 <span data-ttu-id="3db9d-120">Bu örnekler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3db9d-120">These examples require:</span></span>  
  
-   <span data-ttu-id="3db9d-121">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="3db9d-121">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3db9d-122">Visual Basic veya Visual C# için bu örnekler komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3db9d-122">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3db9d-123">Yeni projelere kodu yapıştırılarak Visual Studio'da bu örnekler de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3db9d-123">You can also build these examples in Visual Studio by pasting the code into new projects.</span></span>  <span data-ttu-id="3db9d-124">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3db9d-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db9d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3db9d-125">See Also</span></span>  
 [<span data-ttu-id="3db9d-126">Bir Windows Forms Uygulamasında Fare Girdisi</span><span class="sxs-lookup"><span data-stu-id="3db9d-126">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
