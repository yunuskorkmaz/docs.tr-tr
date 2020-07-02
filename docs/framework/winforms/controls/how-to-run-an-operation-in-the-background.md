---
title: 'Nasıl Yapılır: İşlemi Arka Planda Çalıştırma'
description: Arka planda zaman alan Windows Forms işlemi çalıştırmak için BackgroundWorker sınıfını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621580"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="5094e-103">Nasıl Yapılır: İşlemi Arka Planda Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5094e-103">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="5094e-104">Tamamlanması uzun süren bir işleme sahipseniz ve Kullanıcı arabiriminizdeki gecikmelere yol açmak istemiyorsanız, <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5094e-104">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="5094e-105">Aşağıdaki kod örneği, arka planda zaman alan bir işlemin nasıl çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5094e-105">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="5094e-106">Form **Start** ve **Cancel** düğmelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5094e-106">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="5094e-107">Zaman uyumsuz bir işlem çalıştırmak için **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5094e-107">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="5094e-108">Çalışan bir zaman uyumsuz işlemi durdurmak için **iptal** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5094e-108">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="5094e-109">Her işlemin sonucu bir içinde görüntülenir <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="5094e-109">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="5094e-110">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="5094e-110">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="5094e-111">Ayrıca bkz. [Izlenecek yol: arka planda Işlem çalıştırma](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="5094e-111">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5094e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5094e-112">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5094e-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5094e-113">Compiling the Code</span></span>  
 <span data-ttu-id="5094e-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5094e-114">This example requires:</span></span>  
  
- <span data-ttu-id="5094e-115">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="5094e-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5094e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5094e-116">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="5094e-117">Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama</span><span class="sxs-lookup"><span data-stu-id="5094e-117">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="5094e-118">BackgroundWorker Bileşeni</span><span class="sxs-lookup"><span data-stu-id="5094e-118">BackgroundWorker Component</span></span>](backgroundworker-component.md)
