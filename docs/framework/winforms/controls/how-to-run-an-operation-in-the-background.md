---
title: 'Nasıl Yapılır: İşlemi Arka Planda Çalıştırma'
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
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d17b2b982def283021bbd5d0ba7ab1e40ecf4e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="f584c-102">Nasıl Yapılır: İşlemi Arka Planda Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f584c-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="f584c-103">Tamamlanması uzun zaman alacağı işleme sahip ve kullanıcı arabiriminde gecikmelere neden istemediğiniz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f584c-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="f584c-104">Aşağıdaki kod örneğinde, uzun süren işlem arka planda çalışan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f584c-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="f584c-105">Formun **Başlat** ve **iptal** düğmeler.</span><span class="sxs-lookup"><span data-stu-id="f584c-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="f584c-106">Tıklatın **Başlat** zaman uyumsuz bir işlem çalıştırmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f584c-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="f584c-107">Tıklatın **iptal** çalışan zaman uyumsuz işlemi durdurmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f584c-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="f584c-108">Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="f584c-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="f584c-109">Bu görev için kapsamlı destek [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f584c-109">There is extensive support for this task in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="f584c-110">Ayrıca bkz. [izlenecek yol: bir işlemi arka planda çalışan](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f584c-110">Also see [Walkthrough: Running an Operation in the Background](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f584c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f584c-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f584c-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f584c-112">Compiling the Code</span></span>  
 <span data-ttu-id="f584c-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f584c-113">This example requires:</span></span>  
  
-   <span data-ttu-id="f584c-114">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="f584c-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f584c-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f584c-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f584c-116">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="f584c-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f584c-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f584c-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f584c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f584c-118">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="f584c-119">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="f584c-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="f584c-120">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="f584c-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
