---
title: 'Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: a472226103f077975c9c6ddc744d419cfcc390cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532142"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="340e6-102">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="340e6-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="340e6-103">Aşağıdaki örnek program Fibonacci numaraları hesaplayan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="340e6-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="340e6-104">Hesaplama kullanıcı arabirimi hesaplama devam ettikçe gecikmeler çalışmaya devam eder, kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="340e6-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="340e6-105">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="340e6-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="340e6-106">Ayrıca bkz: [izlenecek yol: Arka plan işlemi kullanan bir Form uygulama](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="340e6-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="340e6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="340e6-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="340e6-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="340e6-108">Compiling the Code</span></span>  
 <span data-ttu-id="340e6-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="340e6-109">This example requires:</span></span>  
  
-   <span data-ttu-id="340e6-110">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="340e6-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="340e6-111">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="340e6-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="340e6-112">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="340e6-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="340e6-113">Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="340e6-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="340e6-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="340e6-114">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="340e6-115">Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="340e6-115">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="340e6-116">Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../../docs/standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="340e6-116">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="340e6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="340e6-117">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="340e6-118">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="340e6-118">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="340e6-119">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="340e6-119">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)
