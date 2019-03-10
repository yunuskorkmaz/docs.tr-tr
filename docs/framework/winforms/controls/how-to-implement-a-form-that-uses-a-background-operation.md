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
ms.openlocfilehash: 9fe514cce4d4aec386f9d61cb84f3a39273c35b0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723341"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="80642-102">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="80642-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="80642-103">Aşağıdaki örnek program Fibonacci numaraları hesaplayan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="80642-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="80642-104">Hesaplama kullanıcı arabirimi hesaplama devam ettikçe gecikmeler çalışmaya devam eder, kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="80642-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="80642-105">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="80642-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="80642-106">Ayrıca bkz: [izlenecek yol: Arka plan işlemi kullanan bir Form uygulama](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="80642-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80642-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="80642-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80642-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="80642-108">Compiling the Code</span></span>  
 <span data-ttu-id="80642-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="80642-109">This example requires:</span></span>  
  
-   <span data-ttu-id="80642-110">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="80642-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="80642-111">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="80642-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="80642-112">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80642-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="80642-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="80642-113">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="80642-114">Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="80642-114">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="80642-115">Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="80642-115">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80642-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80642-116">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="80642-117">Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="80642-117">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="80642-118">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="80642-118">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
