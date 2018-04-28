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
ms.openlocfilehash: 9e672215ac7b381175303c62f24c3881a2cce693
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="0b976-102">Nasıl Yapılır: İşlemi Arka Planda Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0b976-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="0b976-103">Tamamlanması uzun zaman alacağı işleme sahip ve kullanıcı arabiriminde gecikmelere neden istemediğiniz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0b976-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="0b976-104">Aşağıdaki kod örneğinde, uzun süren işlem arka planda çalışan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b976-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="0b976-105">Formun **Başlat** ve **iptal** düğmeler.</span><span class="sxs-lookup"><span data-stu-id="0b976-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="0b976-106">Tıklatın **Başlat** zaman uyumsuz bir işlem çalıştırmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0b976-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="0b976-107">Tıklatın **iptal** çalışan zaman uyumsuz işlemi durdurmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0b976-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="0b976-108">Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="0b976-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="0b976-109">Visual Studio'da bu görev için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="0b976-109">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="0b976-110">Ayrıca bkz. [izlenecek yol: bir işlemi arka planda çalışan](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0b976-110">Also see [Walkthrough: Running an Operation in the Background](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b976-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b976-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b976-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0b976-112">Compiling the Code</span></span>  
 <span data-ttu-id="0b976-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0b976-113">This example requires:</span></span>  
  
-   <span data-ttu-id="0b976-114">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="0b976-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0b976-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0b976-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0b976-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b976-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0b976-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0b976-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b976-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b976-118">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="0b976-119">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="0b976-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="0b976-120">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="0b976-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
