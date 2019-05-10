---
title: 'Nasıl yapılır: Arka Planda İşlem Çalıştırma'
ms.date: 03/30/2017
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
ms.openlocfilehash: a27c6d83a6a132ed5a83031d469e2f527b730d49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638359"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="bbd53-102">Nasıl yapılır: Arka Planda İşlem Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bbd53-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="bbd53-103">Sahip olduğunuz işleminin tamamlanması uzun sürer ve kullanıcı arabiriminizde gecikmelere neden istiyor musunuz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> sınıfı, başka bir iş parçacığı üzerinde işlemi çalıştıramadı.</span><span class="sxs-lookup"><span data-stu-id="bbd53-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="bbd53-104">Aşağıdaki kod örneği, zaman alıcı bir işlem arka planda çalıştırılacak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbd53-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="bbd53-105">Formundadır **Başlat** ve **iptal** düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="bbd53-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="bbd53-106">Tıklayın **Başlat** zaman uyumsuz bir işlemi çalıştırmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="bbd53-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="bbd53-107">Tıklayın **iptal** bir çalıştırma zaman uyumsuz işlemi durdurmak için düğmeye.</span><span class="sxs-lookup"><span data-stu-id="bbd53-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="bbd53-108">Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="bbd53-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="bbd53-109">Visual Studio'da bu görevi için kapsamlı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="bbd53-109">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="bbd53-110">Ayrıca bkz: [izlenecek yol: Arka planda işlem çalıştırma](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="bbd53-110">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbd53-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbd53-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbd53-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bbd53-112">Compiling the Code</span></span>  
 <span data-ttu-id="bbd53-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bbd53-113">This example requires:</span></span>  
  
- <span data-ttu-id="bbd53-114">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="bbd53-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bbd53-115">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bbd53-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bbd53-116">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbd53-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd53-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd53-117">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="bbd53-118">Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama</span><span class="sxs-lookup"><span data-stu-id="bbd53-118">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="bbd53-119">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="bbd53-119">BackgroundWorker Component</span></span>](backgroundworker-component.md)
